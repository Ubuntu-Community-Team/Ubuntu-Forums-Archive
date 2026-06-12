---
title: "Set SSD as cache drive Lenovo Thinkpad"
date: 2014-01-24
forum: New to Ubuntu
---

### Post by Dr. McKay on 2014-01-24
One of the laptops I have in mind, the Lenovo E530 comes with a 1Tb HDD and a SSD of 16Gb.
In Windows, there's software to use the SSD part as cache for the HDD.

Now, some hybrid drives are self-optimzed which means that caching is optimized by the drive itself.
Others are host-optimized through software in the OS. The Lenovo falls into the latter category.

Now, apparently, it's possible to activate this in Ubuntu as well using flashcache, bcache, dmcache…
I've also read that as from kernel 3.9, linux supports SSD caching. 

So, taking into account that I would wipe the drives completely a perform a clean install of Ubuntu 13.10. 
What's the best way to go about it ?

---

### Post by DuckHook on 2014-01-27
> **Dr. McKay said:**
> ... apparently, it's possible to activate this in Ubuntu as well using flashcache, bcache, dmcache…It is possible to activate it, but I'm not sure that caching is the best way to go.

1. If caching is compiled into the kernel, you would need to customize your kernel. A custom kernel breaks updates, so you either live with security holes or commit to recompiling a kernel every one or two months.
2. It can be installed as a module but this adds complexity, fragility and makes your install very brittle. Problem is that caching works at a low level, therefore must be loaded early in the boot process. If it breaks (and there are many potential points of breakage), your system is borked and won't load.

I seriously looked into caching when I bought my SSD. It sounds really good in theory until I started delving into the details. Ultimately decided to do things differently:

1. Installed / onto SSD. 16GB is plenty.
2. Installed /tmp and /var/tmp onto HDD on two partitions of 4GB each. Again plenty.
3. Installed /swap onto HDD on partition = RAM + 1GB (for hibernate—if not using hibernate, then 2GB is enough).
4. Installed /home onto remainder of HDD. It uses by far the most storage so give as much HDD to it as you can.

Since all apps and the OS loads from SSD, but data from HDD, the system starts up like greased lightning. I have sufficient RAM to make the system very responsive and, with 16 GB, so do you.

I suspect that at some point, Ubuntu will come with an option to dedicate SSD as cache. When that happens, we can define SSD cache at install time and everything will be supported out of the box. Until then, I felt it a better choice to forego the complexity and lack of support of caching, but to use a *supported* solution that is almost as good.

---

### Post by Dr. McKay on 2014-01-27
Thx for the useful information !

---

### Post by DuckHook on 2014-01-27
> **Dr. McKay said:**
> Thx for the useful information !No problem.

Good luck and Happy Ubuntuing!

PS

If happy with answer, please mark thread "solved" using thread tools at top of page.

---

