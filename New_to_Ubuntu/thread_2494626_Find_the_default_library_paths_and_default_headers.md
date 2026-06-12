---
title: "Find the default library paths and default headers include paths"
date: 2024-01-22
forum: New to Ubuntu
---

### Post by luca-ub-1993 on 2024-01-22
I'm on an Ubuntu 22.04 system and I'm working with C language and libraries.

I know ( from different books, included "The Linux Programming Interface" by Kerrisk )  that this algorithm is used when looking for runtime shared libraries locations ( I just omitted the preloaded libraries for the sake of simplicity ) :

When RUNPATH field is specified (i.e. DT_RUNPATH is non-empty) 
 
  1 ) LD_LIBRARY_PATH 
  2 ) runpath (DT_RUNPATH field) 
  3 ) ld.so.cache
  4 ) default library paths (/lib and /usr/lib) 

In the absence of RUNPATH (i.e. DT_RUNPATH is empty string) 

  1 ) RPATH 
  2 ) LD_LIBRARY_PATH 
  3 ) ld.so.cache
  4 ) default library paths (/lib and /usr/lib)

The problem is that most books say that generally speaking the default library paths are /lib and /usr/lib but they don't mention **HOW I CAN GET THE EXACT DEFAULT LIBRARY PATHS FOR MY SYSTEM**. What command can I use on my Ubuntu 22.04 system ?

[B]What about the default headers include paths ? What command can I use the get them ?

And finally what is the specific algorithm used in my ubuntu system when dealing with "headers.h" vs  <headers.h> ?[/B]

---

### Post by coffeecat on 2024-01-22
Another duplicate. @luca-ub-1993, please do not post duplicates in different parts of the forum - you posted three identical posts altogether. This is not good netiquette, it dilutes community effort and causes confusion.

Thread closed. The still open thread is here: [https://ubuntuforums.org/showthread.php?t=2494627](https://ubuntuforums.org/showthread.php?t=2494627)

---

