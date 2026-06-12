---
title: "Trouble with printf !!"
date: 2009-12-22
forum: Programming Talk
---

### Post by Mathew Roy on 2009-12-22
Hi,
I am a LINUX newb and now learnig myself how to program in LINUX !. I tried to make a program to copy one file to another location!. The printf() in the program is behaving in doo manner!.. plz help. Here is the program!.
The program does copy the file correctly but the printf() does not function properly!:confused:!.  My idea is to display the statitics of copying while copying. But when the printf does not function properly, how do I implement that :(.

PLZ HELP.:lolflag:

[php]
#include </usr/include/sys/types.h>
#include </usr/include/sys/stat.h>
#include <fcntl.h>
#include <stdio.h>

#define HELP 1
#define COPY 2

void disp_help();

int main(int argc, char *argv[])
{
 char buffer[512000],source[512],dest[512];
 int inhandle,outhandle,bytes,i;
 char cmd=0;
 printf("argc = %d",argc);
 for(i=0;i<argc;i++)
 {
  printf("\nargv[%d]=%s",i+1,argv[i]);
  if(!strcmp(argv[i],"h")||!strcmp(argv[i],"help"))
  cmd=cmd|HELP;
  if(!strcmp(argv[i],"C")||!strcmp(argv[i],"c")||!strcmp(argv[i],"copy"))
  cmd=cmd|COPY;
 }
 if(argc==1||cmd & HELP)
 {disp_help();
  return 0;
 }
 else if(cmd==0)
 printf("\nError : No commands received\n");
 else
 {strcpy(source,argv[1]);
  strcpy(dest,argv[2]);
 }
 
 if(cmd & COPY)
 {printf("\n\nCopy\n----\nCopying ...");                                  //Trobule here (1)
    /* the last "Copying..." appears only after copying the file*/
  if(inhandle=open(source,O_RDONLY),inhandle == -1)
  {printf("\nCannot open source file \"%s\"\n",source);
   return 1;
  }
  if(outhandle=open(dest,O_CREAT|O_WRONLY,S_IWRITE),outhandle ==-1)
  {printf("\nCannot open output file \"%s\"\n",dest);
   return 2;
  }
  while(1)
  {
   bytes=read(inhandle,buffer,512000);
   if(bytes>0)
   {write(outhandle,buffer,bytes);
    printf(".");                                                     //Trouble here (2)
                                                                         //The printf() over is not working in the proper order!...
   }
   else
   {
    printf("\b\bcompleted!..."); 
    break;
   }
  }
 }
 return 0;
}

void disp_help()
{
  printf("\n\nFile copier:-HELP\n-----------------\n");
  printf("!Welcome to File copier!\n");
  printf("Agruments: <sorce file> <destination file>");;
  putchar('\n');
}
[/php]

---

### Post by Sockerdrickan on 2009-12-22
> **Mathew Roy said:**
> 
[php]
 char buffer[512000]
[/php]
Ok now that's not good. Use dynamic memory allocation for buffer or your application might crash (it would for sure on windows)

---

### Post by MadCow108 on 2009-12-22
try fflush(stdout) after your printf's. this will print the stdout buffer onto the screen immediately.
also you're missing the include <string.h> and <unistd.h> as the warnings should have told you (always compile with -Wall)

and this:
char buffer[512000]
it not very nice, your wasting lots of precious stack space
allocate the buffer in heap with malloc (or use a smaller buffer repeatedly)

getopt is quite helpful for parsing command line options:
[http://www.gnu.org/s/libc/manual/html_node/Getopt.html](http://www.gnu.org/s/libc/manual/html_node/Getopt.html)

---

### Post by volodymyr on 2009-12-22
> **Tux0r said:**
> Ok now that's not good. Use dynamic memory allocation for buffer or your application might crash (it would for sure on windows)

Don't think so. By default, in Windows the stack size of thread is 1 MB. Original Poster (OP) reserves ~0.4 MB of stack, so there is still ~0.6 MB :)

---

### Post by Zugzwang on 2009-12-22
Is it possible that you need to flush the "stdout" in order to have you output appearing? As you don't have a newline at the end of the line in which you have trouble, this could be the problem. At least IDEs are likely not to display the line until it has ended.

By the way, if this program crashes in Windows because or insufficient stack space, at least the user gets a stack overflow error message instead of a segfault. So at least the error it is a little bit more informative. :-)

BTW, does anyone know why Linux doesn't distinguish between segfaulting and a stack overflow?

---

### Post by Mathew Roy on 2009-12-22
> **MadCow108 said:**
> try fflush(stdout) after your printf's. this will print the stdout buffer onto the screen immediately.
also you're missing the include <string.h> and <unistd.h> as the warnings should have told you (always compile with -Wall)

and this:
char buffer[512000]
it not very nice, your wasting lots of precious stack space
allocate the buffer in heap with malloc (or use a smaller buffer repeatedly)


Thanks a lot dude...:guitar:
I am terribly sorry I did not include string.h and unistd.h.
Well ur idea did really work!..Congrats, super idea!. The idea never occured to me. But I have a small doubt!. Will flushing in loop make the program run slower?
One more thing, do anyone know how to optimise the process of copying (by adjusting buffer etc.)?

Well it would have been really helpful if anyone could tell me how to use malloc. Otherwise also its not a big problem, I will refer.

Any way thanks a lot everyone especially MadCow108

---

### Post by dwhitney67 on 2009-12-22
> **Mathew Roy said:**
> Thanks a lot dude...:guitar:
I am terribly sorry I did not include string.h and unistd.h.
Well ur idea did really work!..Congrats, super idea!. The idea never occured to me. But I have a small doubt!. Will flushing in loop make the program run slower?
One more thing, do anyone know how to optimise the process of copying (by adjusting buffer etc.)?

Well it would have been really helpful if anyone could tell me how to use malloc. Otherwise also its not a big problem, I will refer.

Any way thanks a lot everyone especially MadCow108

Anytime an application performs I/O to disk or the terminal, it will run slower than if it did not do those things.  Since you are reading lots of data at any given iteration, I would not worry about the efficiency of the printf() call.  The disk I/O will be the main hog.

As for malloc:
```

#include <stdlib.h>
#include <stdio.h>

int main()
{
   /* allocate buffer */
   char* buffer = malloc(512000);

   if (buffer)
   {
      /* use buffer */

      /* deallocate when done with buffer */
      free(buffer);
   }
   else
   {
      fprintf(stderr, "Error allocating memory!\n");
      return -1;
   }

   return 0;
}

```

---

### Post by Mathew Roy on 2009-12-22
Thanks a lot, I learned quite a lot with ur help!...
Does anyone know how to optimise the process of copying (by adjusting buffer etc.)?

---

### Post by Arndt on 2009-12-22
> **Zugzwang said:**
> 
BTW, does anyone know why Linux doesn't distinguish between segfaulting and a stack overflow?

Probably because stack operations are not definitely recognizable as such. Some processors and operating systems have/had special segments for the stack, special registers to point to them, and information in the stack pointer on how big the stack is. Then, it is easy to see that an attempt to store one more thing on the stack will fail and report it as a stack overflow. Typically in Unix, some part of the linear memory is allocated, and a register made to point at the beginning. Nothing in particular keeps track of the end. The kernel could make a guess, if an illegal access is very near the highest allocated stack block, and report that as stack overflow, but I suppose the Unix designers didn't find that sufficiently useful.

---

### Post by lisati on 2009-12-22
> **Mathew Roy said:**
> Thanks a lot, I learned quite a lot with ur help!...
Does anyone know how to optimise the process of copying (by adjusting buffer etc.)?

One way might be to base the size of the buffer on the size of the file. This can be done by seeking to the end of the file and then using ftell() to get the file size. There's an example buried in the source code @ [http://www.mrx.net/c/source.html](http://www.mrx.net/c/source.html)

---

### Post by MadCow108 on 2009-12-23
that does not necessarily make the copy faster (io is bounded by disk speed not by cpu/ram speed) and it scales very badly as hard disk files can be a lot bigger than the available ram.

I recall having heard that the linux kernel hard disk writes are optimized for chunks of 4 mb on ext systems, but I have no source for that and have never tested it, so it could be nonsense.

---

