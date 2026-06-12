---
title: "C programming files"
date: 2013-01-02
forum: Programming Talk
---

### Post by binaryperson on 2013-01-02
Hello. I want my program to print "partSize" amount of bytes of the original file to the new file.
If the original file contains:

0123456789
0123456789
0123456789
0123456789
0123456789
0123456789

and part size is 2 then

0123456789
0123456789
0123456789

is stored to the new file.
So the program is not writing until end of line, that would be the whole file. It is writing partSize amount of bytes.

```

#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <unistd.h>
#include <sys/stat.h> 
#include <sys/types.h> 
#include <errno.h>

int main(int argc, char *argv[])
{
    int createDescriptor;
    int openDescriptorOriginal;
    int closeCreateDescriptor;
int openDescriptorNew;

    //char fileNameOriginal[] = "picture.jpg";
    char fileNameOriginal[] = "original.txt";
    char fileNameNew[] = "new.txt";
    
    int parts;
    int partSize;

    parts=2;

    int bytesRemaining;
    int partNumber;
    char BUFFER[512];
    int readDescriptor;

    int openDescriptorNew;
    
    if ((openDescriptorOriginal = open(fileNameOriginal, O_RDONLY )) == -1)
    {
        printf("Error opening %s", fileNameOriginal);
        exit(EXIT_FAILURE);
    }

    struct stat buf;
    int r = fstat(openDescriptorOriginal, &buf);
    if (r)
    {
        fprintf(stderr, "error: fstat: %s\n", (char *) strerror(errno));
        exit(1);
    }

    int originalFileSize = buf.st_size;
    printf("The file is %.9f Kilobytes large.\n", (double) originalFileSize/1024);

    partSize = ((originalFileSize + parts) + 1)/parts;

    if ((openDescriptorNew = open(fileNameNew, O_CREAT | O_WRONLY )) == -1)
    {
        printf("Error opening %s", openDescriptorNew);
        exit(EXIT_FAILURE);
    }
    
    //I am stuck at this part
    //I want to write the first "partSize" bytes of "fileNameOriginal" to "fileNameNew"
    /*
    while ((readDescriptor = read(openDescriptorOriginal, BUFFER, partSize)) < partSize))
    {
        write(1, BUFFER, readDescriptor);
    }
*/
    if ((closeCreateDescriptor = close(openDescriptorOriginal)) == -1)
    {
        printf("Error closing file.\n");
    }

    return 0;
}

```

---

### Post by cross37 on 2013-01-03
Ok, I'm not sure exactly what you're trying to do here.  Copy a file one part at a time, or split a file into parts.  There were a number of things wrong with your version either way.  

Here's a version which will copy a file one part at a time.  The new file should be identical to the original.

I haven't test this extensively, but it seems to work.

```

#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <unistd.h>
#include <sys/stat.h> 
#include <sys/types.h> 
#include <errno.h>

int main(int argc, char *argv[])
{

    int original_descriptor;
    int new_descriptor;
    int original_file_size;
    int result;

    char original_file_name[] = "original.txt";
    char new_file_name[] = "new.txt";

    int parts = 3;
    int part_size;
    int part_number = 0;
    int bytes_read = 0;

    // Open the file.  If the result is -1 there was an error. Any
    // positive result will be the descriptor for the input file.

    result = open(original_file_name, O_RDONLY );
    if ( result == -1 ) 
    {
        printf("Error opening %s.", original_file_name);
        exit(EXIT_FAILURE);
    }
    original_descriptor = result;


    // Get the file size.

    struct stat buf;
    result = fstat(original_descriptor, &buf);
    if (result)
    {     
        fprintf(stderr, "error: fstat: %s\n", "error");
        exit(1);
    }
    original_file_size = buf.st_size;

    // Get the part size

    printf("The file is %0.2f Kilobytes large.\n", (double) (original_file_size/1024));
    part_size = (original_file_size + 1)/parts;
    if (part_size < 1)
    {
      part_size = 1;
    }

    // Create a buffer large enough to handle partsize bytes.

    char *buffer = malloc(part_size);

    
    // Open ouput file

    result = open(new_file_name, O_CREAT | O_TRUNC | O_WRONLY );
    if ( result == -1 )
    {
      printf("Error opening %s\n", new_file_name);
      exit(EXIT_FAILURE);

    }
    new_descriptor = result;

    do 
    {
        // Read data into buffer
        result = read(original_descriptor, buffer, part_size);
        if (result == -1) 
        {
           printf("Error reading from %s.\n", original_file_name);
           exit(EXIT_FAILURE);
        }
        bytes_read = result;
        printf("Writing part %d (%d bytes).\n", part_number, bytes_read);

        ++part_number;

        result = write(new_descriptor, buffer, bytes_read);
        if (result == -1) 
        {
           printf("Error writing %d bytes to %s.\n", bytes_read, new_file_name);
           exit(EXIT_FAILURE);
        }

    } while (result == part_size);


  // I'm lazy
  // At this point, close files and free buffer.

  return 0;  
      
}


```

