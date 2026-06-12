---
title: "[SOLVED] Problem booting up."
date: 2008-06-12
forum: New to Ubuntu
---

### Post by k33bz on 2008-06-12
Ok so I finally go my desktop fixed, after replacing ram, cpu, video card, and finally getting my motherboard repaired. Which guessing they couldnt do, because they sent me a brand new one, exact same model. I put everything together, got my windoze (dual boot) which worked just fine after re-activating it. Then went onto my linux (Fiesty Fawn, kernel 2.6.20-16-generic)

Well it froze during boot up with the boot loader, so I restarted and tried in safe mode. And it froze again, for about 5 mins, right after loading up my device drivers for my usb ports. then gave me this read out:
```
check root= bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev ALERT! /dev/disk/by-uuid/11656662-477a-4445-b24e-279812baa932 Does not exist. Dropping into shell! 
Busybox v1.1.3 (Debian 1:1.1.3-3ubuntu)
Built in shell (ash) Enter 'help' for a list of commands.
/bin/sh: cant access tty; job control turned off
(initramfs)
```

Now I am figuring that maybe my new motherboard, even though it is the same model and everything, isnt working together with my hdd, so I tried to do it with a liveCD, I could access my Windoze HDD with a LiveCD, but it wouldnt see my Ubuntu HDD. (And yes I mean HDD, not just partitions, I have 2 seperate HDDs for my OS, one for MS, and hte other for Ubuntu.)

So can someone please help.
Thanks.

---

### Post by nowshining on 2008-06-12
you have to prob. manually mount ur Ubuntu HD from the liveCD.

in terminal

sudo mkdir /media/ubuntu

or whatever u want to name it.

if I rem. correctly:

sudo mount /dev/sda /media/ubuntu


u should be able to browse the web from the livecd :) esp. if u got Cable.

if it doesn't mount with thea above try adding an' 1 after sda, if not try bot with -F ext3.

---

### Post by k33bz on 2008-06-12
> **nowshining said:**
> you have to prob. manually mount ur Ubuntu HD from the liveCD.

in terminal

sudo mkdir /media/ubuntu

or whatever u want to name it.

if I rem. correctly:

sudo mount /dev/sda /media/ubuntu


u should be able to browse the web from the livecd :) esp. if u got Cable.

if it doesn't mount with thea above try adding an' 1 after sda, if not try bot with -F ext3.

I thank you for your comment on this, but maybe you didnt underwstand exactly what I am tryin to do. I only tried to access it through a livecd to see if I could even see it. I need that HDD to boot up and not freeze and drop me into a shell. 

Oh, and for a further update, in this shell I am not able to fdisk, at all. It says it dont recognize that command. (ash) or (busybox) shell. I checked my bios, and it sees both my hard drives.

---

### Post by Xiong Chiamiov on 2008-06-13
Is it on the live CD that fdisk doesn't work?  If so, you can try installing the gnu-fdisk package.

---

### Post by cariboo on 2008-06-13
If you read the first line of your error meesage it tells you exactly what your problem is. It can't find your hard drive by uid because you have a different motherboard and the uid has changed. It would probably be quicker to reinstall then trying to find the new uid and changing it.

Pay attention to the error messages and  they will usualyy tell you what the problem is.

Jim

---

### Post by k33bz on 2008-06-13
> **cariboo907 said:**
> If you read the first line of your error meesage it tells you exactly what your problem is. It can't find your hard drive by uid because you have a different motherboard and the uid has changed. It would probably be quicker to reinstall then trying to find the new uid and changing it.

Pay attention to the error messages and  they will usualyy tell you what the problem is.

Jim

I know what the error message was saying, I got that, especially after I did some other poking around. Was just hoping that there was a way to change th uid to where it will boot my hdd.

---

### Post by k33bz on 2008-06-13
Can someone please help with this, I am so exhausted from looking around to find a solution for this, with out having to just re-install.

---

### Post by k33bz on 2008-06-13
ok, I have re-installed, and I am still having the exact same damn problem.


SOMEONE PLEASE HELP

---

### Post by ninja67 on 2008-06-25
Oops! I am having the same problems... Can you help me out?

Thanks.

---

