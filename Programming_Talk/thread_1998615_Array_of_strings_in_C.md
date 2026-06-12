---
title: "Array of strings in C"
date: 2012-06-07
forum: Programming Talk
---

### Post by Datweakfreak on 2012-06-07
Hey people,

I just started learning C, so I thought of writing a program that populates a dynamic array of strings with individual lines from a file, but it keeps segfaulting at keyFile_parse while trying to malloc contentArray. What am I doing wrong here?

```

#include <stdio.h>
#include <assert.h>
#include <stdlib.h>
#include <errno.h>
#include <string.h>

void terminate(const char *message)
{
    if (errno) {
        perror(message);
    } else {
        printf("ERROR: %s\n", message);
    }

    exit(1);
}

int countLines(char *keyFile)
{
    int lineCount = 0, charStream;
    FILE *fptr;
    fptr = fopen(keyFile, "r");

    if (!fptr) terminate("Key file not found.");

    do {
        charStream = fgetc(fptr);
        if (charStream == '\n')
            lineCount++;
    } while (charStream != EOF);
    fclose(fptr);

    return lineCount;
}

char keyFile_parse(char *keyFile, int lineCount)
{
    char lineBuffer[BUFSIZ];
    FILE *fptr;
    fptr = fopen(keyFile, "r");

    if (!fptr) terminate("Key file not found.");
    char **contentArray;
    int lineTrans = 0;
    char *lineContent = NULL;

    lineContent = malloc(sizeof(char*));
    
    while ((lineContent = fgets(lineBuffer, sizeof(lineBuffer), fptr)) && lineTrans <= lineCount) {
        contentArray[lineTrans] = malloc(sizeof(char*));
        contentArray[lineTrans] = lineContent;    
        lineTrans++;
        printf("%s\n", contentArray[lineTrans]);
    }

    free(contentArray);
    free(lineContent);
    fclose(fptr);
}

int main(int argc, char *argv[])
{
   keyFile_parse("Foo.txt", countLines("Foo.txt"));
   return 0;
}
```Running it on valgrind shows this [trace]("http://pastie.org/4042651").

I'd appreciate some help on this.

Thanks!

---

### Post by Bachstelze on 2012-06-07
1. You never allocate any memory for contentArray.
2. You read the data into lineBuffer, and then you do nothing with it.
3. Your function is supposed to return a char*, but you return nothing.

Those are the most obvious problems, there might be others...

---

### Post by Bachstelze on 2012-06-07
This works but I don't find it very elegant. There's probably a better solution that eludes me right now, it is late here. :p

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define BUFSIZE 1024

void usage(char *s)
{
    fprintf(stderr, "Usage: %s [inputfile]\n", s);
    exit(EXIT_FAILURE);
}

int parse(char *inputfile, char ***array)
{
    FILE *ifile = fopen(inputfile, "r");
    if (ifile == NULL) {
        perror("Could not open input file");
        return -1;
    }

    *array = malloc(0);
    char buf[BUFSIZE];
    int n = 0;
    while (fgets(buf, BUFSIZE, ifile) != NULL) {
        n++;
        *array = realloc(*array, n*sizeof(char*));
        int lbuf = strlen(buf);
        (*array)[n-1] = malloc(lbuf+1);
        strncpy((*array)[n-1], buf, lbuf+1);
    }
    if (!feof(ifile)) {
        perror("Error reading input file");
        fclose(ifile);
        return -1;
    }
    return n;
}

int main(int argc, char **argv)
{
    if (argc != 2) {
        usage(argv[0]);
    }
    char **array;
    int n = parse(argv[1], &array);
    printf("Read %d strings:\n", n);
    for (int i=0; i<n; i++) {
        printf("%s", array[i]);
        free(array[i]);
    }
    free(array);
}

```

---

### Post by Datweakfreak on 2012-06-07
I've managed to fix it. w00t!

```
void keyFile_parse(char *keyFile, int lineCount)
{
    char lineBuffer[BUFSIZ];
    FILE *fptr;
    fptr = fopen(keyFile, "r");

    if (!fptr) terminate("Key file not found.");
    char **contentArray;
    int lineTrans = 1;

    contentArray = malloc(sizeof(char*));

    while (fgets(lineBuffer, sizeof(lineBuffer), fptr) && lineTrans <= lineCount) {
        contentArray = realloc(contentArray, lineTrans * sizeof(lineBuffer));
            *(contentArray+lineTrans) = (char*)lineBuffer;    
        printf("%s", *(contentArray + lineTrans));
        lineTrans++;
    }

    free(contentArray);
    fclose(fptr);
}
```

Thanks for your help, Bachstelze! :D

---

### Post by Bachstelze on 2012-06-07
This only works because you print the lines as you read them. The lines are NOT stored correctly!

```
firas@av104151 ~ % cat foo.txt                                           
foo
bar
baz
supercalifragilisticexpialidocious
baz
foo
bar
firas@av104151 ~ % cat test.c 
#include <stdio.h>
#include <assert.h>
#include <stdlib.h>
#include <errno.h>
#include <string.h>

void terminate(const char *message)
{
    if (errno) {
        perror(message);
    } else {
        printf("ERROR: %s\n", message);
    }

    exit(1);
}

int countLines(char *keyFile)
{
    int lineCount = 0, charStream;
    FILE *fptr;
    fptr = fopen(keyFile, "r");

    if (!fptr) terminate("Key file not found.");

    do {
        charStream = fgetc(fptr);
        if (charStream == '\n')
            lineCount++;
    } while (charStream != EOF);
    fclose(fptr);

    return lineCount;
}