---

### Post by binaryperson on 2013-01-03
Sorry, for not explaining enough. Eventually I want to split a file into multiple parts. This was just meant as an attempt to see if I could get the first part of a file read and copied to a new file which would correspond to part1 of a series of files.

---

### Post by cross37 on 2013-01-03
The example I made can be changed to do that.  Each time through the loop you would have to generate a new file name, open the new file, write the data, and close the file.

Hope my example helps.

---

### Post by binaryperson on 2013-01-03
How can I give each file a different second extension? So each time I run the loop I want each new file to be called, if it the original file is mypic.jpg and there are 3 parts, mypic.jpg.part0, mypic.jpg.part1, and mypic.jpg.part2.

---

### Post by spjackson on 2013-01-03
I'm still rather confused by what you are trying to do. In your original post, you say that partSize is the number of bytes to write in each part. Then you give an example of partSize=2, but the part that is written is not 2 bytes. It seems more like in that example you are wanting to write 2 parts, rather than N parts each of size 2.

In any event, do you really want to write a C program for this? The split command (with possibly a small bash wrappper) would seem ideal for whatever it is you are wanting to do.

---

### Post by binaryperson on 2013-01-03
All I want to do is take a file and split into a bunch of parts, which is each a seperate file. So If I have 400KB file and I say the number of parts is 2 then each will have a size if 200KB. Yes, I am sure I want to use C.

---

### Post by r-senior on 2013-01-03
I think I'd lead toward scripting for this too, but if you want to pursue it in C, you need something like snprintf to generate the part names, e.g.:

```
#include <stdio.h>
#include <stdlib.h>

static const unsigned MAXSIZE = 32;

int main(int argc, char **argv)
{
    char filename[] = "myfilename.jpg";
    unsigned parts = 5;

    char partname[MAXSIZE];         
    int bytes_written;
    unsigned p;
    
    for (p = 0; p < parts; p++) {
        bytes_written = snprintf(partname, MAXSIZE, "%s.part%d", filename, p);
        if (bytes_written >= MAXSIZE) {
            fprintf(stderr, "ERROR: Max length of part name is %d\n", MAXSIZE);
            exit(EXIT_FAILURE);
        }
        puts(partname); // The rest of your code in here
    }
    exit(EXIT_SUCCESS);
}

```

I think you've reached the stage where you need to split your program into functions, especially if you wrap it in something like the above.

---

### Post by dwhitney67 on 2013-01-03
> **binaryperson said:**
> Yes, I am sure I want to use C.

Ah... so this is school work.  The utility 'split' (previously mentioned) is written in C.  Why don't you download the source code and slap your name on it?  Just kidding.

---

### Post by binaryperson on 2013-01-03
Thanks, the file naming method you showed me works. I'll divide up the program into functions once I get it working properly. Can someone please test the code? It seems to work, I divided a picture into 2 equal files. But, for some reason it say writing part 2(0 bytes) and writing part 3 (0 bytes). If I ask for 2 parts it should just be part 0 and part 1, why are there 4 parts? Also if I try to free the buffer I a segmentation fault. 
EDIT: if I use free() the program  produces 2 equal sized files but I also get a segmentation fault. If I comment it out the files produced are 0 bytes each but there is no segmentation fault.
EDIT: it should be free(buffer), but still same problem.

