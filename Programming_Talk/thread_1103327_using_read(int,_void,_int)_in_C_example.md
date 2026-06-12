---
title: "using read(int, void, int) in C example?"
date: 2009-03-22
forum: Programming Talk
---

### Post by mcla0203 on 2009-03-22
Does anyone have an example of using read(int,void, int) in C?  I've had trouble finding something through google.

---

### Post by cmay on 2009-03-22
[http://www.opengroup.org/onlinepubs/009695399/functions/read.html](http://www.opengroup.org/onlinepubs/009695399/functions/read.html)
here is the opengroup specifications and i posted a sample from a book of mine i have yet to read which has a example of this function. book is beginning linux programming 4 edition. i am beginner at c so i can not make any other useful comments to this but hope it helps .

[php]

#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>

int main(int argc, char** argv)
{
    int nread;
    char buffer[128];
    
    nread=read(0,buffer,128);
    
    if(nread == -1)
     write(2,"an read error occured\n",26);
     
    if((write(1,buffer,nread))!= nread)
       write(2,"a write error occured\n",27);
    
    return 0;
}[/php]

---

### Post by mcla0203 on 2009-03-22
Yeah, that is the only decent reference I could find, but I couldn't make any sense of what the arguments are.  It is read(offset, buffer, number_of_bytes).. so I added in an int, a char* buffer, and an int number of bytes and it crashes.

---

### Post by hanniph on 2009-03-22
check out the manual. From the 'man read':
> ssize_t read(int fd, void *buf, size_t count);

DESCRIPTION
       read() attempts to read up to count bytes from file descriptor fd into the buffer starting at buf.


---

### Post by cmay on 2009-03-22
> so I added in an int, a char* buffer, and an int number of bytes and it crashes
the first parameter is a file descriptor 0,1,2 for stdin ,stdout stderr and buffer is a *buffer then last parameter is how many bytes to read as integer.

the example above(which i stole from the book) i gave you is just a simple filecopy rutine which will copy only 128 bytes if they exist  so for testing the example it is if used in a pipe on the commandline copying 128 bytes exactly to the stdout or prints error on stderr . 

i started using other books and fprintf to learn from  instead as my programs also crashed a lot;

---

### Post by geirha on 2009-03-22
All the functions of the standard c library has man-pages. You install the man-pages with the package [manpages-dev](apt:manpages-dev). After installing, you can run ```
man read
``` to get information on that function. Sometimes though, there are several man-pages with the same name. If you want information on the sleep function for instance, doing ```
man sleep
``` will give you the information on the sleep command instead of the sleep function. That's because it shows you the first hit it finds, and shell commands are in manual category 1, while standard c library functions are in categories 2 and 3. 3 in the case of the sleep function. In such a case, run ```

man 3 sleep
# or, to go through all hits in all categories
man -a sleep

```

---

