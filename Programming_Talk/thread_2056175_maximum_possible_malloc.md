---
title: "maximum possible malloc"
date: 2012-09-10
forum: Programming Talk
---

### Post by IAMTubby on 2012-09-10
Hi,
I have a question which has probable been asked a few times previously on the internet, but I couldn't get a final answer anywhere.

My question is, If I run malloc inside an infinite while loop, when will it crash ?
```

#include <stdio.h>
#include <malloc.h>

int iteration = 0;
char* p;

int main(void)
{
 while(1)
 {
  p = malloc(1024 * 1024 * 1024 * sizeof(char));
  if(p == NULL)
  {
   printf("\nmalloc failed .. Total memory allocated = %dGB",iteration);
   break;
  }

  iteration++;
  printf("\nSize so far = %dGB, p = %x",iteration,p);
 }

 return 0;
}

```

```

I executed the above code on 2 machines and the output is highly misleading

Machine1 : 3GB RAM, 320GB HDD
.
.
.
Size so far = 131070GB, p = 985a2010
malloc failed .. Total memory allocated = 131070GB

Machine2 : Higher RAM, Higher HDD - not sure exactly how much, as this is a server and there are multiple users on it.
Size so far = 1GB, p = 77f99008
Size so far = 2GB, p = 37f98008
malloc failed .. Total memory allocated = 2GB

```

Possible Answers
1)I heard this answer on one of the forums.> This code quickly filled my RAM (4Gb) and then in about 2 minutes my 20Gb swap partition before it died. 64bit Linux of course

2)This is another answer I heard from one of my teachers.
The maximum space allotted to user-mode processes in Linux is 3GB(2GB on Windows). So every user-mode process/application running over the kernel can take upto 3GB.

But both the outputs are not in accordance with my understanding so far which I have mentioned above in "Possible Answers".

Thanks.

---

### Post by dwhitney67 on 2012-09-11
C programs don't just run under Windows and Linux.  There are other systems out there too, some of which would allow you to directly access RAM.

I can't speak for Windows (don't know much about, nor do I care to), but as for Linux, it maps virtual memory over the physical memory.  Linux also can take advantage of utilizing the system's swap space to store memory that is currently not being accessed.

Typically under Linux, when a program takes up a substantial amount of memory, the Kernel will either kill this process or possibly some other (random?) process in an effort to stave off a system halt/crash.  This Kernel feature is better known as the OOM (Out Of Memory) killer.

You can use the internet to research the topic of Out of Memory a little further:  [http://en.wikipedia.org/wiki/Out_of_memory](http://en.wikipedia.org/wiki/Out_of_memory)

---

### Post by einonm on 2012-09-11
The Linux kernel uses a technique called overcommit when allocating memory - so it will tell you that you've allocated more memory than is possible. But once it actually runs out of real system memory, the out of memory killer will start killing the most greedy processes first in an attempt to free up memory. In your case, this will probably be your program.

This may be helpful - [http://opsmonkey.blogspot.com/2007/01/linux-memory-overcommit.html](http://opsmonkey.blogspot.com/2007/01/linux-memory-overcommit.html)

also check out your system's /proc/sys/vm/ directory for info and switches relating to virtual memory, oom killer and overcommitting.

So to answer your question - your program will be able to allocate much more memory than you would expect it to before crashing.

---

### Post by MadCow108 on 2012-09-11
> **IAMTubby said:**
> Hi,

2)This is another answer I heard from one of my teachers.
The maximum space allotted to user-mode processes in Linux is 3GB(2GB on Windows). So every user-mode process/application running over the kernel can take upto 3GB.


this is only true for 32 bit operating systems
64 bit operating systems can allocate much much more (48 bit I think)
and you can allocate more than you have on linux due the already mentioned overcommit.

if you run this code on a 32 bit OS it will stop after 3GB, not because its out of memory, but because its out of address space.

---