```

#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <unistd.h>
#include <sys/stat.h> 
#include <sys/types.h> 
#include <errno.h>

int main(int argc, char *argv[])
{

    int original_descriptor;
    int new_descriptor;
    int original_file_size;
    int result;

//    char original_file_name[] = "original.txt";
//    char new_file_name[] = "new.txt";
    char original_file_name[] = "picture.jpg";
//    char new_file_name[] = "znewpic.jpg";

    int parts = 2;
    int part_size;
    int part_number = 0;
    int bytes_read = 0;

static const unsigned MAXSIZE = 32;

    char partname[MAXSIZE];         
    int bytes_written;
    unsigned p;
    
    // Open the file.  If the result is -1 there was an error. Any
    // positive result will be the descriptor for the input file.

    result = open(original_file_name, O_RDONLY );
    if ( result == -1 ) 
    {
        printf("Error opening %s.", original_file_name);
        exit(EXIT_FAILURE);
    }
    original_descriptor = result;


    // Get the file size.

    struct stat buf;
    result = fstat(original_descriptor, &buf);
    if (result)
    {     
        fprintf(stderr, "error: fstat: %s\n", "error");
        exit(1);
    }
    original_file_size = buf.st_size;

    // Get the part size

    printf("The file is %0.2f Kilobytes large.\n", (double) (original_file_size/1024));
    part_size = (original_file_size + 1)/parts;
    if (part_size < 1)
    {
      part_size = 1;
    }

    // Create a buffer large enough to handle partsize bytes.

    char *buffer = malloc(part_size);

//int partnumber=0;
    char new_file_name[15]= "znewpic.jpg";

    do 
    {

    for (p = 0; p < parts; p++) {
        bytes_written = snprintf(partname, MAXSIZE, "%s.part%d",new_file_name , p);
        if (bytes_written >= MAXSIZE) {
            fprintf(stderr, "ERROR: Max length of part name is %d\n", MAXSIZE);
            exit(EXIT_FAILURE);
        }
       // puts(partname); // The rest of your code in here

    umask(0000);
 //   result = open(new_file_name, O_CREAT | O_TRUNC | O_WRONLY,0777 );    
    result = open(partname, O_CREAT | O_TRUNC | O_WRONLY,0777 );    
if ( result == -1 )
    {
      printf("Error opening %s\n", partname);
      exit(EXIT_FAILURE);

    }
    new_descriptor = result;
      
// Read data into buffer
        result = read(original_descriptor, buffer, part_size);
        if (result == -1) 
        {
           printf("Error reading from %s.\n", original_file_name);
           exit(EXIT_FAILURE);
        }
        bytes_read = result;
        printf("Writing part %d (%d bytes).\n", part_number, bytes_read);

        ++part_number;

      //  result = write(new_descriptor, buffer, bytes_read);
        result = write(new_descriptor, buffer, bytes_read);
        if (result == -1) 
        {
           printf("Error writing %d bytes to %s.\n", bytes_read, new_file_name);
           exit(EXIT_FAILURE);
        }

close(new_descriptor);
}


free(part_size);
    } while (result == part_size);


  // I'm lazy
  // At this point, close files and free buffer.

  return 0;  
      
}

```

---

### Post by dwhitney67 on 2013-01-03
You could avoid the ping-pong between read() and write() by using copyfile().

For example:
```

#include <errno.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <fcntl.h>
#include <unistd.h>
#include <sys/sendfile.h>
#include <sys/stat.h>
#include <libgen.h>

int main(int argc, char** argv)
{
    if (argc != 3)
    {
        fprintf(stderr, "Usage: %s <file> <parts>\n", argv[0]);
        exit(EXIT_FAILURE);
    }

    const char* orig_file_name = argv[1];
    const char* orig_base_name = basename(argv[1]);
    int parts = atoi(argv[2]);

    // ensure parts is not zero or less than zero.
    parts = (parts <= 0 ? 1: parts);


    // verify that we are given a real file.
    struct stat stat_buf;

    if (stat(orig_file_name, &stat_buf) == -1)
    {
        fprintf(stderr, "Error occurred; reason: %s [%d]\n", strerror(errno), errno);
        exit(EXIT_FAILURE);
    }

    if (!S_ISREG(stat_buf.st_mode))
    {
        fprintf(stderr, "Error occurred; %s is not a regular file.\n", orig_file_name);
        exit(EXIT_FAILURE);
    }

    // open original file (if it exists)
    int orig_fd = open(orig_file_name, O_RDONLY);

    if (orig_fd == -1)
    {
        fprintf(stderr, "Unable to open file %s\n", orig_file_name);
        exit(EXIT_FAILURE);
    }

    int   part_size = (stat_buf.st_size + 1) / parts;
    off_t offset = 0;

    for (int p = 0; p < parts; ++p)
    {
        char part_file_name[256];
        snprintf(part_file_name, sizeof(part_file_name), "%s.part.%d", orig_base_name, p); 

        int new_fd = open(part_file_name, O_CREAT | O_TRUNC | O_WRONLY, stat_buf.st_mode);

        if (new_fd == -1)
        {
            fprintf(stderr, "Unable to open parts file %s\n", part_file_name);
            exit(EXIT_FAILURE);
        }

        int result = sendfile(new_fd, orig_fd, &offset, part_size);

        if (result == -1)
        {
            fprintf(stderr, "Error writing data; reason: %s [%d]\n", strerror(errno), errno);
            exit(EXIT_FAILURE);
        }

        close(new_fd);
    }

    close(orig_fd);

    return 0;
}

```
I hope you do well in school.

