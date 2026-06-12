---
title: "Which flavor of Ubuntu would you recommend?"
date: 2010-06-28
forum: Programming Talk
---

### Post by stirbad on 2010-06-28
Hi all,

I'm going to be coding in either C or Python for an embedded system, and I was wondering which flavor of Ubuntu you'd recommend that I install to the board. The board will be interfacing with a camera and will do some data mining/analysis, and all of this will be autonomous in the end product, so I don't need anything too fancy to work with. I just need to be able to code in either C or Python and have the program run on its own indefinitely in the end.

I've never had experience with Ubuntu or even Linux before, so I was thinking of taking the safe route and installing Ubuntu over things like Xubuntu since most people seem to prefer it. I know this won't matter much in the end since both run on the same kernel and the GUI won't play a vital role at all, but I'd still like some input as to which flavor of Ubuntu I should go for.

Ideally, whatever I choose won't hog resources that the autonomous program will be using.

---

### Post by trent.josephsen on 2010-06-28
Any variety of Ubuntu will be rather hefty for embedded applications, being designed for desktop use and all... can you give some more information on the hardware you'll be using?

---

### Post by stirbad on 2010-06-28
The board I'll be using has an Intel ATOM 1.6 GHz processor with a 512 KB L2 Cache. Right now all it's hooked up to is a power supply, CD/DVD drive, HDD, and a monitor. I'll most likely get a hold of a 2 GB stick of RAM for it. The final product will only have the board hooked up to a power supply and to an external camera, and possibly some sort of data transmitter.

---

### Post by trent.josephsen on 2010-06-28
> **stirbad said:**
> The board I'll be using has an Intel ATOM 1.6 GHz processor with a 512 KB L2 Cache. Right now all it's hooked up to is a power supply, CD/DVD drive, HDD, and a monitor. I'll most likely get a hold of a 2 GB stick of RAM for it. The final product will only have the board hooked up to a power supply and to an external camera, and possibly some sort of data transmitter.

And, I presume, a hard drive or some other source of static memory?

---

### Post by stirbad on 2010-06-28
Correct, some sort of static memory will be available, although it will most likely be small. Memory management will become an issue, but I'll handle that with the program I'll be writing.

---

### Post by Some Penguin on 2010-06-28
Looks like their used to be an Ubuntu Mobile version, but it's no longer developed and the Canonical page for it appears to be gone.

You might want to consider something like Gentoo, which is likely easier to be more 'minimalist' while still having some semblance of packaging and alterable configurations.  It's been installed on a guitar...

[http://www.gentoo.org/news/20100125-misa-guitar-interview.xml](http://www.gentoo.org/news/20100125-misa-guitar-interview.xml)

---

### Post by stirbad on 2010-06-28
> **Some Penguin said:**
> Looks like their used to be an Ubuntu Mobile version, but it's no longer developed and the Canonical page for it appears to be gone.

You might want to consider something like Gentoo, which is likely easier to be more 'minimalist' while still having some semblance of packaging and alterable configurations.  It's been installed on a guitar...

[http://www.gentoo.org/news/20100125-misa-guitar-interview.xml](http://www.gentoo.org/news/20100125-misa-guitar-interview.xml)

Thanks. I'll look into Gentoo.

I should mention that I'm not necessarily tied down to free distributions of Linux, and I came across BlueCat, which seems promising. Does anyone have any experience with BlueCat?

---

### Post by unter on 2010-06-28
what about the android x86 version? 
[http://www.androidx86.org/](http://www.androidx86.org/)

---

