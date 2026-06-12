---
title: "C different malloc behaviour in Linux and Windows"
date: 2009-07-16
forum: Programming Talk
---

### Post by jero3n on 2009-07-16
Hi

I am a software developer coming from Windows world, so I have no much experience in Linux programming.

I am writing some software in C which performs some large matrix calculations and I was testing its behaviour in situations where there is not enough memory. Though I am handling cases where malloc returns NULL, the program terminates with a “Killed” message.

I wrote a small testing program to reproduce this behaviour.
I am using Ubuntu 9.04 with libc 2.9.4 and gcc 4.3.3

This is the testing code

```

#include <stdio.h>
#include <stdlib.h>

int main()
{
    void *d;
    while(1) {
        d = malloc(1000000L);
        if(d==NULL) {
            printf("Out of memory.\n");
            exit(1);
        }
    }
    return 0;
}

```

If I run this program in Windows XP (compiled with mingw 3.4.5), it immediately prints in cmd
```

Out of memory.

```
and exits with no visible change in memory usage in task manager.

Running this code in Linux causes my system to hang for 2 minutes until it eats all swap memory and prints in terminal
```

Killed

```

I was not able to debug it with gdb or valgrind.

Is this an expected behaviour?

---

### Post by fr4nko on 2009-07-16
That's strange. I've tried your code on my laptop with ubuntu 9.04 and I get exactly the same behaviour that you have in Windows. Probably we need the help of a linux guru here :-)

Francesco

---

