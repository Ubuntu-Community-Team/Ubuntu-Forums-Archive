---
title: "Matlab Mex - Random Crashes"
date: 2012-12-09
forum: Programming Talk
---

### Post by da_steve123 on 2012-12-09
Hi everybody,

Thought i would post this on here as i just spent a good few days trying to figure this out and there is nothing about this problem.

So ... I am making a user interface to a USB/GPIB connector. This requires some low level device drivers ( in C ) but i wanted a high level gui ( matlab ). I decided to use mex after some searching. The gpib library i was using sends abort calls which was closing matlab. This was quite irritating and undesirable as i did not want the GUI to quit if it was not connected.

I used the signal.h library, using signal(SIGABRT, &error_handler). I got a few segmentation faults (in my code :p ) and decided it would be a good idea to catch these too on error and quit nicely.

BAD IDEA!!!

The symptoms of the problem were successful execution of the program. Mex finished, and about 30secs to a minute later it would crash with segmentation fault.

I thought matlab may not be cleaning up or something. But it turns out ( after a few days of testing ) that it crashed because the signal(SIGSEGV, &error_handler) overwrote the matlab default handler in the JVM. The next segmentation fault in matlab (this happens apparently and is 'normal' ) would call my error_handler function that had already been freed. 

Hence the error message would crash in the matlab with no reference to my function meaning i spent ages trying to find something wrong with my install or compile with mex.

Moral of the story: Careful with SIGSEGV when using it with a JVM

Hope that helps somebody :)

Stephen

---

