---
title: "Linux equivalent to DOS' Debug?"
date: 2010-10-16
forum: Programming Talk
---

### Post by Christmas on 2010-10-16
Hi! I dropped by to ask this: what is the Linux equivalent to the 'Debug' command in DOS, so that I can use commands for some kind of registries, r, mov, xchg etc? (I need it for my classroom as I don't want to install Windows in a virtual machine).

I mention I tried gdb but it doesn't seem to work like that. Reading the man page didn't help me much either.

---

### Post by The Cog on 2010-10-16
Moved to Programming Talk forum. You're more likely to get help there, and won't get buried so quickly.

---

### Post by Christmas on 2010-10-16
OK, hopefully.

---

### Post by The Cog on 2010-10-16
As a thought:

I don't know how to use gdb - the last debugger I used was Borland turbo C. But Borland turbo C is now a free download, I gather, and would probably work in dosbox.

And a quick google found these two references:
[http://www.gnu.org/software/ddd/](http://www.gnu.org/software/ddd/)
[http://libre.adacore.com/libre/tools/gps/](http://libre.adacore.com/libre/tools/gps/)

---

### Post by nvteighen on 2010-10-16
It is gdb. Look at this very good introduction to it (PDF): [http://www.cs.umd.edu/~srhuang/teaching/cmsc212/gdb-tutorial-handout.pdf](http://www.cs.umd.edu/~srhuang/teaching/cmsc212/gdb-tutorial-handout.pdf)

---

### Post by NathanB on 2010-10-16
It is obvious that a Linux debugger would be of no use to you because you'll likely need access to the DOS interrupt routines.

Your best route is to install a Virtual Machine:
[http://www.virtualbox.org/](http://www.virtualbox.org/)

Then load a DOS environment into it:
[http://www.freedos.org/](http://www.freedos.org/)

---

### Post by NathanB on 2010-10-16
P.S. - This will not help you in your class, but if you *do* get the notion to play with a debugger in a Linux environment, check out EDB (Evan's Debugger):

[http://freshmeat.net/projects/edebugger](http://freshmeat.net/projects/edebugger)

Tutes, Refs, Utils, and other resources available at Linux Assembly:

[http://asm.sourceforge.net/](http://asm.sourceforge.net/)

Hope that helps!

Nathan.
[http://clax.inspiretomorrow.net/index.html](http://clax.inspiretomorrow.net/index.html)

---

### Post by Christmas on 2010-10-18
Ok guys, thank you all for your replies. I think I will try the FreeDOS option, it was also suggested to me somewhere else too.

---