### Post by Yannick Le Saint kyncani on 2009-07-16
When your system is out of memory, any process may be killed by the "oom killer" [http://linux-mm.org/OOM_Killer](http://linux-mm.org/OOM_Killer)

I'd say your single process eating essentially all the memory makes a sweet target.

---

### Post by fr4nko on 2009-07-16
> **Yannick Le Saint kyncani said:**
> When your system is out of memory, any process may be killed by the "oom killer" [http://linux-mm.org/OOM_Killer](http://linux-mm.org/OOM_Killer)

I'd say your single process eating essentially all the memory makes a sweet target.
But this does not answer to the original question. It is normal the behaviour that jero3n get on linux ?

On my linux system the same program dies very soon and if prints 'Out of memory.', so it is not killed by the oom killer.

Francesco

---

### Post by jero3n on 2009-07-16
I see.. many thanks for your reply.

However I agree with you Francesco. Killing my process is not accepted since I check malloc returns.

It is strange why windows behave so smoothly with the same code and with almost the same compiler. My Linux box needs 3-4 minutes to recover to normal UI responses.

---

### Post by nvteighen on 2009-07-16
> **jero3n said:**
> 
It is strange why windows behave so smoothly with the same code and with almost the same compiler. My Linux box needs 3-4 minutes to recover to normal UI responses.

This may related to this (from malloc's manpage):
> 
Bugs
By default, Linux follows an optimistic memory allocation strategy. This means that when malloc() returns non-NULL there is no guarantee that the memory really is available. This is a really bad bug. In case it turns out that the system is out of memory, one or more processes will be killed by the infamous OOM killer. In case Linux is employed under circumstances where it would be less desirable to suddenly lose some randomly picked processes, and moreover the kernel version is sufficiently recent, one can switch off this overcommitting behavior using a command like

    # echo 2 > /proc/sys/vm/overcommit_memory

See also the kernel Documentation directory, files vm/overcommit-accounting and sysctl/vm.txt.


---

### Post by jero3n on 2009-07-16
ouch :)

So, may I ask, is this a "bad bug", or it leads to faster mallocs?

Thanks

---

### Post by fr4nko on 2009-07-16
> **nvteighen said:**
> This may related to this (from malloc's manpage)
Bugs
By default, Linux follows an optimistic memory allocation strategy. This means that when malloc() returns non-NULL there is no guarantee that the memory really is available. This is a really bad bug. In case it turns out that the system is out of memory, one or more processes will be killed by the infamous OOM killer. In case Linux is employed under circumstances where it would be less desirable to suddenly lose some randomly picked processes, and moreover the kernel version is sufficiently recent, one can switch off this overcommitting behavior using a command like

    # echo 2 > /proc/sys/vm/overcommit_memory

See also the kernel Documentation directory, files vm/overcommit-accounting and sysctl/vm.txt. 			 		

This is interesting. I've made a test on my system. By default it is 0 but I've tried it to set it to 1 or 2 and I always get the same results: the program terminates quickly with an 'Out of memory' message.
May be the kernel config in ubuntu is such that the kernel never overcommit, whatever you may change at runtime.

Francesco

---

### Post by smartbei on 2009-07-16
Kepp in mind your swap space - perhaps you have a lot more swap in linux, and the reason everything is going slow is because your are forcing the operating system to use the swap (which sucks) for everything, including the UI, etc.

---

### Post by lisati on 2009-07-16
> This means that when malloc() returns non-NULL there is no guarantee that the memory really is available.
That is not good, particularly when the only way of returning information to the calling process is the returned (non-NULL) pointer. Nasty! 

Edit: yes I know that some implementations of C have the capability to fill in special variables like ERRNO, but that's beside the point.

---

### Post by jero3n on 2009-07-16
> 
       /proc/sys/vm/overcommit_memory
              This file contains the kernel virtual  memory  accounting  mode.
              Values are:
              0: heuristic overcommit (this is the default)
              1: always overcommit, never check
              2: always check, never overcommit
              In  mode  0,  calls  of  mmap(2)  with MAP_NORESERVE set are not
              checked, and the default check is very weak, leading to the risk
              of getting a process "OOM-killed".  Under Linux 2.4 any non-zero
              value implies mode 1.  In mode 2 (available  since  Linux  2.6),
              the  total virtual address space on the system is limited to (SS
              + RAM*(r/100)), where SS is the size of the swap space, and  RAM
              is the size of the physical memory, and r is the contents of the
              file /proc/sys/vm/overcommit_ratio.



I changed value to 2 without any effect. My overcommit_ratio is 50. This piece of code keeps eating all the memory and gets killed.

Indeed smartbei it eats all the swap memory. According to man page this should not happen.

So this is my final question: 

I develop in Linux because I trust it more for faster and safer calculation expensive code. I know this by its reputation and only. However, killing such a program because it eats memory in this way is not standard-C. In fact it is very ugly. It is also very ugly watching the Windows version works so rapidly and smoothly :) 

Allocating memory is a very fundamental process for an OS.

I could live with that, if I knew this happens for any good reason.

---

### Post by dwhitney67 on 2009-07-16
> **jero3n said:**
> ouch :)

So, may I ask, is this a "bad bug", or it leads to faster mallocs?

Thanks

I modified the program:
```

#include <stdio.h>
#include <stdlib.h>

int main()
{
    void *d;
    while(1) {
        d = malloc(1000000L);
        if(d==NULL) {
            printf("Out of memory.\n");
            exit(1);
        }
        else {
            printf("alloc successful.\n");
        }
    }
    return 0;
}

```

This is the output:
```

...
alloc successful.
alloc successful.
alloc successful.
alloc successful.
alloc successful.
Out of memory.

```

What else would you expect??

When running 'free':
```

free
             total       used       free     shared    buffers     cached
Mem:        509340     488788      20552          0      48928     151536
-/+ buffers/cache:     288324     221016
Swap:      2096440      66828    2029612

```

---

### Post by Yannick Le Saint kyncani on 2009-07-17
Here is what I think happens.

> **jero3n said:**
> Allocating memory is a very fundamental process for an OS.

Yes it is. In fact, it is so fundamuntal that if you run out of memory, these operations which require some memory available will fail :

- Starting any new process, that means you cannot kill any process (kill is a new process), you cannot "ls", "sync", "top", "halt", ...

- Anything kernel-releated that needs to allocate some memory will fail.

It is a very nasty situation where the system would be dead for all purpose (no way to even shut down cleanly) if not for the oom killer, a necessary evil, to make the system somehow able to do something.

So using every bit of available memory will render the whole system unusable. Even if the responsible program checks malloc's return code, it does not matter : something has to be done regarding available memory (hence the infamous but necessary evil oom killer).



So what I think is happening in your particular case, and I may be wrong here or there is :

- Your program allocates small bits of memory at each time.
- This memory is zeroed out, to avoid leaking any information from other previous processes.
- At some point, you've allocated most of the available ram, the kernel will start swapping out pages.
- At some other point, you will eat all available memory (ram+swap). Two things can happen at this point :
(1)- Your program request yet another allocation, this allocation fails, your program notices it, print out of memory and exit().
(2)- Something on the system (another process, the kernel) needs some memory. Linux does not have any unused memory available and starts the oom killer.

Which exact actions trigger the oom killer I do not know (what will trigger (2) before (1) hapens). What I do know is :

- It happens when you've eaten all your memory.
- Your system is unusable at this point.
- As infamous as it may be, the oom killer is necessary at this point.
- The rules used to select a process to kill are complex (see [http://linux-mm.org/OOM_Killer](http://linux-mm.org/OOM_Killer)). Having one arbitrary process killed has always been a controversy. The oom killer has been refined/tweaked by many kernel hackers over the years.
- If you do not have any memory left, something must be done by the kernel (not even shutdown would work at this point, logging in as root would not work either).


So, two questions :

- Why does it happen some other way in windows ?

You must have memory limitations in windows. That's why your process is not allowed any more memory when linux will start to allocate "from swap" and ubuntu does not set memory limits by default I think. Swapping will slow down the entire system and it will take some time but at some point you will eat all available ram+swap.

I do not know all the limits you can set in linux. You may check /proc/$$/limits and "man setrlimit".

- Why do jero3n and fr4nko have different behavior under linux ?

As I said, I do not know which exact action will trigger the oom killer, but jero3n is seeing the case (2) when fr4nko is seeing the case (1). If someone do know which specific points in the kernel trigger the oom killer and all the various limits that one may encounter on the road to consuming all available memory, please tell.

However, when you've run out of memory, something nasty is bound to happen to one process or another.

PS: As for the overcommit bad bug, it does lead to faster mallocs in case the memory is not used. Also, newly allocated zeroed out memory may or may not immediately translate to real ram if you don't write to it depending on your kernel version ( 2.6.20 < X < 2.6.30 ).

PS2: You may check RLIMIT_AS, RLIMIT_DATA which may lead your linux box to behave like your windows box (I don't know what drive window's behavior).

PS3: Sooo, that'd be a somehow long post. I must have made some mistakes ;) but I hope it adds to the discussion :)

---

### Post by The Cog on 2009-07-17
I tried it on my system, I get> ...
alloc successful.
alloc successful.
alloc successful.
alloc successful.
alloc successful.
Out of memory.
Here is my memory status:
 > ~$ free
             total       used       free     shared    buffers     cached
Mem:       3569876    1025080    2544796          0        840     583092
-/+ buffers/cache:     441148    3128728
Swap:      5116660          0    5116660

This on a standard Jaubty i386 desktop.

---

### Post by jero3n on 2009-07-17
Well forgot to mention, my system is Ubuntu 9.04 64bit and my kernel is 2.6.28-14-generic

I think there are two interesting points here.

1. malloc() never returns NULL and
2. malloc() performance

This is my memory status before this runs.

```

             total       used       free     shared    buffers     cached
Mem:       1968280     305356    1662924          0          0      80380
-/+ buffers/cache:     224976    1743304
Swap:      1028120     287128     740992
```

I tried this small modification

```

/* Listing 1 */
#include <stdio.h>
#include <stdlib.h>

int main()
{
    void *d; unsigned long i=0;
    while(1) {
        d = malloc(1000000L);
        if(d==NULL) {
            printf("Out of memory.\n");
            exit(1);
        } else {
            printf("Allocation successful. %ld million bytes.\n", i++);
        }
    }
    return 0;
}
```

The output is

```

Allocation successful. 433183 million bytes.
Allocation successful. 433184 million bytes.
AlloKilled
```

I think I run out of memory because of memory allocator internal memory usage, and not by my allocation.

So, yet another minor modification to overcome with this lazy behaviour.

```

/* Listing 2 */
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main()
{
    void *d; unsigned long i=0;
    while(1) {
        d = malloc(1000000L);
        if(d==NULL) {
            printf("Out of memory.\n");
            exit(1);
        } else {
            memset(d, 0, 1000000L);  /* force system to use allocated memory */
            printf("Allocation successful. %ld million bytes.\n", i++);
        }
    }
    return 0;
}
```

Output:

```

Allocation successful. 2605 million bytes.
Allocation successful. 2606 million bytes.
Killed
```


Conclusion: I cannot somehow force malloc to inform me about memory allocation failure. I have not understand yet if this is kernel issue or it is OOM Killer guy. Is there a way to turn OOM killer off and test it again?

This behaviour is bad in general, because in such a case I want my code to save a valuable snapshot of buffers into disk before it terminates. 

Regarding performace issue, indeed, a numb malloc() is very fast. The only thing it does is to index memory. It does not checks, nor it actually allocates. The true allocation is done when memory is actualy used. In this case
```

/proc/sys/vm/overcommit_memory = 0 
```
might be faster for temp buffers, but it might not be faster for programs that actually use all of allocated memory.

I cannot use
```

/proc/sys/vm/overcommit_memory = 2
```
because it has no effect in my system (bug?)

I tested the same code in a windows XP virtual machine hosted in the same system with 512mb physical and 1.5GB swap memory.
(Less physical but more slow swap, 32bit and slower execution since it is vm)

Listing 1 runs rapidly and prints "Out of memory"

Swap pages are not used, so there is also some lazy mechanism in memory allocator in windows.

Listing 2 takes a bit more time, swap pages are used, malloc also returns NULL and runs faster and smoother than Linux, especially when swapping starts and in the critical time when all memory is exhausted.

It would be interesting if someone tests Linux and Windows version using the same hardware and swap sizes, but despite the Linux OOM Killer and overcommit_memory ideas, it seems to my surprise that Windows kernel allocator behaves better, especially when system is pushed in its limits.

I am not an OS expert, nor I wish to start a windows/linux debate but if i am not understanding the whole thing wrong, there is plenty of room for some improvements in memory allocation in Linux kernel.

---

### Post by Yannick Le Saint kyncani on 2009-07-17
You're running out of memory because of your allocations, not because of some other internal structure. Your output is truncated because it's buffered in user-space for performance reason and you're not using fflush().

Malloc() will inform you of allocation failures returning NULL. However, just before some near-future allocation fails, linux should decide to take action and free some space because there is nothing else to do.

If you want crash-proof software, you should design it so that it saves information when it can or at regular intervals. You certainly cannot rely on malloc() returning NULL when you've consumed all your memory if your process is the culprit (because it's the one which will be aborted).

Overcommit = 0 is an heuristic, if setting it to 2, you observe roughly the same thing, it may mean that the heuristic is close to setting the value to 2, don't worry, it's not a bug :)

I'm no OS expert either, but the people working on linux and gnu libc are. Check [http://lwn.net/Articles/339641/](http://lwn.net/Articles/339641/) -> "Some ado about zero", it's just a well-written example how simple things can affect performance/usage/maintenance/bugs one way or another.

---

### Post by jero3n on 2009-07-17
> You're running out of memory because of your allocations, not because of some other internal structure. Your output is truncated because it's buffered in user-space for performance reason and you're not using fflush().

My observation was the 433184 allocations instead of the normal 2606, not the truncated print :) It seems by memory usage observation like each allocation, adds a few bytes usage instead of abt 1MB.

