---
title: "/dev/sda1: clean, ***/*** files, ***/*** blocks"
date: 2016-05-21
forum: New to Ubuntu
---

### Post by nabin3 on 2016-05-21
/dev/sda1: clean, 227147/30269440 files, 3330843/121068288 blocks

is displaying after upgrading ubuntu 16.04

---

### Post by mörgæs on 2016-05-21
Hi, welcome to the fora.

I guess that you have Intel graphics. 

There are several solutions to the problem. One of them is to open the Old Hardware link in my signature and look for the text in red.

---

### Post by nabin3 on 2016-05-21
Thank you, but I have nvidia GeForce 820m with 2 gb dedicated vram.

---

### Post by mörgæs on 2016-05-21
I have to admit that it's the first time I see this error on non-Intel hardware. 
Still I think the workaround is worth trying.

---

### Post by grahammechanical on 2016-05-21
> **nabin3 said:**
> /dev/sda1: clean, 227147/30269440 files, 3330843/121068288 blocks

is displaying after upgrading ubuntu 16.04

And that is a problem? No. It is s system message reporting the result of a file system check (fsck). I see it as well. In fact I saw that all through the 26 week development period of 16.04. It will still be there when 16.10 is release. As part of the Linux loading process the file system (partition) is checked for errors.

For some reason when we use the Nvidia driver the Ubuntu purple splash screen is suppressed. Even when using the open source video driver, Nouveau, that message appears but it is usually quickly hidden by the splash screen.

I don't worry about this.

---

### Post by bulletyuan999 on 2016-09-21
i meet this problem too right now...
but my system seems like pause there
the screen just show some texts "/dev/sda1: clean, ***/*** files, ***/*** blocks"...
how to solve it ?
that's so hardly man...

---

### Post by mörgæs on 2016-09-21
Does this happen in 16.04.1 or 16.04.0?

---

### Post by echotech2 on 2016-09-21
It happens on Ubuntu 16.04  Just a quick flash at the top of the screen if using quiet, splash in Grub.  There is another post on this a while ago but I can't find it right now.

---

### Post by mörgæs on 2016-09-21
The solution i posted in May is not relevant any more. Now the easiest approach is a fresh install of 16.04.1 (not 16.04.0) using wired internet connection throughout the process.

---

