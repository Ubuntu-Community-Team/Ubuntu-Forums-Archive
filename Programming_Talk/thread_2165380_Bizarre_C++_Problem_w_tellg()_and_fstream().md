---
title: "Bizarre C++ Problem w/ tellg() and fstream()"
date: 2013-08-04
forum: Programming Talk
---

### Post by grantcurell on 2013-08-04
In the code below, if the call to tellg() inside the print statement is not there, the program will not loop and will immediately terminate after the one pass. If that call to tellg() is included, the program works exactly as expected. The input must be greater than 100 bytes in order to observe the problem. At first I considered that maybe a badbit was being set. I tested that theory by replacing the printf w/tellg() with a call to file.clear(). TO my astonishment, the program failed just as before. When I put the tellg() back in the program worked as expected. For clarification, it may be helpful to know that for fstream the get and put pointers are separate.

```

/* Quick n' Dirty File Encoder
 * Author: Grant Curell
 * Date: 3 August 2013
 * Encodes a file using the xor function. The key is whatever memblocktemp
 * is initialized to. The function uses the output of the first xor as the
 * input for the next xor and so on and so forth.
 */


#include <fstream>
#include <stdio.h>
#include <string.h>


using namespace std;


#define BLOCKSIZE 100


char memblock[BLOCKSIZE], memblocktemp[BLOCKSIZE];


int main () {
    //Open the file in binary mode
    fstream file;
    file.open("test.exe", ios::in|ios::out|ios::binary);


    memset(memblocktemp, 'G', BLOCKSIZE);


    //Make sure the file successfully opened
    if (file.is_open()) {    


        int bytes_read;


        while(file.good()) {
            file.read(memblock, BLOCKSIZE); //Read Block        


            //Count the number of bytes read in to ensure we don't
            //write past the end of the file
            bytes_read = file.gcount();
            
            //xor the bytes read in    
            for(int x=0; x<BLOCKSIZE; x++) {
                memblock[x] ^= memblocktemp[x];
                memblocktemp[x] = memblock[x];
            }


            file.seekp(-bytes_read, ios::cur);
        
            if(file.eof()) {
                file.clear();
                file.seekp(-bytes_read, ios::cur);
                file.write(memblock, bytes_read);
                break;
            }
                
            file.write(memblock, bytes_read); //Write to the block
            printf("File get pointer is at %d\n", (int)file.tellg());
            
        }


        file.close();
        
        printf("Operation complete.\n");

    } else
        printf("Unable to open file\n");

    return 0;
}

```

---

### Post by dwhitney67 on 2013-08-04
I ran your program with and without the printf/tellg, and in both cases the resulting file (test.exe) was the same.

Can you please elaborate as to what is not "working"?

P.S.  I tested with a file that is 455 characters long.

---

### Post by grantcurell on 2013-08-04
What was your result? fstream has a lot of platform dependent behavior. It should encode the entire input file (test.exe). For me, without the tellg() it only goes through the code in the loop once and then terminates even  if it should loop multiple times. If the tellg() is there it loops the appropriate number of times and encodes the entire file.

---

### Post by ofnuts on 2013-08-05
If the loop is only run once then either file.good() becomes false or file.eof() is true. file.good() get false if either eof, fail, or bad is true, so knowing which will help (as will knowing if the break is the one making the loop exit).

Also, my C++is getting quite rusty, but if there are distinct get/put pointers, I don't understand your use of seekp(). If you are writing things sequentially then that pointer will be maintained by the runtime. And if you want to make sure that you are overwriting the bytes you just read, you should set the put pointer from the get pointer minus bytes_read (or memorize the get pointer before you read the bytes...) but fixing up th eput pointer from itself means you are going to overwrite the same BLOCKSIZE bytes repeatedly at the beginning of the file?

---

### Post by dwhitney67 on 2013-08-05
> **grantcurell said:**
> What was your result?

As I indicated earlier, the program functioned as expected, with or without the usage of tellg().

> **grantcurell said:**
> 
fstream has a lot of platform dependent behavior.

Perhaps, but none that I can recollect between Linux, Windows, Solaris, HP-UX, or the Mac.  Each OS may have their particular quirks (I know Windoze does), but this is beyond the scope of fstream.

> **grantcurell said:**
> 
It should encode the entire input file (test.exe).

Actually it is not fstream that should encode the file, but your application.

> **grantcurell said:**
> 
For me, without the tellg() it only goes through the code in the loop once and then terminates even  if it should loop multiple times. If the tellg() is there it loops the appropriate number of times and encodes the entire file.
What evidence do you have that without the tellg(), the loop is only executed once?  Perhaps since you have commented out the printf() statement, you don't have any way to see that the loop is indeed executed multiple times for a file that has 100+ bytes.  If your file has 100, or less, bytes, then it is reasonable to expect the loop to occur only once.

While putting together my response, I tweaked your program a little to "tighten" it up a bit; here's the modified code:
```

#include <fstream>
#include <iostream>
#include <cstring>

#define BLOCKSIZE 100

using namespace std;


int main()
{
    char memblocktemp[BLOCKSIZE];

    memset(memblocktemp, 'G', BLOCKSIZE);

    fstream file("test.exe", ios::in|ios::out|ios::binary);

    if (file) {
        while (file.good()) {
            char memblock[BLOCKSIZE] = {0};

            file.read(memblock, BLOCKSIZE);

            size_t bytes_read = file.gcount();

            cout << "Read " << bytes_read << " bytes." << endl;

            if (bytes_read == 0) break;

            //xor the bytes read in    
            for (size_t x = 0; x < bytes_read; ++x) {
                memblock[x] ^= memblocktemp[x];
                memblocktemp[x] = memblock[x];
            }

            file.seekp(-bytes_read, ios::cur);

            if (file.eof()) {
                file.clear();
                file.seekp(-bytes_read, ios::cur);
                file.write(memblock, bytes_read); //Write to the block
                break;
            }

            file.write(memblock, bytes_read); //Write to the block

            cout << "iterating..." << endl;
        }

        cout << "Operation complete." << endl;
    }
    else {
        cerr << "Unable to open file" << endl;
    }
}

```

P.S.  You might find it easier to verify your program is working if you test it using a debugger.  Also, rather than XOR the data, perhaps just leave it unchanged (or convert it to something readable).

---

