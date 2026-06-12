---
title: "Unusual problem, hopeful fix."
date: 2008-06-03
forum: New to Ubuntu
---

### Post by wilberforce74 on 2008-06-03
I have a Toshiba A75 s-2112 notebook computer that would not boot Windows.  I tried to boot the "Try It" Ubuntu disk as well, but ended up with a memory dump after about 2 minutes.  I have since checked the machine's memory only to find that there are bad addresses on it.  Through research, I have found out that the onboard memory for this machine is not a module, but is soldered directly to the motherboard.  This, of course, means that the motherboard would have to be replaced to fix the problem.  Talking to a computer technician, though, I found out that there is something called "BadMem" that, if embedded in the Linux kernel, will mark bad addresses and allow the good part of the memory to be used.  What a great feature.  Problem is, I have no experience with how to incorporate BadMem with the kernel so that I can install Ubuntu on my machine.  Anyone have suggestions where I might turn for instruction?:confused:

---

### Post by Mark_in_Hollywood on 2008-06-03
This one is for LINUX

[http://badmem.sourceforge.net/docu/BadMEM-HOWTO.html](http://badmem.sourceforge.net/docu/BadMEM-HOWTO.html)

this one for Microsot Windows 98/dos:

[https://sourceforge.net/projects/badxms](https://sourceforge.net/projects/badxms)

---

### Post by groggyboy on 2008-06-03
i found [this page]("https://help.ubuntu.com/community/BadRAM") on the community ubuntu documentation website.  it gives some instructions on compiling an ubuntu kernel with badRAM built in.

the instructions are fairly in depth, so i won't repeat them here. 

although i must admit, i don't envy you: compiling a kernel isn't exactly a walk in the park.  it's not rocket science, but it's not basic computing either.  quite the intro to linux!

---

### Post by Shazaam on 2008-06-03
nm bad user memory sorry.

---

### Post by wilberforce74 on 2008-06-05
Thanks all for the replies.  I shall try what I can from the websites you have provided.  Hope they work!  Thanks again.[-o<

---

