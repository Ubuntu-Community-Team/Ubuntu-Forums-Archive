---
title: "Can we use rEFIT with an Intel based PC (not Mac)?"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by the8thstar on 2008-06-21
I stumbled upon this nice GUI bootloader called rEFIT. I was wondering if it could be run on a standard Intel based PC. My idea was to replace Grub and use rEFIT instead.

Your feedback would be appreciated!

[URL="http://refit.sourceforge.net"]
http://refit.sourceforge.net/[/URL]

---

### Post by cariboo on 2008-06-21
I've had a look at the page you may be able to build it from the source code, but seeing as you're asking this in absolute beginner it may beyond your skills at this time.

There are some excellent threads on making grub look better. have a look at this.

[http://ohioloco.ubuntuforums.org/showthread.php?t=481957](http://ohioloco.ubuntuforums.org/showthread.php?t=481957)

Jim

---

### Post by the8thstar on 2008-06-21
Thanks. I've tried pimping up Grub in the past and I've used GfxBoot too. But rEFIT looks REALLY nice and better than the Grub or GfxBoot, that's why I wanted to try it.

Any wiz out there interested in a Linux version of rEFIT???

---

### Post by the8thstar on 2008-06-22
Bump

---

### Post by kennethsime on 2010-07-27
Unfortunately, rEFIt is not actually a bootloader, though it looks quite like one. You still need GRUB to boot linux. :(

You can download rEFIt as an ISO and also as a tar.gz, so in theory you should be able to get it to run on a linux machine, but it's really pointless because it doesn't know how to boot linux.

For example on my machine, which is dual-booting between Snow Leopard and Lucid Lynx, (if and) when rEFIt loads when I power on, I choose linux or mac, and if I choose linux that partition starts, runs grub, then boots ubuntu from there.

I would love to do this too, if it were possible...

---