> Malloc() will inform you of allocation failures returning NULL. However, just before some near-future allocation fails, linux should decide to take action and free some space because there is nothing else to do.

If you want crash-proof software, you should design it so that it saves information when it can or at regular intervals. You certainly cannot rely on malloc() returning NULL when you've consumed all your memory if your process is the culprit (because it's the one which will be aborted).

Overcommit = 0 is an heuristic, if setting it to 2, you observe roughly the same thing, it may mean that the heuristic is close to setting the value to 2, don't worry, it's not a bug 

At least Windows do not kill processes "because there is nothing else to do". I am just comparing Linux to Windows for testing purposes. My point is Windows performing the way every C programmer would expect, reliable and fast. Memory allocation is a critical task, and if there are no other trade-offs for this behaviour I think it is obvious that there is room for improvements. I would like a second opinion. Insisting that this is the only logical behaviour is not useful.

> I'm no OS expert either, but the people working on linux and gnu libc are. Check [http://lwn.net/Articles/339641/](http://lwn.net/Articles/339641/) -> "Some ado about zero", it's just a well-written example how simple things can affect performance/usage/maintenance/bugs one way or another.

Great post -thanks :)

---

### Post by Can+~ on 2009-07-17
> **jero3n said:**
> It is strange why windows behave so smoothly with the same code and with almost the same compiler. My Linux box needs 3-4 minutes to recover to normal UI responses.

