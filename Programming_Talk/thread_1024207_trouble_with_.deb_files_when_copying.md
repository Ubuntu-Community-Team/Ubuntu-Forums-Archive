---
title: "trouble with .deb files when copying"
date: 2008-12-28
forum: Programming Talk
---

### Post by shindz on 2008-12-28
Hi all,
 I had nothing to do these days so I decided to write a copy programme.I'm not so good by programming.
 This programme should act like the copy fonction of an operating system.
 I don't want to rebuild whats was already done, I was just currious.
 After compiling, my programm works well on all file, just the .deb's file have a trouble. here is the message I have from the Debian file manager :
 ""Could not open opera_9.63.2474.gcc4.qt3_i386.deb.this paquets may be corrupted or you don't have rights to acces it. Please check your acces' rights. "

 But after the copy, the size is correct. here is the sample code :```

#include <stdio.h>
#include <stdlib.h>

void copy(char *dest, char *src, FILE* file);

int main()
{
    char src[100];
    char dest[100];
    FILE* output;
    printf("Please give the source's path of the file to copy :");
    gets(src);
    printf("Please give the destination's path of the file :");
    gets(dest);
    copy(dest,src,output);

    return 0;
}

void copy(char *dest, char *src, FILE* file)
{

    int N = 0;// count the character number of the file
    int C = 0;

    FILE* tocopy = fopen(src,"r");// opening the file to copy from in the read mode
    if(!tocopy)
    {
        printf("Can't find the file %s\n",src);
        return -1;
    }
   file = fopen(dest,"w"); // opening the destination file in the writting mode
   if(!file)
   {
       printf("Can't create teh file %s at this place\n",dest);
       return -1;
   }
    while(!feof(tocopy)) // here run the copy
    {
        C = fgetc(tocopy);
       fputc(C,file);

       N++;
     }
   fclose(tocopy);
   fclose(file);
}

```

---

### Post by snova on 2008-12-28
Run 'md5sum' on the original file and the duplicate, to confirm that they are different.

Try opening the file in "rb" mode.

---