---

### Post by nvteighen on 2013-01-03
> **dwhitney67 said:**
> You could avoid the ping-pong between read() and write() by using copyfile().


I suppose you meant "sendfile()"... Anyway, I didn't know that function and it's really really handy. Thanks! :)

(Btw, Happy New Year, dwhitney67!)

---

### Post by Bachstelze on 2013-01-03
> **nvteighen said:**
> I suppose you meant "sendfile()"... Anyway, I didn't know that function and it's really really handy. Thanks! :)

(Btw, Happy New Year, dwhitney67!)

copyfile() seems to be specific to OS X, it's the only OS I know of that has it. Also sendfile() is far from standard as well (afaik it's only on Linux, OS X and FreeBSD).

---

### Post by binaryperson on 2013-01-03
> **dwhitney67 said:**
> You could avoid the ping-pong between read() and write() by using copyfile().

For example:
```

#include <errno.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <fcntl.h>
#include <unistd.h>
#include <sys/sendfile.h>
#include <sys/stat.h>
#include <libgen.h>

int main(int argc, char** argv)
{
    if (argc != 3)
    {
        fprintf(stderr, "Usage: %s <file> <parts>\n", argv[0]);
        exit(EXIT_FAILURE);
    }

    const char* orig_file_name = argv[1];
    const char* orig_base_name = basename(argv[1]);
    int parts = atoi(argv[2]);

    // ensure parts is not zero or less than zero.
    parts = (parts <= 0 ? 1: parts);


    // verify that we are given a real file.
    struct stat stat_buf;

    if (stat(orig_file_name, &stat_buf) == -1)
    {
        fprintf(stderr, "Error occurred; reason: %s [%d]\n", strerror(errno), errno);
        exit(EXIT_FAILURE);
    }

    if (!S_ISREG(stat_buf.st_mode))
    {
        fprintf(stderr, "Error occurred; %s is not a regular file.\n", orig_file_name);
        exit(EXIT_FAILURE);
    }

    // open original file (if it exists)
    int orig_fd = open(orig_file_name, O_RDONLY);

    if (orig_fd == -1)
    {
        fprintf(stderr, "Unable to open file %s\n", orig_file_name);
        exit(EXIT_FAILURE);
    }

    int   part_size = (stat_buf.st_size + 1) / parts;
    off_t offset = 0;

    for (int p = 0; p < parts; ++p)
    {
        char part_file_name[256];
        snprintf(part_file_name, sizeof(part_file_name), "%s.part.%d", orig_base_name, p); 

        int new_fd = open(part_file_name, O_CREAT | O_TRUNC | O_WRONLY, stat_buf.st_mode);

        if (new_fd == -1)
        {
            fprintf(stderr, "Unable to open parts file %s\n", part_file_name);
            exit(EXIT_FAILURE);
        }

        int result = sendfile(new_fd, orig_fd, &offset, part_size);

        if (result == -1)
        {
            fprintf(stderr, "Error writing data; reason: %s [%d]\n", strerror(errno), errno);
            exit(EXIT_FAILURE);
        }

        close(new_fd);
    }

    close(orig_fd);

    return 0;
}

```I hope you do well in school.

Thank you for this solution. I didn't know there was a function called sendfile(). However, I am going to stick with the other method since it is almost working correctly.

---

### Post by dwhitney67 on 2013-01-03
> **nvteighen said:**
> I suppose you meant "sendfile()"... Anyway, I didn't know that function and it's really really handy. Thanks! :)

(Btw, Happy New Year, dwhitney67!)

Dooh!  Thanks for the correction.

---

### Post by binaryperson on 2013-01-03
So, no one knows why my code isn't working?

