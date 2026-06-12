---
title: "Ubuntu won't boot"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by mcbgun on 2008-06-26
Right guys,

I've been tearing my hair out trying to figure out this problem.

Basically I have a Dell Xps 420 with 2 hard drives in raid0 stripe format.

Vista has installed fine on the raid partition but when it came to installing ubuntu.....hell no!

I have tried installing ubuntu on this raid0 partition but to no avail. 

What happens is when I install it....when it comes to booting up, firstly it said grub error 21 i think...then it said grub  error 2...now it just says grub and freezes!

Is it the raid that's mucking it up? I've run out of ideas! Please help!

---

### Post by ercferret18 on 2008-06-26
maybe reinstall ubuntu... srry thats all i can think of.

have you tried using wubi?

[http://www.wubi-installer.org/](http://www.wubi-installer.org/)

---

### Post by Victormd on 2008-06-26
Most likely, yes. I've read several posts regarding RAID and ubuntu boot issues.
One question that comes to mind is: Is your RAID soft or hardware controlled? If it's hardware configured then grub should recognize it but if it's software controlled (most on-board RAID fall under this category), then grub will have a hard time figuring it out.

---

### Post by Victormd on 2008-06-26
Check out this thread:
[http://ubuntuforums.org/showthread.php?t=816292&highlight=ubuntu+raid](http://ubuntuforums.org/showthread.php?t=816292&highlight=ubuntu+raid)

---

### Post by Victormd on 2008-06-26
> **mcbgun said:**
> What happens is when I install it....when it comes to booting up, firstly it said grub error 21 i think...then it said grub  error 2...now it just says grub and freezes!

Is this boot process for the Live CD or after install?
You might want to try using [Supergrub]("http://www.supergrubdisk.org/") to fix your grub.

---

### Post by mcbgun on 2008-06-26
Hi guys.

Right firstly Wubi is awesome....if your running xp not vista it seems lol. In xp it installed perfectly...i'm typing in ubuntu as we speak on my laptop! 

I was pretty gutted then that on the dell xps i did exactly as I did with my xp laptop only to find that busybox came up instead of what should happen which is booting into ubuntu and then letting the automated installation finish.

Pretty much gutted now!

Not sure what to do...i don't understand how to use busybox and anything i've read on it confuses the hell out of me as I don't know what problem i'm experiencing.

Any more help guys and gals??

---

### Post by mcbgun on 2008-06-26
After trawling the internet i'm going to arrive at the conclusion that raid just isn't supported yet. I'll make do with having it on my laptop for now as all I want it for is project work. Fingers crossed for a release that supports raid!

Thanks for all your help peeps....WUBI IS AWESOME!!!

---