It's not an issue about the compiler, is something that the OS (and ultimately the Hardware) has to solve.

I remember seeing a similar post that allocated tiny chunks but forever  (while(1)), linux went unresponsive but finally called the OOMkiller to finish it. Windows entered a infinite SWAP cycle.

*edit: [Found the original thread]("http://ubuntuforums.org/showthread.php?t=910699&highlight=Windows").

> I tested the same code in a windows XP virtual machine hosted in the same system with 512mb physical and 1.5GB swap memory.
(Less physical but more slow swap, 32bit and slower execution since it is vm)

So you are assuming that the virtual machine doesn't have any mechanisms of defending against Out of Memory?

---

### Post by jero3n on 2009-07-17
> So you are assuming that the virtual machine doesn't have any mechanisms of defending against Out of Memory?
Good point. I've tested in a real box, too. It's the same.

---

### Post by fr4nko on 2009-07-18
Just for information, you can use ulimit to limit the resources that a process can have, also in term of memory. To have more information you can type 'man bash' and search for ulimit.
With the -m option you can set the maximum memory size of the program and with -v the maximum virtual memory. Probably it is a good idea to configure your system with a sane limit in the virtual memory usage for all processes.

So, you can perform some tests with ulimit but I don't consider normal the behaviour of your system. In a system configured normally your program should get NULL from malloc when the system is out of memory. This is the way malloc work and this is why all the stupid programs in the earth always check the return value of malloc.

