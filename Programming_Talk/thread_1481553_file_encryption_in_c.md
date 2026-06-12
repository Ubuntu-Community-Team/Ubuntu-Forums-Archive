---
title: "file encryption in c"
date: 2010-05-12
forum: Programming Talk
---

### Post by oscurochu on 2010-05-12
I'm trying to write a simple program that encrypts a file. I'm new to C, and I'm overwhelemed with errors, :confused:
 Here is my code:
[PHP]#include <string.h>
char encrypt_file(char *source_file[100], char *key[100], int save_file )
{
    int key_count = 0; //Used to restart key if strlen(key) < strlen(encrypt)
    int i;
    char destination_file[104], *file_contents, *encrypt_byte;
    FILE *from, *to;
    strcpy(destination_file, *source_file);
    strcat(destination_file, ".tmp");
    /* open source file */
    if ( ( from = fopen(*source_file, "rb") ) == NULL) {
        //printf("Cannot open source file.\n");
        return 1;
    }
    if ( save_file == 1 )
    {
        /* open destination file */
        if ( ( to = fopen(destination_file, "wb")) == NULL ) {
            //printf("Cannot open destination file.\n");
            return 1;
        }
        //Loop through each byte of file until EOF
        while ( ( encrypt_byte = fgetc(from) ) != EOF ) 
        {
            //XOR the data and write it to a file
            fputc(encrypt_byte ^ key[key_count], to);
            //Increment key_count and start over if necessary
            key_count++;
            if ( key_count == strlen(key) )
            {
                key_count = 0;
            }
        }
        if ( fclose(from) == EOF )
        {
            //printf("Error closing source file.\n");
            return 1;
        }
        if ( fclose(to) == EOF )
        {
            //printf("Error closing destination file.\n");
            return 1;
        }
        remove(source_file);
        rename(destination_file, source_file);
    }
    else
    {
    
        /* open source file */
        if ( ( from = fopen(source_file, "rb") ) == NULL) {
            cls();
            printf("Error encountered: Cannot open source file.\n");
            return 1;
        }
        //Loop through each byte of file until EOF
        for ( i = 0; ( encrypt_byte = fgetc(from) ) != EOF; i++ ) 
        {
            //XOR the data and write it to a file
            file_contents[i] = encrypt_byte ^ key[key_count];
            //Increment key_count and start over if necessary
            key_count++;
            if ( key_count == strlen(key) )
            {
                key_count = 0;
            }
        }
        if ( fclose(from) == EOF )
        {
            return file_contents;
        }
    }
}
[/PHP]And here's the problem: [PHP]
encrypt.h:23: warning: assignment makes pointer from integer without a cast
encrypt.h:23: warning: comparison between pointer and integer
encrypt.h:26: error: invalid operands to binary ^ (have &#8216;char *&#8217; and &#8216;char *&#8217;)
encrypt.h:29: warning: passing argument 1 of &#8216;strlen&#8217; from incompatible pointer type
/usr/include/string.h:397: note: expected &#8216;const char *&#8217; but argument is of type &#8216;char **&#8217;
encrypt.h:44: warning: passing argument 1 of &#8216;remove&#8217; from incompatible pointer type
/usr/include/stdio.h:155: note: expected &#8216;const char *&#8217; but argument is of type &#8216;char **&#8217;
encrypt.h:45: warning: passing argument 2 of &#8216;rename&#8217; from incompatible pointer type
/usr/include/stdio.h:157: note: expected &#8216;const char *&#8217; but argument is of type &#8216;char **&#8217;
encrypt.h:51: warning: passing argument 1 of &#8216;fopen&#8217; from incompatible pointer type
/usr/include/stdio.h:249: note: expected &#8216;const char * __restrict__&#8217; but argument is of type &#8216;char **&#8217;
encrypt.h:57: warning: assignment makes pointer from integer without a cast
encrypt.h:57: warning: comparison between pointer and integer
encrypt.h:60: error: invalid operands to binary ^ (have &#8216;char *&#8217; and &#8216;char *&#8217;)
encrypt.h:63: warning: passing argument 1 of &#8216;strlen&#8217; from incompatible pointer type
/usr/include/string.h:397: note: expected &#8216;const char *&#8217; but argument is of type &#8216;char **&#8217;
encrypt.h:71: warning: return makes integer from pointer without a cast[/PHP]

---

### Post by MadCow108 on 2010-05-12
encrypt_byte is a pointer, but fgetc returns an int. fix the types

char *source_file[100], char *key[100]
which is equivalent to:
char **source_file, char **key
do you really want pointer-to-pointer arrays here?

I guess you mean this:
char *source_file, char *key
or the equivalent:
char source_file[], char key[]

you are also missing some headers (stdio.h e.g.) and you should not put that code in a header but in a c file.
If you do need it in a header, add a static __attribute__((unused)) to the declaration to avoid multiple definition errors and unused function warnings when used in more than one c file

---

### Post by oscurochu on 2010-05-15
Ok, what about the last error, on line 71?

---

### Post by lisati on 2010-05-15
> **oscurochu said:**
> Ok, what about the last error, on line 71?

I'm not sure of this but your function returns a char, and you appear to be trying to return a pointer to a char.

---

### Post by oscurochu on 2010-05-15
i want to return a c-string

---

### Post by lisati on 2010-05-15
> **oscurochu said:**
> i want to return a c-string

I will have to defer to the knowledge & wisdom of someone more experienced with C than myself.....

---

### Post by MadCow108 on 2010-05-15
look at your types:

**char** encrypt_file(char *source_file[100], char *key[100], int save_file );
**char***file_contents;
...
return file_contents;

I also just saw you never allocate any space for file_content. So it is unlikely your program will work.
and fclose only returns EOF on error, not on success, so that last check is weird: you return undefined value on success and defined value on error.

You should better have a look at some C basics again notably the type system and memory model.

---

### Post by oscurochu on 2010-05-15
the file_content is a variable size, how would I allocate memory for it? What if I don't allocate enough memory?

---

### Post by MadCow108 on 2010-05-15
you allocate big blocks of memory using malloc/calloc/realloc
malloc an uninitialized block of memory
calloc allocates initialized to zero
realloc can resize an existing block to a new size.

if you do not allocate enough memory your program will have undefined behavior and mostly crash (often with an so called segmentation fault).

---

### Post by Some Penguin on 2010-05-15
One simple approach is to allocate for and read in blocks of a fixed size (e.g. 8KB at a time, whatever), while building a linked list (each node would need to contain the pointer to that array, plus number of bytes actually used in that block).   Track the total.  When you're done, allocate a block of that size.

It's space-inefficient, because it takes more than twice the memory it would need in a perfect implementation, but it's useful in certain cases such as receiving content during an HTTP request (as the content-length header may in fact be a very uninformative -1; you want to keep reading until you can't read anymore, or you hit a size limit of your choosing, or you hit a time limit of your choosing).

In a more ordinary case like a local file, you can use the stat() calls (at least on Unix-y systems) to obtain the file size, and allocate that much space and stop reading when you hit it.  You could then recheck the file size; it's up to you to decide how to handle it if the file size has changed while you're reading it. 

Neither is a great thing to do if the file won't fit in memory, of course.  Since you're just using XOR, you could read/encrypt/write in chunks rather than load the whole thing THEN process.

---