char **keyFile_parse(char *keyFile, int lineCount)
{
    char lineBuffer[BUFSIZ];
    FILE *fptr;
    fptr = fopen(keyFile, "r");

    if (!fptr) terminate("Key file not found.");
    char **contentArray;
    int lineTrans = 1;

    contentArray = malloc(sizeof(char*));

    while (fgets(lineBuffer, sizeof(lineBuffer), fptr) && lineTrans <= lineCount) {
        contentArray = realloc(contentArray, lineTrans * sizeof(lineBuffer));
            *(contentArray+lineTrans) = (char*)lineBuffer;    
        lineTrans++;
    }
    return contentArray;

    fclose(fptr);
}

int main(int argc, char *argv[])
{
    int n = countLines("foo.txt");
    char **array = keyFile_parse("foo.txt", n);
    for (int i=1; i<=n; i++) {
        printf("%s", array[i]);
    }
    free(array);
    return 0;
}
firas@av104151 ~ % gcc -std=c99 -pedantic -Wall -Wextra -g -o test test.c
test.c:58: warning: unused parameter &#8216;argc&#8217;
test.c:58: warning: unused parameter &#8216;argv&#8217;
firas@av104151 ~ % ./test
bar
bar
bar
bar
bar
bar
bar

```

---

### Post by Datweakfreak on 2012-06-07
*gulp* Got hasty there, I guess. I thought it might have something to do with seeking back to the beginning of the file, so I did some fseek()ing, but that isn't helping either, the array in main() keeps returning the last line of the file 10 times instead of the 10 lines.

---

### Post by Bachstelze on 2012-06-07
Compare your code with mine and look what I did differently when I store the string in the array.

---

### Post by Bachstelze on 2012-06-07
Also you do not need to use realloc() in your code, since you know in advance how many strings you have, you can just allocate all the space at once. In my code I use realloc() because I don't calculate the number of strings beforehand.

---

### Post by Datweakfreak on 2012-06-07
Alright, thanks Bachstelze, that helped me fix the code, though it's leaking memory. I realize it's because I can't free contentArray before returning the function, so how do I go about freeing this memory? Making it a static variable and freeing it from within main() or something?

```
#include <stdio.h>
#include <assert.h>
#include <stdlib.h>
#include <errno.h>
#include <string.h>

#define BUFSIZE 1024

void terminate(const char *message)
{
    if (errno) {
        perror(message);
    } else {
        printf("ERROR: %s\n", message);
    }

    exit(1);
}

int countLines(char *keyFile)
{
    int lineCount = 0, charStream;
    FILE *fptr;
    fptr = fopen(keyFile, "r");
    fseek(fptr, 0L, SEEK_SET);

    if (!fptr) terminate("Key file not found.");

    do {
        charStream = fgetc(fptr);
        if (charStream == '\n')
            lineCount++;
    } while (charStream != EOF);
    fclose(fptr);
    
    return lineCount;
}

char **keyFile_parse(char *keyFile, int lineCount)
{
    char lineBuffer[BUFSIZE];
    FILE *fptr;
    fptr = fopen(keyFile, "r");
    fseek(fptr, 0L, SEEK_SET);

    if (!fptr) terminate("Key file not found.");
    char **contentArray;
    int lineTrans = 0;

    contentArray = malloc(lineCount * sizeof(char*));

    while (fgets(lineBuffer, sizeof(lineBuffer), fptr)) {
        lineTrans++;
        int bufLen = strlen(lineBuffer);
        contentArray[lineTrans - 1] = malloc(bufLen + 1);
        strncpy(contentArray[lineTrans - 1], lineBuffer, bufLen + 1);
    }

    fclose(fptr);

    return contentArray;
}


int main(int argc, char *argv[])
{
    int i;
    int n = countLines("Foo.txt");
    char **array = keyFile_parse("Foo.txt", n);
    for (i = 0; i < n; i++) {
        printf("%s", array[i]);
    }
    free(array);
    return 0;
}
```Here's the valgrind output: [http://pastie.org/4044426](http://pastie.org/4044426)

---

### Post by dwhitney67 on 2012-06-07
Examine the code in BOLD text below:
```

int main(int argc, char *argv[])
{
    int i;
    int n = countLines("Foo.txt");
    char **array = keyFile_parse("Foo.txt", n);
    for (i = 0; i < n; i++) {
        printf("%s", array[i]);
        **free(array[i]);**
    }
    free(array);
    return 0;
}

```

Btw, this code can be reduced:
```

int bufLen = strlen(lineBuffer);
contentArray[lineTrans - 1] = malloc(bufLen + 1);
strncpy(contentArray[lineTrans - 1], lineBuffer, bufLen + 1);

```
to
```

contentArray[lineTrans - 1] = strdup(lineBuffer);

```

---

### Post by Datweakfreak on 2012-06-07
==2271== All heap blocks were freed -- no leaks are possible

Sweetest message I've seen all day, thanks, dwhitney67 and Bachstelze! 

So, even if I'm not using the dynamic array in main(), it isn't a bad idea to free the allocated memory outside of the function where it's mem-allocated?

Also, heck, as a python guy, I gotta say, C is lovely.

---

### Post by Bachstelze on 2012-06-07
> **Datweakfreak said:**
> 
So, even if I'm not using the dynamic array in main(), it isn't a bad idea to free the allocated memory outside of the function where it's mem-allocated?


It's not a problem at all. Of cours,e if you distribute your code, you have to say in the documentation that the caller is responsible for free()ing the memory.

---

