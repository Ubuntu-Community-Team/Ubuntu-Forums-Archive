---
title: "fopen doesn't seem to like non-constant char* in C"
date: 2010-03-28
forum: Programming Talk
---

### Post by ownaginatious on 2010-03-28
Hello everyone,

I'm having trouble with the fopen function in C, in the sense that it won't open files if I don't send the function the file path as a hardcoded string.

i.e. This works:

```
FILE * fileOne = fopen("/media/textfile.txt", "rb");
```

But this appears to not work...
```
FILE * fileOne = fopen(file1, "rb");
```
where file1 is a string (char*) that I sent to if from a function.

I'm probably missing something really stupid here....

Thanks :)

---

### Post by MadCow108 on 2010-03-28
please post more code
the problem is impossible to see from this single line

there is probably something wrong with the string.
maybe its not null terminated
what happens if you print it?

---

### Post by tookyourtime on 2010-03-28
I can compile and run this perfectly. Are you doing something different?

```
#include <stdio.h>
#include <stdlib.h>

void read(char * path)
{
    FILE * test;
    char * ReadBuffer[50];

    test = fopen(path, "r");

    fread (ReadBuffer,1,49,test);

    printf(ReadBuffer);

}

int main()
{
    char * path[256];

    gets(path);
    read(path);

    return 0;
}
```

---

### Post by ownaginatious on 2010-03-28
If I print it using:

```
printf("%s\n", file1)
```

It appears to come out fine. Would this still be printed if I had not null-terminated the string?

Also, this string was originally concatenated using the strncat function with something else. Is it write to assume that that function automatically takes care of nulling the end of the string?

---

### Post by ownaginatious on 2010-03-28
Here is what I'm doing at the beginning of the function:

```
// Files must be as a binary stream
int compare_files(char* file1, char* file2){

   FILE * fileOne = fopen(file1, "rb");
   FILE * fileTwo = fopen(file2, "rb");

   printf("---> %s\n---> %s\n", file1, file2);

   int count = 0, sizeOne = 0, sizeTwo = 0;
   
   if(fileOne == NULL || fileTwo == NULL){
      printf("One of the input files is null or both are null\n");
      return 0;
     ...
   }

```

The program always terminates at that if statement, and I'm definitely sure that the files do infact exist :s.

---

### Post by MadCow108 on 2010-03-28
you can get the actual error occurring in fopen with strerror(errno)
maybe that helps

please show the function creating the strings

also running your code through valgrind might help finding the problem

---

### Post by lisati on 2010-03-28
> **ownaginatious said:**
> Here is what I'm doing at the beginning of the function:

```
// Files must be as a binary stream
int compare_files(char* file1, char* file2){

   FILE * fileOne = fopen(file1, "rb");
   FILE * fileTwo = fopen(file2, "rb");

   printf("---> %s\n---> %s\n", file1, file2);

   int count = 0, sizeOne = 0, sizeTwo = 0;
   
   if(fileOne == NULL || fileTwo == NULL){
      printf("One of the input files is null or both are null\n");
      return 0;
     ...
   }

```

The program always terminates at that if statement, and I'm definitely sure that the files do infact exist :s.
My question would be: what is fopen() seeing in file1 and file2?

---

### Post by gnometorule on 2010-03-28
> **ownaginatious said:**
> 
Also, this string was originally concatenated using the strncat function with something else. Is it write to assume that that function automatically takes care of nulling the end of the string?

Yes, assuming that both strings to be concatenated were valid C-style strings (aka, '\0' terminated).

---

### Post by ownaginatious on 2010-03-28
The strings I'm getting are from the DIR* dir = opendir(path).

EDIT:

Thanks for the tip MadCow108, it turned out I had "too many files open". I fixed it now, thanks :).

---

