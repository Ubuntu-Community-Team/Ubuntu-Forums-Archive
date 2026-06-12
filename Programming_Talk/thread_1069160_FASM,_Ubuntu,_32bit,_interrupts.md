---
title: "FASM, Ubuntu, 32bit, interrupts"
date: 2009-02-13
forum: Programming Talk
---

### Post by Jack Shankle on 2009-02-13
At the present time I would not be able to write a program to put the letter "A"
on the screen in FASM using Ubuntu. The Fasm board takes off at a dead run using
terms that are not familiar to one used to MASM32. The documentation has been of little
help getting started. For instance I would need an "INT" to write to the screen.
I presume they are totally different from the MASM32 interrupts. Where in the world do I find a list of the interrupts? 
What I need is an example program to write the letter "A" to the screen using FASM with
Ubuntu and for 32 bit. NO DOS, No Windows, NO 16 bit.
Or something I could read that starts from scratch building a very simple program.
Thanks from a floundering MASM32 programmer. 
2% Ubuntu working on 3%

---

### Post by snova on 2009-02-13
I suggest using libc and not the raw kernel API, but here is a table of Linux syscalls:

[http://foosec.pl/pub/info/syscalls_linux_2_2.html](http://foosec.pl/pub/info/syscalls_linux_2_2.html)

---

### Post by Jack Shankle on 2009-02-13
Thank you very much Snova.
That is a very useful site.

2% Ubuntu working on 3%

---

### Post by jimi_hendrix on 2009-02-13
linux syscalls are a LOT easier than DOS ones :)

---

### Post by Jack Shankle on 2009-02-14
I hate to ask this but here goes.
Where/how can I take a look at "LIBC"????

---

### Post by Zugzwang on 2009-02-14
> **Jack Shankle said:**
> I hate to ask this but here goes.
Where/how can I take a look at "LIBC"????

I hate to tell, but here's the answer: ;-)

Use google. Type in "libc". Follow the link to the first result.

---

