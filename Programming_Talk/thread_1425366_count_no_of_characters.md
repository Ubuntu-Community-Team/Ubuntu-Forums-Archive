---
title: "count no of characters"
date: 2010-03-09
forum: Programming Talk
---

### Post by LittleU on 2010-03-09
Hi ,

i have read that new line character gets converted to \r\n when writing characters to a file
and converted to new line again when reading.

but i observed one thing here.

i have written contents hello followed by return key .

and i have written a program to count the no of characters i got the result as 7.
then i tried printing character and its ascii value then its printing two characters with the same ascii value( 10 ) at the end . that mean its not converting \r\n to \n . if so the out put should be 6.

this is the program:

```

#include<stdio.h>
int main(int argc,char *argv[]) {
        FILE *fp;
        char ch;
        int nc=0;
        fp=fopen(argv[1],"r");
        if(!fp)
                printf("file doesnot exist\n");
        else {
        while((ch=fgetc(fp))!=EOF)
        {
                printf(" < %c > and < %d > \n", ch , ch );
                nc++;
        }
        printf("no of chars=%d",nc);
        }
return 0;
}


```

i many of the forums many ppl mentioned that there is no difference between text and binary on *nix systems.

the out put i got is:

> 
< h > and < 104 > 
 < e > and < 101 > 
 < l > and < 108 > 
 < l > and < 108 > 
 < o > and < 111 > 
 < 
 > and < 10 > 
 < 
 > and < 10 > 
no of chars=7


i am running programs on ubuntu 9.04
please help..

---

### Post by lisati on 2010-03-09
It can depend on the compiler and/or run-time libraries.

On my machine, the default settings for gcc result in a single character, 0x0a, to be written out for '\n' when compiled on Ubuntu.

Edit: a musing. Perhaps the gurus better versed in C can correct me if I'm mistaken: is it wise to use the value of CH if it triggered the EOF condition?

---

### Post by Reiger on 2010-03-09
I am not a C coder (much) but anyway:

As I understand it the C standard requires that "\n" is whatever the newline is on the platform the program is compiled on. Thus on Windows or Symbian it should be "\r\n", on Mac it should be "\r", and on Linux it is "\n". Thus relying on it for line deliminating may make files created/read with your program on various platforms be mutually incompatible with your program on different ones unless you take care to handle this yourself (there's probably a trim() function for that).

In C typically chars are in memory the same as bytes; thus strings are an array of chars are an array of bytes. However since 255 characters are no longer deemed sufficient range for most applications; many API's now specify that input must have a different type of characters or strings (different from *char).

As for the use of ch: It (ch) is never used after EOF is encountered? When EOF is assigned to it, the condition of the while{} loop becomes false, thus terminating the loop -- and I see no use of ch after that loop?

However it seems to me that fp is not properly disposed of.

---

### Post by Some Penguin on 2010-03-09
> **LittleU said:**
> Hi ,
i have read that new line character gets converted to \r\n when writing characters to a file
and converted to new line again when reading.


That's a poor assumption.   It's not part of the C language definition, and is more of a Microsoft-ism, and specifically when opening files as ASCII text rather than binary.  Most other systems including just about every Unix-type OS ignore binary-vs-ascii and write exactly what you ask them to -- no more, no less.

---

### Post by MindSz on 2010-03-09
I've had to write programs in Linux-C that create text files that are to be read in Windows. 

If I just write "\n" at the end of the file (the way Linus reads it) then in Windows' Notepad and Excel I see just a single line of text that ends at EOF. 

On the other hand, if I write "\r\n" then even though the notepad reads it as it's supposed to, my Linux system gives me a blank line after every data line.

---

### Post by Dougie187 on 2010-03-09
If you want a character count, you can always use the command line program "wc". For more information about it you can type ```
 man wc
``` but what you are looking for is the -m flag. So do this
```
wc -m *filename*
```and it should give you the number of characters in the file. Just an fyi.

---

### Post by dwhitney67 on 2010-03-09
> **Dougie187 said:**
> If you want a character count, you can always use the command line program "wc". For more information about it you can type ```
 man wc
``` but what you are looking for is the -m flag. So do this
```
wc -m *filename*
```and it should give you the number of characters in the file. Just an fyi.

I was just thinking the same thing.

And if the OP insists that the application must be done in C, then surely it is a homework assignment... and we all know this will lead the thread to be closed.

---

