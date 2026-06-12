---
title: "Undeletion Security Program?"
date: 2008-09-04
forum: Programming Talk
---

### Post by lordhaworth on 2008-09-04
I know its possible for data to be retrieved from the hard disk drive, but out of curiosity I was looking into how this is possible. I mean if i fill my computer up with files, and then delete them - space is freed, so how does the information remain? Furthermore, if data could be stored in such a small manner - why not do it?


Ok well I read something which tells me that the deleted file is stored in memory as a directory or something like that and that if this memory location is overwritten the data is permanently lost.

So couldnt this security risk to sensitive data be overcome by writing a program that allocates and then releases all memory on the hard disk drive?
Or have I just described formatting the hard drive (something I know little about in theory)?

---

### Post by slavik on 2008-09-04
most important is that this depends on the OS and the filesystem. OpenBSD will overwrite the actual file with random data or whatever the gov't standard is for secure erasure of files.

On regular linux filesystem (ext3), when you remove a file, you unlink it, reducing the file's inode reference count by 1, once that count reaches 0, the inode is marked asfree and can be reused. the actual file data is never overwritten unless some other file is put there.

when you create a new file, even if you reuse a previously used inode, that does not mean that the inode will point to the same disk location.

---

### Post by lordhaworth on 2008-09-04
After reading a bit more I think what I was getting at is the overwriting part of:

[http://en.wikipedia.org/wiki/Data_remanence](http://en.wikipedia.org/wiki/Data_remanence)


> 
the actual file data is never overwritten unless some other file is put there.

when you create a new file, even if you reuse a previously used inode, that does not mean that the inode will point to the same disk location. 


Perhaps a file generator to swamp the entire hard drive?

As you can probably tell, I'm new to thinking and talking in terms of hardware! But learning ...

---

### Post by slavik on 2008-09-04
not really practical ... especially for big disks.

---

### Post by ajgreeny on 2008-09-04
There is shred which is in most if not all linux distros by default.  Have a look at ```
man shred
``` and you will see what can be done if you are really paranoid.

---

### Post by lordhaworth on 2008-09-04
> 
and you will see what can be done if you are really paranoid. 


cheers for the feedback - I'm not paranoid about my comp just starting to take more of an interest in hardware - a step which I think most programmers will end up taking to expand their understanding.

---

### Post by Vox754 on 2008-09-04
> **lordhaworth said:**
> cheers for the feedback - I'm not paranoid about my comp just starting to take more of an interest in hardware - **a step which I think most programmers will end up taking to expand their understanding.**

Wow!

This is the exact opposite of what some "programmers" think.
Some of them will tell you that hardware is not that important, what really matters is the higher abstraction layers the computer provides.
Namely, that you must concentrate on studying algorithms; that is, you can solve any programming problem with algorithms rather than with more "powerful" hardware.

---

### Post by lordhaworth on 2008-09-05
> 
Wow!

This is the exact opposite of what some "programmers" think.
Some of them will tell you that hardware is not that important, what really matters is the higher abstraction layers the computer provides.
Namely, that you must concentrate on studying algorithms; that is, you can solve any programming problem with algorithms rather than with more "powerful" hardware. 


Im only now delving into modern programming languages - most of my experience has been with C and now Fortran 90. So in relation to those languages it is quite interesting to see how hardware fits in a bit. From what I think I know (which isnt very much - hence the "Im learning" bit) a lot of modern languages are based on things like C anyway (i.e. python) and the point Ive seen made a few times is that people should start with something like python then go and learn C, so Im only really doing that by taking an interest in hardware - I dont intend to really use anything I pick up but it helps my understanding.

You are correct though - well written code does make a massive difference, however it wont do if your computer is broken

---

