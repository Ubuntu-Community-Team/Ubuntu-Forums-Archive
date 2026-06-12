---
title: "undefined reference error in libGL.so"
date: 2017-03-20
forum: Programming Talk
---

### Post by Patrick_Jeeves on 2017-03-20
I'm getting an undefined reference error in a program I'm making:

undefined reference to `drmGetDevices2' in libGL.so
undefined reference to `drmGetDevice2' in libGL.so

I was able to compile it yesterday, and between those times I used 'apt-get dist upgrade,' Is anyone else experiencing this problem? And is there anything I can do about it, or is there something wrong with the library and I have to wait it out?

---

### Post by olympionex on 2017-05-22
Did you ever have any luck with this?  One one PC in which I have an nvidia card, installing nvidia drivers seemed to fix the problem.  On my other PC without an nvidia card (Intel HD graphics) I've not had any luck getting past this error.  My ubuntu version is 16.04.02

---

