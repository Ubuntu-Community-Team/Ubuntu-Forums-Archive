---
title: "[SOLVED] a question on linux kernel"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by fourthofjuly on 2008-09-24
hi...

am just curious...  is there any difference in the kernels of different distros...? 

like say is the kernel of ubuntu exactly identical to that of fedora, opensuse, mint or redhat?

also, how can i access the kernel source files in ubuntu? i would like to see the actual lines of codes that are in the heart of my system, again only out of curiosity...

thanks...

---

### Post by GregMB on 2008-09-24
Unfortunately, I don't have an answer for you. But, it's a great question. I've been wondering that myself.

---

### Post by billgoldberg on 2008-09-24
I'm pretty sure the kernel is optimized for Ubuntu.

For the source:

[https://help.ubuntu.com/community/Kernel/Compile#Get](https://help.ubuntu.com/community/Kernel/Compile#Get) the kernel source

---

### Post by NullHead on 2008-09-24
Well each distro downloads the latest kernel source files from [http://kernel.org](http://kernel.org) and makes a custom build of the kernel to better suit their needs for the specific version of distro they're building.

---

### Post by perlluver on 2008-09-24
> **billgoldberg said:**
> I'm pretty sure the kernel is optimized for Ubuntu.

Indeed it is, Ubuntu adds over 100 lines to the Kernel, the other distros, do the same, even Slackware adds some things to the Kernel.  So in closing they are all based off of the Linux Kernel, but optimized for the particular system.

---

### Post by SunnyRabbiera on 2008-09-24
Well typically most distros carry the same kernel, but do different things with it.
Most modify the kernel to their needs, like Mandriva, Redhat Ubuntu.
But distros like mint dont modify the kernel much if at all as they are spin off distros.
The kernel in mint is the same as the one in Ubuntum its what is pre packaged that makes it different.
But from what I see most modern distros use the same base kernel, its how they modify it that matters.

---

### Post by fourthofjuly on 2008-09-24
thanks, think i get it, 

how about the second part of my question? 

where are the kernel lines of codes located on my system?

---

### Post by PmDematagoda on 2008-09-24
> **fourthofjuly said:**
> thanks, think i get it, 

how about the second part of my question? 

where are the kernel lines of codes located on my system?

If you mean the source, it isn't included by default. However you can download the vanilla linux source from [here]("http://www.kernel.org/pub/linux/kernel/v2.6/") and extract it to where ever you wish and then start hacking, or you can install the source of Ubuntu's kernel with:-
```
sudo apt-get install linux-source-2.6.24
```
The source can then be found in /usr/src/linux-2.6.24/.

---

