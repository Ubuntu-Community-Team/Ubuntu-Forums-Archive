---
title: "MASSIVE problem after failed update"
date: 2015-03-03
forum: New to Ubuntu
---

### Post by hmiersch on 2015-03-03
Hi
Today I ran software updater. It exited with an error telling me there was a problem installing a package. I wanted to boot OSX so I restarted the mac, thinking I could try again later. But now the partition is inaccessible. It doesn't appear in the refind menu and OSX doesn't complain about it either. So what can I do? HELP!

Correction: OSX can see the partition but it can't read the Linux format which is normal. But I still can't boot from the Linux HD

---

### Post by ajgreeny on 2015-03-03
Which partition is inaccessible, the mac or Ubuntu, it's not clear from your question?

---

### Post by hmiersch on 2015-03-03
The Ubuntu partition is the one that disappeared. OSX works normally.

---

### Post by JeQhdMD on 2015-03-03
Is it really gone, . . . am not familiar with MacOS at all or refind . . . but have you tried running a Live DVD or USB-Stick, then starting "gparted" to actually check your partitions?   Might be interesting.

---

### Post by hmiersch on 2015-03-04
Is it really gone? I sure hope not!
Later I'm gonna try installing Linux on the internal HD and then I'll see if I can access the disappeared partition from there...

---

### Post by Impavidus on 2015-03-04
Installing an operating system on a hard drive is a great way of making damaged partitions really disappear.

Updates gone wrong can make a system unbootable, but destroying the partition is unlikely. Try booting from a live disk and investigate. Linux is better at handling Linux partitions than Mac. The command```
sudo parted -l
```should list your partitions. If the Ubuntu partition is still there, the file manager may be able to mount it and let you access it.

---

### Post by hmiersch on 2015-03-04
> **Impavidus said:**
> Installing an operating system on a hard drive is a great way of making damaged partitions really disappear

I know that. I'm new to Ubuntu in particular but not to computing in general. The missing partition is on an EXTERNAL HD and I'm gonna install on the INTERNAL HD.

---

### Post by philinux on 2015-03-04
Could be a failed grub update.

---

### Post by hmiersch on 2015-03-04
Backing up the internal HD now, then I'll install Ubuntu on it. I hope then I can at least read the external HD with the problem

---

### Post by hmiersch on 2015-03-07
Ok, I've installed Ubuntu on my internal HD but I still have problems:
- in the new Ubuntu install, I can't find the HD with the failed update. It doesn't appear in files, it's not on the desktop and I cant find it in the terminal either.
- in OSX the HD with the failed update appears in disk utility, but the individual partitions don't. Since disk utility can see the individual partitions of the new Ubuntu install, I'm assuming that's a bad sign, right?
So what can I do? Or should i ask, CAN I do anything? I'd HATE to lose those files...

---

