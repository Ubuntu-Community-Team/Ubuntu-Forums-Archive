---
title: "Few questions to the kernel conscious :-)"
date: 2008-02-03
forum: Packaging and Compiling Programs
---

### Post by JamesUser on 2008-02-03
I am sorry if I am posting this in the wrong forum. But I feel this is where I will get the right ppl to read this post. :-)

1. I compiled the kernel on my pc a couple of days ago. I ran make gconfig and checked a few drivers (like my memory card reader's) to be compiled by default. This doesn't seem to have made it any better than the default installation. Both detect the card equally quickly. Guess, there are a few issues with my compilation. I am able to boot into it. But it doesn't seem to detect my wi-fi card.

2. I am trying to optimize(in terms of both size and performance) the ubuntu kernel for my machine. There don't seem to be many good resources on this. Can someone nudge me in the right direction? Anybody reading this thread has done it before and documented their experience(s)?

3. There are some older kernels installed as well, which are unnecessarily taking up a lof space. I would like to remove them all. So, can I just comment those entries in GRUB's menu.lst and remove those directories under /usr/src?

---

### Post by Whiffle on 2008-02-03
1)  Trial and error really is about the only way to get things really working, which is why distros take the shotgun approach and just include everything.  I havn't noticed much difference between running a modular kernel or a monolithic one.

2) For me, its just going through the menuconfig and taking out stuff I know I'll never use.  If you have questions, google helps alot, and so does hitting the ?

3)You should be able to remove them with apt-get/synaptic/aptitude etc.

---

### Post by JamesUser on 2008-02-04
Yup.. I removed a couple of older kernels with apt-get. That gave me back 200 MB of free space. I ran out of space on my 8 gig ubuntu partition. Now, it's more usable.

---

