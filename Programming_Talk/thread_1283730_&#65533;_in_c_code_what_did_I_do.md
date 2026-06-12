---
title: "&#65533; in c code: what did I do??"
date: 2009-10-05
forum: Programming Talk
---

### Post by xem2189 on 2009-10-05
Okay code is pretty basic I think, but once again I've done something dumb that I can't figure out. 

Code takes a text file specified at the command line, opens, finds the size. All that works. Then I dynamically allocate memory for an array the same size as the file to read in the contents of the file into the array. I'm trying to use fread. It seems to work but when I check by printf it just prints out a bunch of &#65533; marks for the characters. What the heck did I do?

Heres part of my code, it's part of a bigger program for a class.

Thanks in advance for any help.

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char *argv[])
{

        // Initialize variables
        FILE *file_input;
        char *file_array;
        int file_size;
        char hold;
        int option = -1;
        int option_1;
        char option_2[31];
        int  option_3;
        int truth;
        int array_length;
        int length;
        int i;

        // Check to see if correct number of command line arguments
        if(argc != 2)
        {
                printf("\nIncorrect number of command line arguments.\n");
                printf("Must have two command line arguments. Exiting program.\n\n");
        }

        // Open the input file
        file_input = fopen(argv[1], "r");

        // Check if file opened correctly
        if(file_input == NULL)
        {
                printf("File %s could not be opened. Exiting program.", argv[1]);
                return 0;
        }

        // Determine the size of the file
        file_size = ftell(file_input); // Byte pointed to by file pointer
        fseek(file_input, 0, SEEK_END); // Move to the end of the file
        file_size = ftell(file_input);

        // Dynamically Allocate array
        file_array = (char *)calloc(file_size, sizeof(char));

        for(i = 0; i < 149; i ++)
        {
                printf("%c", file_array[i]);
        }

        // Check if memory allocated
        if(file_array == NULL)
        {
                printf("Could not allocate enough memory. Exiting program.\n");
                fclose(file_input);
                return 0;
        }

        // Scan the document into the array
        for(i = 0; i < file_size; i ++)
        {
                fread(&hold, 1, 1, file_input);
                file_array[i] = hold;
        }

        printf("%s", file_array);

        // Close the file
        fclose(file_input);
```

---

### Post by dwhitney67 on 2009-10-05
What are you trying to accomplish with this group of statements?
```

for(i = 0; i < 149; i ++)
{
printf("%c", file_array[i]);
}

```
You post did not indicate if you are reading printable data or binary data.  If the latter, then you may not be able to display all of the data using the %c formatter.  Consider printing with %x.

If you are reading printable data exclusively, then consider using fgetc() or if your data permits, fgets().

Btw, the for-loop above is repeatedly printing the zero-eth character of the ASCII table, which is a NUL ('\0').  It is not printable!

---

### Post by slavik on 2009-10-05
1. please edit your post and use code tags to post code.
2. is your input file plain text?
3. try using read as it will read bytes into a buffer.

---

### Post by xem2189 on 2009-10-05
I'm reading printable data, not binary. That group of statements doesn't really do anything, I was just messing around with malloc earlier and was using it see what was in the array.

Apparently I have a twisted approach to checking stuff.

---

### Post by fct on 2009-10-06
```
        // Determine the size of the file
        file_size = ftell(file_input); // Byte pointed to by file pointer
        fseek(file_input, 0, SEEK_END); // Move to the end of the file
        file_size = ftell(file_input);

```

Did you ever move back to the beginning of the file?

---

### Post by nvteighen on 2009-10-06
Hm... also, if you're using ASCII data, you better use **fgetc()** rather than **fread()**... It's much easier to use :p

---

