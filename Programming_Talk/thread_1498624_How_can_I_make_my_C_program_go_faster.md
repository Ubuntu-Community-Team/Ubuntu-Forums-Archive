---
title: "How can I make my C program go faster?"
date: 2010-06-01
forum: Programming Talk
---

### Post by ownaginatious on 2010-06-01
Now before anyone tells me something like this already exists, this is purely an experiment to help me learn C ;).

Anyway, I got bored and decided to try and make a C program that works very similarly to "cp" in Unix, except that it also shows me a progress bar when I'm copying a file.

Right now the only way to copy a file from one place to another is by hardcoding the paths in.

It seems to work, but the copy speed is relatively slow.

Does anyone know any tips on how I can make the copying faster?

Thanks!

```

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

long fileSize(FILE* input_file);
void copy_file(char* from_path, char* to_path);

int main(){
   char * file1 = "/path/to/existing/file";
   char * file2 = "/path/to/copy/to";

   copy_file(file1, file2);
}

long fileSize(FILE* input_file){
   long size;
   
   fseek(input_file, 0, SEEK_END);
   size = ftell(input_file);
   fseek(input_file, 0, SEEK_SET);

   return size;
}

// Copys one file from one location to another
void copy_file(char* from_path, char* to_path){

   FILE * old_file = fopen(from_path, "rb");
   FILE * new_file = fopen(to_path, "wb");
   
   long totalSize = fileSize(old_file);
   
   int percent = 0;
   double last = 0;
   double speed = 0;
   
   long count = 0, difference = 0, lastTime = 0, lastCount = 0;
   
   int i = 0;

   time_t timer = time(NULL);
   
   while(!feof(old_file)){
     
     timer = time(NULL);
     
     percent = (int)(100 * count++/totalSize);

     difference = timer - lastTime;
     
     if(difference >= 1){
       speed = count - lastCount;
       lastCount = count;
       lastTime = timer;
       fflush(stdout);
       last = percent;
       printf("%d% |", percent);
       for(i = 0; i < 10; i++)
	 if(i < (int)percent/10)
	    printf("*");
	 else
	    printf("-");
       printf("| [%f MB/s]\r", speed/(1024*1024));
     }
     putc(fgetc(old_file), new_file);
   
   }
   
   printf("\n");
   
   fclose(old_file);
   fclose(new_file);
}

```

---

### Post by Finalfantasykid on 2010-06-01
```
putc(fgetc(old_file), new_file);
```

I'm not a c expert, but my guess would be this line is your culprit.  Moving 1 character of the file at a time creates a massive number of I/O operations.  If you move say 1% of the file at a time you should see massive performance gains.

---

### Post by schauerlich on 2010-06-01
> **Finalfantasykid said:**
> ```
putc(fgetc(old_file), new_file);
```

I'm not a c expert, but my guess would be this line is your culprit.  Moving 1 character of the file at a time creates a massive number of I/O operations.  If you move say 1% of the file at a time you should see massive performance gains.

Agreed. Every time you read from a disk, you're doing an operation on the order of milliseconds - an eon to your CPU. You should read in chunks of 4KiB, ext3's normal block size.

---

### Post by ziekfiguur on 2010-06-01
> **schauerlich said:**
> You should read in chunks of 4KiB, ext3's normal block size.

Actually i would recommend using stat(2) to get the blocksize, that way you automatically get the most efficient result for any file-system.
you could use something like:
```

unsigned blocksize;
struct stat filestat;
stat(from_path, &filestat);
blocksize = filestat.st_blksize;

```

and you could use stat to see if the file exists and if it is a normal (copyable) file.

---

### Post by MadCow108 on 2010-06-01
file streams are buffered to optimal size already, so the block size is probably not really the problem
(only indirectly over the function call overhead).

The problems are:
- outputting to stdout (slow)
- flushing stdout (makes above slower because you destroy stdout's internal buffering)
- the calculations done for the progress bar
- the high amount of function calls

Luckily the solution is identical to the solution of to small buffer size:
Do it in bigger data chunks instead of once per byte.
Just to be sure also use the st_blksize as recommeded by ziekfiguur

---

### Post by StephenF on 2010-06-01
Use multiples of the block size to reduce the number of seek operations as the hard drive heads need to be repositioned between reads and writes. Each movement costs around 7 to 10ms.

---

### Post by ownaginatious on 2010-06-01
Wow, I never even considered the block size thing. I'll look into that.

Thanks!

EDIT:

Sorry, which function would I use to read blocks rather than characters?

---

### Post by Finalfantasykid on 2010-06-01
I think fgets would be the one you want.

And thanks for the stat() functions.  That might help me for stuff that I might eventually be working on :)

---

### Post by wmcbrine on 2010-06-01
> **Finalfantasykid said:**
> I think fgets would be the one you want.NO.

Use fread() and fwrite().

---

### Post by rnerwein on 2010-06-01
hi
just a hint -- have a look at open/close and readv, writev - read or write data into multiple buffers ( man 2 ... )
ciao

---

### Post by soltanis on 2010-06-01
Don't mix calls of read(2) and write(2) with fread(3) and fwrite(3) (i.e. functions from unistd.h vs. stdio.h). stdio uses different buffering systems and such and you will get strange results.

If you are interested in portability, I would recommend fread/fwrite over read/write, because read/write is implemented only on POSIX conforming systems.

---

### Post by Mordred on 2010-06-02
Hi,

You could also profile your program to see where it spends the most time.
This way you know on what you have to focus to make it faster.

gprof is one tool to do this:

[http://www.cs.utah.edu/dept/old/texinfo/as/gprof_toc.html]("http://www.cs.utah.edu/dept/old/texinfo/as/gprof_toc.html")

Cheers

---

### Post by rnerwein on 2010-06-02
> **soltanis said:**
> Don't mix calls of read(2) and write(2) with fread(3) and fwrite(3) (i.e. functions from unistd.h vs. stdio.h). stdio uses different buffering systems and such and you will get strange results.

If you are interested in portability, I would recommend fread/fwrite over read/write, because read/write is implemented only on POSIX conforming systems.

hi
oh that's pretty brand new for me. start programming C long before posix ( 1978 !! ).
quiz ! on wich systemcalls fread and fwrite are based ?
by the side you can open your files O_SYNC and there is absolutely no buffer.
real programmers don't use functions :-)
ciao

---

