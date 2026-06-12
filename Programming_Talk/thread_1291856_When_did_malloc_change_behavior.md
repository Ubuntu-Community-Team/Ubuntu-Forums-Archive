---
title: "When did malloc change behavior?"
date: 2009-10-15
forum: Programming Talk
---

### Post by janerikdahlin on 2009-10-15
I used to be able load a C/C++ program in gdb, run it until it crashed, examine the variables, set a conditional break point, rerun the program, and it would stop before the crash. I used to be able to do this on pointer variables, e.g. on the this pointer, but that no longer works. When I run the program the second time malloc/new returns another address!

When did this change?

Can I turn this off? I prefer to have predictable behavior when I debug my program.

---

### Post by HNS-I on 2009-10-15
Did you compile with the -g argument?

---

### Post by dwhitney67 on 2009-10-15
> **janerikdahlin said:**
> I used to be able load a C/C++ program in gdb, run it until it crashed, examine the variables, set a conditional break point, rerun the program, and it would stop before the crash. I used to be able to do this on pointer variables, e.g. on the this pointer, but that no longer works. When I run the program the second time malloc/new returns another address!

When did this change?

Can I turn this off? I prefer to have predictable behavior when I debug my program.

If I understand you correctly, you ran gdb more than once, and for each occurrence, you expected malloc/new to return the same address for allocated memory.  Good luck with that assumption.

Now, there is nothing to prevent you from setting a breakpoint at the point where the malloc/new take place.

---

### Post by Zugzwang on 2009-10-15
@OP: For tracing crashes, you probably want to consider using the "valgrind" tool. It finds some causes of these and probably you don't need to do what you are trying to do then anymore.

---

### Post by Arndt on 2009-10-15
> **dwhitney67 said:**
> If I understand you correctly, you ran gdb more than once, and for each occurrence, you expected malloc/new to return the same address for allocated memory.  Good luck with that assumption.

Now, there is nothing to prevent you from setting a breakpoint at the point where the malloc/new take place.

No one will guarantee that memory addresses stay the same from one run to the next, but all the same, unless some code is doing things randomly just for the heck of it (or better, for testing purposes), I would also assume that two runs with identical input and no random aspects use the same memory addresses.

---

### Post by janerikdahlin on 2009-10-15
The -g switch doesn't seem to have any effect on malloc's return values.

dalle@dalburk:~$ cat malloctest.c
#include <stdlib.h>
#include <stdio.h>
int main()
{
  void *p1 = malloc(100);
  printf("%p\n", p1);
}
dalle@dalburk:~$ gcc malloctest.c
dalle@dalburk:~$ ./a.out 
0x8a52008
dalle@dalburk:~$ ./a.out 
0x9f54008
dalle@dalburk:~$ ./a.out 
0x8793008
dalle@dalburk:~$ ./a.out 
0x8ec4008
dalle@dalburk:~$ gcc -g malloctest.c
dalle@dalburk:~$ ./a.out 
0x9c4a008
dalle@dalburk:~$ ./a.out 
0x8b0e008
dalle@dalburk:~$ ./a.out 
0x92d0008
dalle@dalburk:~$ ./a.out 
0x86a2008
dalle@dalburk:~$ ./a.out 
0x9c84008
dalle@dalburk:~$ 

