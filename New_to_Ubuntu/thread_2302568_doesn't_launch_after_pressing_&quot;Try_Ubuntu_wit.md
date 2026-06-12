---
title: "doesn't launch after pressing &quot;Try Ubuntu without installing"
date: 2015-11-11
forum: New to Ubuntu
---

### Post by Biaou on 2015-11-11
Hi,

I'm trying to get ubuntu on my HP Envy x2. I created a bootable USB with Ubuntu 15.10. 
I can access to the first grub menu but when I press any of the proposition (Try ubuntu without installing ; Install Ubuntu ; OEM install ; Check disc for defects) it get me to a black screen and doesn't go to Ubuntu.
The fact is my computer is kinda rare and I can't find any people with the same problem and a solved issue.

For informations, I put the file bootia32 in the EFI/BOOT directory in my USB stick, if I hadn't it wouldn't launch (I tried without).

Thanks for your help.

---

### Post by grahammechanical on 2015-11-11
My guess is that you either have a 32 bit UEFI with a 64 bit CPU. And that is not unknown. Or. a 32 bit UEFI with a 32 bit CPU and are using a 64 bit bit version of Ubuntu which will not run. Just guessing.

---

### Post by stalkingwolf on 2015-11-11
are you using a disk or flash drive?

---

### Post by leunam12 on 2015-11-11
Maybe it's a video card issue, wait for a few minutes after the black screen comes up to see if it boots up.

---

### Post by Biaou on 2015-11-12
Hi, thanks for your answer !

> My guess is that you either have a 32 bit UEFI with a 64 bit CPU. And that is not unknown. Or. a 32 bit UEFI with a 32 bit CPU and are using a 64 bit bit version of Ubuntu which will not run. Just guessing.

If I don't use the 64bit I can't reach the grub menu, USB stick isn't even recognized

> are you using a disk or flash drive?         

I'm using a flash drive

> Maybe it's a video card issue, wait for a few minutes after the black screen comes up to see if it boots up.

I waited fifteen or twenty minutes, it still don't work

---

### Post by sandyd on 2015-11-12
Searched around a bit, apparently, the Envy2 uses a 32bit UEFI with an [Intel Atom Z2760]("http://ark.intel.com/products/70105/Intel-Atom-Processor-Z2760-1M-Cache-1_80-GHz")

[Here is the bug]("https://bugs.launchpad.net/ubuntu-cdimage/+bug/1025555") that is preventing you from installing Ubuntu, try the instructions at the very top.

That being said, this is a clovertrail CPU. The last time I checked, they are designed for Windows 8 and not supported under Linux, though that may have changed recently.

---

