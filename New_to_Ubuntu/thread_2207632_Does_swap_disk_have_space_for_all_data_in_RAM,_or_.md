---
title: "Does swap disk have space for all data in RAM, or just the excess?"
date: 2014-02-24
forum: New to Ubuntu
---

### Post by desconocido on 2014-02-24
I'm curious whether modern Unix systems need to have space in the swap partition for all the data used by the currently running programs (like I seem to remember with paging systems on old Virtual Memory systems), or just enough to store the data that there is no more room in RAM for. By data I mean the program code as well.

For example if you are running two large monolithic programs which each need 80% of RAM, when you switch your focus to the other program, does it need to store all its 80% on the swap partition before getting the other 80% back into RAM? Or is the system a bit cleverer and can decant the data in small chunks so that it doesn't need (in this case) 160% of RAM as a swap partition?

---

### Post by grahammechanical on 2014-02-24
It depends upon how you use your machine. Swap space is used when system RAM is full. But if we want to Hibernate (Suspend to Disk) then we will need a swap space large enough to hold all the data in system RAM.

Regards.

---

### Post by The Cog on 2014-02-24
It's clever. It will decant onto disk the bits of RAM that the programs least recently used. And it well retrieve just bits of  memory from disk back into RAM when the program wants to access those areas of RAM again. I don't think memory managers have ever done it by paging entire programs out to disk. At least not by design, although perhaps of necessity when really struggling to cope with multiple RAM hungry apps that use all their memory all the time.

Swap space needs to be larger than physical RAM if you are going to hibernate the machine, of course.

---

### Post by buzzingrobot on 2014-02-24
I seem to recall some pseudo-swapping engines swapped out entire programs back in the heyday of DOS. E.g., third-party TSR gizmos that loaded into extended/enhanced memory and allowed the memory footprint of loaded programs to exceed RAM by writing out to the drive.  Windows 3, which was a DOS extender using so-called extended memory, may have done something similar,  but I'm not certain. Of course, the Unix swap they were imitating had already been around for some years at that point.

---

### Post by SeijiSensei on 2014-02-24
That sounds like [Desqview]("http://en.wikipedia.org/wiki/DESQview"), which was a task switcher that ran on top of DOS.  Modern multi-tasking operating systems like Linux use an entirely different memory model.  They are really not comparable.

---

### Post by buzzingrobot on 2014-02-24
> **SeijiSensei said:**
> That sounds like [Desqview]("http://en.wikipedia.org/wiki/DESQview"), which was a task switcher that ran on top of DOS.  Modern multi-tasking operating systems like Linux use an entirely different memory model.  They are really not comparable.

DesqView, I think, would use "Enhanced Memory" (RAM above the 640k limit organized in sections that could be swapped in and out of the below-640k space) as long as there was enough to spare.  Other DOS TSR utilities were less sophisticated.

As I mentioned, the swap algorithms used in Unix/Linux predate DOS by a several years or more.  Nothing modern there; it's just better.

---

