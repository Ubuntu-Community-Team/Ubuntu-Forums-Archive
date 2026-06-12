---
title: "Linux Platform Independent"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by gagan3019 on 2011-09-24
Hi I just wanted to know what is there in linux that makes it hardware independent , is it kernel that is written different for different processor architecture , e.g as i read that android is a linux based operating system and ubuntu for PC is also linux then how does linux run on different platforms ?
I am very new to linux , please answer this question

---

### Post by Lisiano on 2011-09-24
Most stuff is independent but some items are (Kernel and some userland programs). You can run Linux on virtually ANYTHING. Ranging from a humble calculator to the worlds fastest supercomputer.
Read more on the Ubuntu documentation site.
[https://help.ubuntu.com/11.04/installation-guide/i386/hardware-supported.html](https://help.ubuntu.com/11.04/installation-guide/i386/hardware-supported.html)

EDIT: I'll also note that your Android phone probably has a ARM processor while your PC has a general purpose CPU, most notably x86_64 (64-bit) or x86 (32-bit). AMD and Intel processors are both General Purpose.

---

### Post by gagan3019 on 2011-09-24
Thanks for reply

---

### Post by Blasphemist on 2011-09-24
This is also a good place to start. [http://en.wikipedia.org/wiki/Linux](http://en.wikipedia.org/wiki/Linux)

At the end you'll see links to many other linux related subjects.

---

### Post by lykwydchykyn on 2011-09-24
Technically, nothing is "platform independent" -- it's just been made to support many many platforms.

Since Linux is open-source and openly developed, anyone who needed Linux to support a given hardware platform could submit patches to modify to code to do so.

Of course, the source code has to be compiled to support the platform in question; you can't run the normal Ubuntu disc on a Sparc processor, for example, because it's only been compiled for x86 and amd64.

---

### Post by Lars Noodén on 2011-09-24
One example, Debian, has been [ported to 11 architectures](http://www.debian.org/ports/).  Ubuntu is derived from Debian though it uses only the x86 and amd64.

Edit: FWIW [OpenBSD](http://www.openbsd.org/plat.html) is ported to 17 platforms.

---

