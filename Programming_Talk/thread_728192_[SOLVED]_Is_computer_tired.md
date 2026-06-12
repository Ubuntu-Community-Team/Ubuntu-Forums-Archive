---
title: "[SOLVED] Is computer tired?"
date: 2008-03-18
forum: Programming Talk
---

### Post by fyplinux on 2008-03-18
A problem suddenly appeared with my program.

Ok, I have to fix it. Some hours later, the problem was still. em...then I decided to take a rest, so I logged out the system.

After the rest, when I came back that problem suddenly disappeared. did I have a wrong vision of my program once before? was the computer tired that it cannot run my program smoothly? or did god help me? 

or originally, the computer is unstable? or my program was wrong? but I run the program under the same condition. By the way, It's a C program, compiled by GCC.

---

### Post by tlink on 2008-03-18
God proofs your code while you sleep.  Its a little known fact.

---

### Post by Wybiral on 2008-03-18
Could you post some of this "holy" code?

---

### Post by aks44 on 2008-03-18
If your program is multithreaded, you can rest assured that the bug didn't disappear magically, it's still lying around...


BTW: Gods don't bother with C programs...
[IMG]http://imgs.xkcd.com/comics/lisp.jpg[/IMG]

---

### Post by LaRoza on 2008-03-18
> **aks44 said:**
> 
BTW: Gods don't bother with C programs...


[http://www.gnu.org/fun/jokes/dna.html](http://www.gnu.org/fun/jokes/dna.html)

I have evidence to the contrary.

---

### Post by fyplinux on 2008-03-18
> **Wybiral said:**
> Could you post some of this "holy" code?

the code base are now boo big to be posted, so I cannot show any holy.

Basically, It's a part of network connection via socket, both PF_UNIX and PF_INET are used. 

> **aks44 said:**
> If your program is multithreaded, you can rest assured that the bug didn't disappear magically, it's still lying around...


BTW: Gods don't bother with C programs...
[IMG]http://imgs.xkcd.com/comics/lisp.jpg[/IMG]

It is not multi-threaded.

I am worrying about that it will appear again, So I keep on running the program, god told me, it would never appear again.

---

### Post by LaRoza on 2008-03-18
> **fyplinux said:**
> the code base are now boo big to be posted, so I cannot show any holy.

It's a part of network connection via the local socket.

Could it be a network issue?

---

### Post by fyplinux on 2008-03-18
When I was finding and fixing the bug, the local socket is used Only.

---

### Post by LaRoza on 2008-03-18
> **fyplinux said:**
> 

I am worrying about that it will appear again, So I keep on running the program, god told me, it would never appear again.

I would be most worried if it doesn't appear again. Randomness is evil (although MS gets away with it...)

---

### Post by fyplinux on 2008-03-18
Do you know have any good experience on debugging C? or some good tutorial on debugging?

I began to program in C  about 3 months ago, and I have written more than 10000 lines of code including comments till now.

I debug (from high priority to low priority):
by guessing where the problem could be,
by putting lots of print(),
by using gdb,
by using valgrind, whose output message is too verbose in my opinion.

---

### Post by jespdj on 2008-03-18
> **tlink said:**
> God proofs your code while you sleep.  Its a little known fact.
Really? I thought the little GNOME in my computer fixes all the problems while I'm not looking. :lolflag:

---

### Post by Wybiral on 2008-03-18
> **fyplinux said:**
> I debug (from high priority to low priority):
by guessing where the problem could be,
by putting lots of print(),
by using gdb,
by using valgrind, whose output message is too verbose in my opinion.

valgrind should not be at the bottom of that list. It's one of my favorite tools when debugging C code. If you don't post your program, we can't try to figure it out.

This is why unit testing is so important... Don't wait for those bugs to show up when your program is too big to handle, test every module thoroughly, individually.

---

### Post by ruy_lopez on 2008-03-18
C is mysterious. Sometimes, when testing, you do something screwy with pointers, and weird things happen. I experienced the same the other week, doing sockets programming. A buffer worked when an unrelated, redundant statement was included. It stopped working when I removed the statement. After a reboot, neither worked, because I was doing something screwy. It shouldn't have worked in the first place.

I'm experiencing this quite a lot.

EDIT: Most of these problems disappear when I use malloc, and pass pointers, instead of passing pointers to declared storage.

---

