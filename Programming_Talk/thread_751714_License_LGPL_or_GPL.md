---
title: "License: LGPL or GPL?"
date: 2008-04-10
forum: Programming Talk
---

### Post by reacocard on 2008-04-10
I'm writing a new python downloading library, and I'm not sure which license to choose. Should I go with LGPL, or GPL? I'll be using version 2 (with the or later clause) of the license in either case (unless there's a good reason why I shouldn't).

---

### Post by samjh on 2008-04-10
Before choosing a license, what restrictions or allowances do you want for your project?  What do you want to grant others to do with your project - for personal use, for commercial gain, etc.

The key difference between GPL and LGPL, is that GPL imposes itself on any software that links to it, while LGPL does not.  So that means if someone uses your downloading library to create a program, and your library is licensed under GPL, that person's program will be bound by GPL.  But if your library is LGPL, then he/she is free to choose whatever license they want for their program.

---

### Post by pmasiar on 2008-04-10
... and why not new L/GPLv3, instead of obsolete v2?

---

### Post by reacocard on 2008-04-10
> **samjh said:**
> Before choosing a license, what restrictions or allowances do you want for your project?  What do you want to grant others to do with your project - for personal use, for commercial gain, etc.

The key difference between GPL and LGPL, is that GPL imposes itself on any software that links to it, while LGPL does not.  So that means if someone uses your downloading library to create a program, and your library is licensed under GPL, that person's program will be bound by GPL.  But if your library is LGPL, then he/she is free to choose whatever license they want for their program.

I understand the differences between the licenses, and I've heard arguments in favor of each. I just wanted to hear more people's opinions before I made a choice. I really don't mind having others use my library, but it's primarily for use in the download manager I'm writing which will be GPL.

---

### Post by reacocard on 2008-04-10
> **pmasiar said:**
> ... and why not new L/GPLv3, instead of obsolete v2?

turn that question around, why should I use v3 over v2, aside from the fact that it's newer? If I use v2, that means both those who write v2 and v3 programs can benefit from it, wheras with v2, using the and any later version clause, both users of v2 and v3 can use it.

---

### Post by t3hi3x on 2008-04-10
> **reacocard said:**
> turn that question around, why should I use v3 over v2, aside from the fact that it's newer? If I use v2, that means both those who write v2 and v3 programs can benefit from it, wheras with v2, using the and any later version clause, both users of v2 and v3 can use it.

There are some protections in v3 that you do not have in v2. Mainly due to embedded devices.

And if they licensee has the choice, he can choose to use the slightly less restricted one.

---

### Post by nanotube on 2008-04-11
in brief: gplv3 gives you more protection than gplv2, which in turn gives you more than lgpl v2. 

wherein "protection" is with respect to other people being able to use your code in non-open-source-friendly ways.

so, depending on your goals and your personal philosophy wrt free software, choose one that makes you happier. 

fwiw, i personally choose the gplv3 for my software projects, because i think [in brief] that the tit-for-tat strategy has to have some bite in order to work. :)

more detailed-ly, see this article from gnu about "why you shouldn't use lgpl": [http://www.gnu.org/licenses/why-not-lgpl.html](http://www.gnu.org/licenses/why-not-lgpl.html)

and this article from gnu about "why you should upgrade to gplv3": [http://www.gnu.org/licenses/rms-why-gplv3.html](http://www.gnu.org/licenses/rms-why-gplv3.html)

---

### Post by samjh on 2008-04-11
> **reacocard said:**
> I understand the differences between the licenses, and I've heard arguments in favor of each. I just wanted to hear more people's opinions before I made a choice. I really don't mind having others use my library, but it's primarily for use in the download manager I'm writing which will be GPL.

If you don't mind other people making closed-source software using your library, use LGPL.

If you want users to produce only GPL'ed software, choose GPL.

Personally, I choose LGPL for libraries and GPL for applications.

---

### Post by pmasiar on 2008-04-11
@ OP: If you don't know difference between v2 and v3, you did not researched licenses deep enough.

samjh is right. LGPLv3 seems best for your library.

---