On my system the malloc is returning NULL at some point and the OOM killer doesn't get involved. May be this is because I have 2 Gb of RAM and in a 32bit system you can address at most 4Gb of memory so the swap memory is never used ? Actually I have seen that my system stop to give memory at exactly 3204448256 bytes that is, almost 3Gb.

It would be nice if someone that ***really*** know this subject could explain us why the system of jero3n is not behaving like it should. May be it can be helpful to know if it is a 32bit or 64bit platform and how much memory you have.

Francesco

---

### Post by Reiger on 2009-07-18
A short recollection of some points raised in discussions like these before (and you may want to double check 'em as I don't know nearly enough about memory allocators to be really sure):

First, any Win32 app has by default a built-in limit of 2GB of RAM (which it is allowed to use). There is some kind of flag you can use in the Win32 executable headers to tell the system that "this process can handle more than 2GB RAM". (At least the CFF explorer tool says you can.) Furthermore Windows actively enforces other rules to how many memory any process is allowd, it is also one of the key technical differences between Windows Server and other 32bit Windows OS'es. Basically put, Windows is rather pessimistic, but the Server OS line less so than the others. Of course, that will lead a memory allocation to fail sooner when in reality there is *probably* still quite a bit of memory available. It is also a relatively well-known "trick" to turn the "2GB restriction" off in a binary header, which is almost required if you want to use more than 4GB to any real purpose --even on a 64bit OS since many apps are still of the 32bit type (see the CFF explorer tool for an example). So out-of-memory may mean reached-the-allowed-limit rather than realy-truly-out-of-memory.

Second thing is that by default the Linux memory allocator "over commits", that is it allows you to use memory that doesn't physically exist. Third thing is that malloc doesn't actually return any "chunk of memory" at all. You could say, it merely marks some address in the entire address space as "reserved by process with id ...". The combination means that on a 64bit OS the chances of malloc returning NULL are quite remote, and if it does you are in trouble beyond graceful repair (because you'll really have no memory left anymore).

---

### Post by fr4nko on 2009-07-19
> **Reiger said:**
> 
First, any Win32 app has by default a built-in limit of 2GB of RAM (which it is allowed to use). There is some kind of flag you can use in the Win32 executable headers to tell the system that "this process can handle more than 2GB RAM".
This can explain the behaviour that jero3n observe on Windows and also what I see on my linux, since I have just 2Gb of RAM. So I guess that you can have make your system safer by setting some system wide limits with ulimit.

Thank you for your post.

Francesco

---

### Post by jero3n on 2009-07-19
> So out-of-memory may mean reached-the-allowed-limit rather than realy-truly-out-of-memory.
Very correct thinking. However I tested on a Windows machine with 2GB or less RAM+SWAP memory.

> The combination means that on a 64bit OS the chances of malloc returning NULL are quite remote, and if it does you are in trouble beyond graceful repair
I am curious to test a Win64 server environment, if I had one.

> So I guess that you can have make your system safer by setting some system wide limits with ulimit.
Francesco, my system should be safer without this workarround. The more I look at this, the less I think overcommit is a good idea.

---