---

### Post by dwhitney67 on 2013-01-03
> **binaryperson said:**
> So, no one knows why my code isn't working?

What's the point of the do-while loop?  Take it out, and I suspect your program would work.

P.S.  I did not comment on your code earlier because you make it difficult to read with many lines that are commented out, others that are poorly indented, and other lines of code with an atypical style of declaring variables.

When declaring a string to reference a string-literal, something like the following will generally suffice:
```

const char* str = "Some String Literal";

```
If you have intentions of modifying a string-literal, then your style (of making a copy) would be appropriate.

---

### Post by binaryperson on 2013-01-03
I have more testing to do, but it seems as though removing the do-while loop did the trick! Thank you!

---

### Post by cross37 on 2013-01-04
You don't want to free the buffer until you are done using it (after the "do" loop completes).

Also, you want to free the buffer, not part_size.

This line allocates a buffer part_size bytes in size, and returns a pointer to it.
```
char *buffer = malloc(part_size);
```

To free the buffer:
```
free(buffer);
```

Trying to free(part_size) would certainly cause a segfault.

---

### Post by cross37 on 2013-01-04
Ok, now that I've reread this thread I'm not sure my last post even applies anymore...

---

### Post by binaryperson on 2013-01-04
Yes, it works now but I didn't use the free() function. I need to free the buffer but I'm not sure at which part of the code to do it? The very end, before return?

---

### Post by dwhitney67 on 2013-01-04
> **binaryperson said:**
> Yes, it works now but I didn't use the free() function. I need to free the buffer but I'm not sure at which part of the code to do it? The very end, before return?

Where you currently have it, just before the return statement, is fine.

Btw, I wanted to add that allocating a large amount of space is probably not the best approach.  You should consider reading from the source file in chunks of 1024 bytes (or something reasonable) until you fulfill the amount of bytes you need to write to the destination file.

You would want to avoid scenarios in which a large file (say 4 GB) is split into 1 part!

---

### Post by binaryperson on 2013-01-04
How difficult would it be to modify this code to have each new part created in a separate thread? So, 3 parts, 3 threads that run at the same time. Would it take a lot of modifying? Would writing each file in a separate thread be equivalent to or even better than the chunking you were talking about?

---

### Post by dwhitney67 on 2013-01-04
> **binaryperson said:**
> How difficult would it be to modify this code to have each new part created in a separate thread? So, 3 parts, 3 threads that run at the same time. Would it take a lot of modifying? Would writing each file in a separate thread be equivalent to or even better than the chunking you were talking about?

I could be wrong, but I do not think that accessing a file descriptor is thread-safe.  If I am correct, then you would need to open the file in each thread which might negate the time savings of just using a single thread.  Within each thread you would need to use lseek() to adjust the file descriptor to the appropriate location within the file to start reading.  The start location would need to be passed to the thread.

I won't design the app for you, but in essence you would need to let the thread know of the source file name, the start position for reading, and the part-number to create the output file.  A data structure would be handy to store all this data.

As for writing, this is a non-issue because you would be creating distinct files.

---

### Post by trent.josephsen on 2013-01-04
> **binaryperson said:**
> How difficult would it be to modify this code to have each new part created in a separate thread? So, 3 parts, 3 threads that run at the same time. Would it take a lot of modifying? Would writing each file in a separate thread be equivalent to or even better than the chunking you were talking about?
Splitting into threads is not going to speed up disk access. You would be much more likely to hurt your performance than help it.

You should know what they say about premature optimization...

---

### Post by binaryperson on 2013-01-06
How can I write a program that joins different files into one? Each file part is named file.extension.part0,file.extension.part1 and so on. One requirement is that you can't tell the program how many file parts there are. You just tell it the original name of the file: file.extension. Somehow it must realize how many parts there are and put them together.

---

### Post by ofnuts on 2013-01-07
> **binaryperson said:**
> How can I write a program that joins different files into one? Each file part is named file.extension.part0,file.extension.part1 and so on. One requirement is that you can't tell the program how many file parts there are. You just tell it the original name of the file: file.extension. Somehow it must realize how many parts there are and put them together.
```

If the parts files are sortable by name (ie; you have *part01-*part09 if there is a part10):
[code]
cat file.extension.part*  > file.extension

```
(bash guarantees the "file.extension.part*" will be replaced by an alphabetically sorted list)

---