If I log in on our trusty old (== haven't been updated for quite some time) suse machine and run the same program I get:

dalle@suse1:~> ./a.out 
0x804a008
dalle@suse1:~> ./a.out 
0x804a008
dalle@suse1:~> ./a.out 
0x804a008
dalle@suse1:~> ./a.out 
0x804a008

Malloc used to behave that same way in Ubuntu too. I have been using this technique for years, but it no longer works. I assume the malloc implementation changed since one could hardly change the underlying sbrk without breaking a lot code.

---

### Post by fct on 2009-10-15
Yep, you can't rely on malloc returning the same address across different executions for debugging, regardless of it happening to work in particular malloc implementations.

Read any man page for malloc and that isn't guaranteed, not even mentioned, for any implementation.

---

### Post by janerikdahlin on 2009-10-15
> **dwhitney67 said:**
> If I understand you correctly, you ran gdb more than once, and for each occurrence, you expected malloc/new to return the same address for allocated memory.  Good luck with that assumption.


What is wrong with that assumption? You load the same program with the same arguments and environment into memory. It will be (or it was until recently) loaded at the same address so malloc will start with the same heap and see the same allocation sequence. So unless I have any random behavior in my program or someone else introduces a random element I'd expect two consecutive runs in exactly the same way. They used to behave the same way and now they don't and I wonder if I can get the old behavior back.

---

### Post by HNS-I on 2009-10-15
The point is that you cannot rely on that behaviour. Why argue this with people? This is the fact as it is. Maybe you want to do something in a way you shouldn't (happens a lot). Sorry if this comes across as blunt.

---

### Post by Zugzwang on 2009-10-15
> **janerikdahlin said:**
> What is wrong with that assumption? You load the same program with the same arguments and environment into memory. It will be (or it was until recently) loaded at the same address so malloc will start with the same heap and see the same allocation sequence. So unless I have any random behavior in my program or someone else introduces a random element I'd expect two consecutive runs in exactly the same way. They used to behave the same way and now they don't and I wonder if I can get the old behavior back.

Note that there are a lot of programs running on your machine. Consider for example the keyboard driver. Whenever you press a key, it does something and it might allocate memory (I don't know if it does). That means that after you've pressed a key, the state of your system has changed, i.e., the memory addressed for newly allocated memory might have changed. There are also tasks such as the X-server for which its memory consumption can also depend on the position of the windows. There's also a timer tick that is periodically called. As a final example, there's a writing buffer for the hard disk in the kernel. Depending on how much writes have been done in the past and where these write operations were supposed to go, the amount of memory allocated to the kernel might be different.

Now, this was only theory (ignoring the difference between physical and virtual memory - but the concept should be clear by now: Your system is probably never in the same state two times). What is also important is that the libraries your program links to (in particular, libc) have similar stuff in it and might or might not perform different operations on the start-up of the program, such that the position of allocated memory blocks might always be different. 

Computer scientists call such "stuff" non-determinism.

Oh, any by the way: I've noticed that when debugging, addresses are more likely to be the same:
```

user@user-laptop:/tmp$ ./a.out                                                             
0x9e18008                                                                                      
user@user-laptop:/tmp$ ./a.out                                                             
0x8b8d008                                                                                      
user@user-laptop:/tmp$ ./a.out                                                             
0x986d008                                                                                      
user@user-laptop:/tmp$ ./a.out                                                             
0x9412008                                                                                      
user@user-laptop:/tmp$ valgrind --tool=memcheck ./a.out                                                             
==6248== Memcheck, a memory error detector.                                                                             
==6248== Copyright (C) 2002-2008, and GNU GPL'd, by Julian Seward et al.                                                
==6248== Using LibVEX rev 1884, a library for dynamic binary translation.                                               
==6248== Copyright (C) 2004-2008, and GNU GPL'd, by OpenWorks LLP.                                                      
==6248== Using valgrind-3.4.1-Debian, a dynamic binary instrumentation framework.                                       
==6248== Copyright (C) 2000-2008, and GNU GPL'd, by Julian Seward et al.                                                
==6248== For more details, rerun with: -v
==6248==
0x42d4028
==6248==
==6248== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 17 from 1)
==6248== malloc/free: in use at exit: 100 bytes in 1 blocks.
==6248== malloc/free: 1 allocs, 0 frees, 100 bytes allocated.
==6248== For counts of detected errors, rerun with: -v
==6248== searching for pointers to 1 not-freed blocks.
==6248== checked 93,340 bytes.
==6248==
==6248== LEAK SUMMARY:
==6248==    definitely lost: 100 bytes in 1 blocks.
==6248==      possibly lost: 0 bytes in 0 blocks.
==6248==    still reachable: 0 bytes in 0 blocks.
==6248==         suppressed: 0 bytes in 0 blocks.
==6248== Rerun with --leak-check=full to see details of leaked memory.
user@user-laptop:/tmp$ valgrind --tool=memcheck ./a.out
==6252== Memcheck, a memory error detector.
==6252== Copyright (C) 2002-2008, and GNU GPL'd, by Julian Seward et al.
==6252== Using LibVEX rev 1884, a library for dynamic binary translation.
==6252== Copyright (C) 2004-2008, and GNU GPL'd, by OpenWorks LLP.
==6252== Using valgrind-3.4.1-Debian, a dynamic binary instrumentation framework.
==6252== Copyright (C) 2000-2008, and GNU GPL'd, by Julian Seward et al.
==6252== For more details, rerun with: -v
==6252==
0x42d4028
==6252==
==6252== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 17 from 1)
==6252== malloc/free: in use at exit: 100 bytes in 1 blocks.
==6252== malloc/free: 1 allocs, 0 frees, 100 bytes allocated.
==6252== For counts of detected errors, rerun with: -v
==6252== searching for pointers to 1 not-freed blocks.
==6252== checked 93,340 bytes.
==6252==
==6252== LEAK SUMMARY:
==6252==    definitely lost: 100 bytes in 1 blocks.
==6252==      possibly lost: 0 bytes in 0 blocks.
==6252==    still reachable: 0 bytes in 0 blocks.
==6252==         suppressed: 0 bytes in 0 blocks.
==6252== Rerun with --leak-check=full to see details of leaked memory.
user@user-laptop:/tmp$ valgrind --tool=memcheck ./a.out
==6255== Memcheck, a memory error detector.
==6255== Copyright (C) 2002-2008, and GNU GPL'd, by Julian Seward et al.
==6255== Using LibVEX rev 1884, a library for dynamic binary translation.
==6255== Copyright (C) 2004-2008, and GNU GPL'd, by OpenWorks LLP.
==6255== Using valgrind-3.4.1-Debian, a dynamic binary instrumentation framework.
==6255== Copyright (C) 2000-2008, and GNU GPL'd, by Julian Seward et al.
==6255== For more details, rerun with: -v
==6255==
0x42d4028
==6255==
==6255== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 17 from 1)
==6255== malloc/free: in use at exit: 100 bytes in 1 blocks.
==6255== malloc/free: 1 allocs, 0 frees, 100 bytes allocated.
==6255== For counts of detected errors, rerun with: -v
==6255== searching for pointers to 1 not-freed blocks.
==6255== checked 93,340 bytes.
==6255==
==6255== LEAK SUMMARY:
==6255==    definitely lost: 100 bytes in 1 blocks.
==6255==      possibly lost: 0 bytes in 0 blocks.
==6255==    still reachable: 0 bytes in 0 blocks.
==6255==         suppressed: 0 bytes in 0 blocks.
==6255== Rerun with --leak-check=full to see details of leaked memory.

```

---

### Post by fct on 2009-10-15
> **janerikdahlin said:**
> What is wrong with that assumption? You load the same program with the same arguments and environment into memory. It will be (or it was until recently) loaded at the same address so malloc will start with the same heap and see the same allocation sequence. So unless I have any random behavior in my program or someone else introduces a random element I'd expect two consecutive runs in exactly the same way. They used to behave the same way and now they don't and I wonder if I can get the old behavior back.

If you look at your example, the address always ends in 008 but the base address changes. That probably means that the kernel's behaviour has changed and now it loaded the program in a different base address on each execution.

So I don't think you can have the behaviour back unless you compile that kernel version on your system and cross your fingers so that's what changed (that supposing the kernel versions are different).

Instead I'd avoid using memory addresses returned by functions to manage **dynamic** memory as inmutable vars.

There are much better reliable methods to debug memory in GDB:

[http://www.unknownroad.com/rtfm/gdbtut/gdbsegfault.html](http://www.unknownroad.com/rtfm/gdbtut/gdbsegfault.html)

---

### Post by matthew.ball on 2009-10-15
Wouldn't it actually be *really* dangerous to load a program into the same place in memory each time?

I mean, if I knew program x was going to load variable y into 0x00 I could just re-write 0x00...

---

### Post by Arndt on 2009-10-15
> **HNS-I said:**
> The point is that you cannot rely on that behaviour. Why argue this with people? This is the fact as it is. Maybe you want to do something in a way you shouldn't (happens a lot). Sorry if this comes across as blunt.

Be as blunt as you like, but it's because the question itself is interesting. If you took everything "as it is", nothing new would ever be produced. It's those who take an interest in why things don't work the way they expected who create new things.

---

### Post by Arndt on 2009-10-15
> **matthew.ball said:**
> Wouldn't it actually be *really* dangerous to load a program into the same place in memory each time?

I mean, if I knew program x was going to load variable y into 0x00 I could just re-write 0x00...

That's why we have variable names, and call the memory position "y" instead.

---

### Post by matthew.ball on 2009-10-15
I'm talking about externally accessing RAM (i.e. external from the program).

---

### Post by fct on 2009-10-15
> **matthew.ball said:**
> Wouldn't it actually be *really* dangerous to load a program into the same place in memory each time?

I mean, if I knew program x was going to load variable y into 0x00 I could just re-write 0x00...

Now that you mention it, I remember this protection being included in the kernel:

[https://wiki.ubuntu.com/Security/Features#ASLR](https://wiki.ubuntu.com/Security/Features#ASLR)

---

### Post by Arndt on 2009-10-15
> **matthew.ball said:**
> I'm talking about externally accessing RAM (i.e. external from the program).

I'm not sure what you mean. Usually only the program itself has access to its memory space (and the kernel, of course). There is plenty of hardware where you do want to access explicitly given addresses, but aren't we talking about user processes in Linux?

---

### Post by matthew.ball on 2009-10-15
I heard Apple had something that loaded dynamic libraries to *random* places in memory, this is why I asked. (This may, or may not be related to Grand Central Dispatch).

Edit: Exactly as fct posted.

---

### Post by Arndt on 2009-10-15
> **fct said:**
> Now that you mention it, I remember this protection being included in the kernel:

[https://wiki.ubuntu.com/Security/Features#ASLR](https://wiki.ubuntu.com/Security/Features#ASLR)

Wonderful, an actual answer to the question. Thank you.

And I found a thread which also mentions how to turn it off:

[http://ubuntuforums.org/showthread.php?t=976656](http://ubuntuforums.org/showthread.php?t=976656)

---

### Post by HNS-I on 2009-10-15
> **Arndt said:**
> Be as blunt as you like, but it's because the question itself is interesting. If you took everything "as it is", nothing new would ever be produced. It's those who take an interest in why things don't work the way they expected who create new things.

In all honesty I do not know much about it but I guess I could say something. This behaviour depends on the implementation of virtual memory in the os, it could be that some os supplies virtual memory with the same memory offset each time you run a certain process, this is possible because it is virtual but it is not something you can depend on and it is definitely not in the c standard. Also I don't see how this is important in your program logic, you should take this as it is when you are trying to write a program. I mean if you are going to question this, you could also question how the switch case mechanism is implemented in c or that it should use a call by reference mechanism. All interesting matters or course.

---

### Post by janerikdahlin on 2009-10-15
I found that as well. Thanks a lot, Fct.

In case you're interested:

echo 0 > /proc/sys/kernel/randomize_va_space

will turn off the brk ASLR.

---

### Post by fct on 2009-10-15
> **janerikdahlin said:**
> I found that as well. Thanks a lot, Fct.

You're welcome, but find a way not to rely on that EVER. ;)

---

### Post by janerikdahlin on 2009-10-15
> **fct said:**
> You're welcome, but find a way not to rely on that EVER. ;)

Well, I write compilers for a living and when you have a bug when transforming a particular expression tree in a 100k program, it is really useful to be able go up in the call stack, set a breakpoint in the caller and make it conditional on an object address, rerun the program, and single step through the program to see what happens just before things go wrong. 

The compiler works fine with ASLR enabled, but when the compiler doesn't work it is often easier to find out why if one run behaves exactly as the previous one.

---

### Post by matthew.ball on 2009-10-15
Just stumbled upon this, somewhat related article.
[http://insecure.org/stf/smashstack.html](http://insecure.org/stf/smashstack.html)

---

### Post by fct on 2009-10-15
> **janerikdahlin said:**
> Well, I write compilers for a living and when you have a bug when transforming a particular expression tree in a 100k program, it is really useful to be able go up in the call stack, set a breakpoint in the caller and make it conditional on an object address, rerun the program, and single step through the program to see what happens just before things go wrong. 

The compiler works fine with ASLR enabled, but when the compiler doesn't work it is often easier to find out why if one run behaves exactly as the previous one.

Have you looked at the new features in GDB 7.0? Reversible debugging and python scripting ( [http://tromey.com/blog/?p=412](http://tromey.com/blog/?p=412) ). \\:D/

---

### Post by janerikdahlin on 2009-10-15
I'm not sure if embedded python will help me, but reversible debugging definitely will. :) I've been dreaming about that...

---

### Post by janerikdahlin on 2009-10-15
After playing around with gdb 7.0 I don't think I'll find reversible debugging as useful as I thought it would be. One has to enable the instruction recorder to be able to reverse the execution and the recorder is orders of magnitude slower than native execution. I might still have to use my breakpoint trick to get to a point in the execution where I can turn on the recorder :(

---

