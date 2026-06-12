---
title: "reading a jpeg's comment"
date: 2008-08-23
forum: Programming Talk
---

### Post by StOoZ on 2008-08-23
Im trying , as a practice , not looking for a library to do it for me , to read a jpeg's comment , now I know its in bytes 0xFFFE , according to wiki [http://en.wikipedia.org/wiki/JPEG]("http://en.wikipedia.org/wiki/JPEG")

so I tried this :
> #include<iostream>
#include<fstream>
using namespace std;


int main(int argc , char* argv[]) {
   
    fstream image_file("bl83x010.jpg" , ios_base::in | ios_base::binary );
    image_file.seekg(-0xFFFE , ios_base::end);
    
    char data[0xFFFE];
    image_file.read(data ,  0xFFFE );
    cout<<(const char*) data;

    
    image_file.close();
    return 0;
}

but it doesnt work.
the image is in the source dir , it loads fine (checked with is_open , and it has a comment)


and I tried this also , and still doesnt work :
> #include<iostream>
#include<fstream>
using namespace std;


int main(int argc , char* argv[]) {
   
    fstream image_file("bl83x010.jpg" , ios_base::in | ios_base::binary );
    image_file.seekg( 0 , ios_base::end);
    int length = image_file.tellg();
    image_file.seekg(-0xFFFE , ios_base::end);
    
    char data[ length - 0xFFFE ];
    image_file.read(data ,  length - 0xFFFE );
    cout<<length;

    
    image_file.close();
    return 0;
}

---

### Post by odyniec on 2008-08-23
The 0xFFFE is not the position of the comment, but a two-byte marker. You need to look for it inside the JPEG file, and the comment will follow it.

---

### Post by StOoZ on 2008-08-23
hmmm I dont get it , to look for what?

---

### Post by jinksys on 2008-08-23
> **StOoZ said:**
> hmmm I dont get it , to look for what?

The Markers are not positions or offsets, like 0xFFFE bytes from the beginning of the file.  Rather, they are patters that mark the beginning of a field.  Take a look at a small jpeg using a hexeditor, preferably one that has a search feature.

Take a look at this hexdump of Lego_hawking.jpg.  It has the comment, "This is the comment field!"

```

00000000  ff d8 ff e0 00 10 4a 46  49 46 00 01 01 01 00 48  |......JFIF.....H|
00000010  00 48 00 00 ff e1 00 16  45 78 69 66 00 00 4d 4d  |.H......Exif..MM|
00000020  00 2a 00 00 00 08 00 00  00 00 00 00 ff fe 00 1c  |.*..............|
00000030  54 68 69 73 20 69 73 20  74 68 65 20 63 6f 6d 6d  |This is the comm|
00000040  65 6e 74 20 66 69 65 6c  64 21 ff db 00 43 00 05  |ent field!...C..|
00000050  03 04 04 04 03 05 04 04  04 05 05 05 06 07 0c 08  |................|

```

Notice the pattern **fffe** followed by 001C (which is 28, the size of the comment plus the 2 bytes specifying the size).  Then you see the comment.  Then notice the **ffdb** this is a marker specifying the start of another field.

---

### Post by StOoZ on 2008-08-24
thanks for that.
any suggestion for a particular hex editor ?

---

### Post by jinksys on 2008-08-24
> **StOoZ said:**
> thanks for that.
any suggestion for a particular hex editor ?

I usually just use the command-line program **hexdump**, so I'm not really familiar with any GUI editors.  I know that gnome has ghex and khexedit.

---

### Post by asiffayyaz on 2012-03-30
for anyone who wants to read comments. Here is the code:

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

//Gets the JPEG size from the array of data passed to the function, file reference: http://www.obrador.com/essentialjpeg/headerinfo.htm
static char get_jpeg_size(unsigned char* data, unsigned int data_size) {
   //Check for valid JPEG image
   int i=0;   // Keeps track of the position within the file
   unsigned char comment[1024];
   if(data[i] == 0xFF && data[i+1] == 0xD8 && data[i+2] == 0xFF && data[i+3] == 0xE0) {
      i += 4;

      // Check for valid JPEG header (null terminated JFIF)
      if(data[i+2] == 'J' && data[i+3] == 'F' && data[i+4] == 'I' && data[i+5] == 'F' && data[i+6] == 0x00) {
         //Retrieve the block length of the first block since the first block will not contain the size of file
         unsigned short block_length = data[i] * 256 + data[i+1];
         while(i<data_size) {
            i+=block_length;               //Increase the file index to get to the next block
            printf("%x,%x\n", data[i], data[i+1]);
            if(i >= data_size) return false;   //Check to protect against segmentation faults
            if(data[i] != 0xFF){ printf("Byte is not 0xFF, Exiting\n"); return false;}   //Check that we are truly at the start of another block
            if(data[i+1] == 0xFE) {            //0xFFFE is the "Start of Comment" marker which contains comment
               //The structure of the 0xFFFE block is quite simple [0xFFFE][Comment]
               unsigned short comment_len = data[i+2]*256 + data[i+3] - 2;
               strncpy((char*)comment, (char*)(data+(i+4)), comment_len);
               printf("Comment is: %s\n", comment);
            }

            i+=2;                              //Skip the block marker
            block_length = data[i] * 256 + data[i+1];   //Go to the next block
         }
         return false;                     //If this point is reached then no size was found
      }else{ return false; }                  //Not a valid JFIF string

   }else{ return false; }                     //Not a valid SOI header
}


int main(int argc, char* argv[])
{
    FILE* pFile;
    long size;
    unsigned char* buffer;
    unsigned short width, height;
    size_t result;

    pFile = fopen(argv[1], "rb");
    if (pFile == NULL) {perror ("Error opening file"); exit(1);}

    fseek(pFile, 0, SEEK_END);
    size = ftell(pFile);
    rewind(pFile);


    buffer = (unsigned char*)malloc(sizeof(char)*size);
    if (buffer == NULL) {fputs ("Memory Error",stderr); exit(2);}

    result = fread(buffer, 1, size, pFile);
    if (result != size) {printf("size=%d, result=%d\n", size, result);perror("Reading File"); exit(3);}

    get_jpeg_size(buffer, size);
    fclose(pFile);
    free (buffer);
    return 0;
}

```

---

