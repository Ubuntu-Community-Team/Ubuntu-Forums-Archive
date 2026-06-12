---
title: "64 bit vs 32 bit"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by Autodave on 2012-05-05
Can you run 32 bit programs on 64 bit Ubuntu 12.04?

---

### Post by strask on 2012-05-05
Mostly, yes. But some apparently have problems. Is there a particular 32 bit program you are concerned about?

---

### Post by khelben1979 on 2012-05-05
Short answer: yes.

But if there are 64 bit packages I would strongly recommend you use these instead, unless the 32 bit packages works better.

---

### Post by Autodave on 2012-05-05
> **khelben1979 said:**
> Short answer: yes.

But if there are 64 bit packages I would strongly recommend you use these instead, unless the 32 bit packages works better.


To both of you who responded, thanks!  I have a 64 bit machine and was just wondering if I am missing out by running the 32 bit Ubuntu package.

---

### Post by khelben1979 on 2012-05-05
> **Autodave said:**
> To both of you who responded, thanks!  I have a 64 bit machine and was just wondering if I am missing out by running the 32 bit Ubuntu package.

The thing I can imagine is that you loose some performance, since the 64 bit packages are software which are better optimized for more modern processors.

The worst part of using a 64 bit package distribution have historically been when it was rather new, since many packages hadn't been compiled up for 64 bit and by using 32- and 64 bit packages could create package conflicts within the distribution, but I would think that these issues are a thing of the past.

If you're looking for performance, go for 64 bit.

---

### Post by perspectoff on 2012-05-23
To run some 32-bit packages on a 64-bit computer you will need 32-bit libraries, which can be installed:

 sudo apt-get install ia32-libs

I don't have any apps any longer that come only in 32-bit versions and not in 64-bit versions; Precise Pangolin is the first distro version in which I did not find it necessary to install ia32-libs.

Having said that, Ubuntu itself these days seems oriented at 32-bit processing on ARM devices, and I can't vouch for Ubuntu packages (I am a Kubuntu user primarily, not an Ubuntu user).

---

