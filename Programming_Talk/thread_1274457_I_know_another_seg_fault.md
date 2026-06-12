---
title: "I know another seg fault"
date: 2009-09-24
forum: Programming Talk
---

### Post by xem2189 on 2009-09-24
Okay so this is my first post and I hope someone can help. I've been writing this program for a class and it is essentially done except for this one part which I've attached. Basically I want to open a file, in this case it is a list of words in the file linux.words, and then allocate memory so I can put the words into an array. Well I figured first that I need to know how many words were in the file and since I don't know any real shortcut on how to do that I wrote the code below to count how many times it scans in a word and use that number to allocate memory. 

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char *argv[])
{
    // Initialize variables
    FILE *dictionaryFile;    // Dictionary
    char **dictionary;    // Array to hold dictionary
    char dictionaryword;    // Word in the dictionary
    int num_word = 0;
    
    // Check if correct number of command line arguments
    if(argc != 2)
    {
        printf("\nError, insufficient command line arguments!");
        printf(" Exiting.\n\n");
        return 0;
    }

    // Open file
    dictionaryFile = fopen(argv[1], "r");
    
    // Verify file opened successfully
    if(dictionaryFile == NULL)
    {
        printf("\nError, dictionary file %s could not be opened\n\n", argv[1]);
        return 0;
    }

    fscanf(dictionaryFile, "%s", &dictionaryword);

    // Calculate the number of words in the dictionary
    while(!feof(dictionaryFile))
    {
        fscanf(dictionaryFile, "%s", &dictionaryword);
        printf("%d\n", num_words);
        num_words ++;
    }

    // Close the dictionary file
    fclose(dictionaryFile);

    return 0;
    
}

Problem: I keep getting a seg fault at the end of my while(!feof....) and I have absolutely no idea why that is happening. If someone could explain this to me that would be great.

---

### Post by MadCow108 on 2009-09-24
char dictionaryword; // Word in the dictionary
this has only room for a single char
so fscanf overwrites this

increase the size (e.g. char dictionaryword[100]) and replace fscanf with this:
fscanf(dictionaryFile, "%100s", dictionaryword);

---

### Post by napsy on 2009-09-24
```
fscanf(dictionaryFile, "%s", &dictionaryword)
```;

You are storing a string in 1-byte allocated memory.

---

### Post by xem2189 on 2009-09-24
Okay thanks guys. Sometimes it is just the simplest stuff. One more question though, and I think I know the answer but what does the 100 in %100s do?

---

### Post by napsy on 2009-09-24
it says only a string of 100 characters should be read by scanf()

---

### Post by xem2189 on 2009-09-24
Okay that makes sense. Thanks. :)

---

### Post by MadCow108 on 2009-09-24
this is just to make sure no buffer overflow happens because of malformed input.
it will truncate your data but that (when correctly handled) does not form a security risk

you could also use the "%as" flag so that scanf allocates its own memory of appropriate size
in that case you will have to explicitly free it again
see man fscanf
this is also a non standard extension of gcc so you will lose portability

---

### Post by dwhitney67 on 2009-09-24
A safer bet when reading C-string is to use fgets().  This function will stop reading after a newline character is found or one less than the number of characters specified is read.  If a newline is found, it is included in the result.

If a line has multiple words in it, then use strtok() or other "tool" to parse the line.

In the case the OP was attempting to solve, fgets() would be used as:
```

char dictionaryWord[100];
...
fgets(dictionaryWord, sizeof(dictionaryWord), dictionaryFile);

/* to remove a newline, if it exists */
char* nl = strchr(dictionaryWord, '\n');
if (nl) *nl = '\0';

...

```

---

