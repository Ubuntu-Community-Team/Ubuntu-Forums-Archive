---
title: "restricted drivers w/ custom kernel"
date: 2007-05-30
forum: Other OS Talk
---

### Post by ddp on 2007-05-30
As background, I'm new to Ubuntu and Linux but have lots of experience building and hacking custom kernels for NetBSD and FreeBSD.  But this is my first Linux installation...

I've successfully built and booted a custom kernel based on 2.6.20-18-generic (result was 2.6.20.3-ubuntu1) and all is mostly good except...  My WiFi adapter is a Thinkpad Atheros abg card, which Feisty supports with a restricted driver (madwifi) which got installed during the standard desktop-i386 installation ISO.

My question is: what do I have to do to get a compatible restricted Atheros driver for my shiny new custom kernel?  I tried just copying the essential bits from /lib/modules/<generic> to /lib/modules/<custom> but they won't load due to various addressing and fixup errors against my new kernel, no real surprise here.

Are .ko modules supposed to be loadable across different versions in Linux? 

In any case, how am I supposed to solve this?  Pointers to documentation welcome...

---

### Post by hardcore on 2007-06-21
If you have figured this out, I would appreciate knowing as I would love to use a 2.6.21 kernel instead of the default ubuntu kernel.

---

### Post by 5-HT on 2007-06-21
You'd be better of compiling the required modules for the new kernel. You can try some symlinking hackery to use Ubuntu's restricted modules, but the modules themselves are compiled against a specific kernel and most likely wouldn't work in the new one.

---

