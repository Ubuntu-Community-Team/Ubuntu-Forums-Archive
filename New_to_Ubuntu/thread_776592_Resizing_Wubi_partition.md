---
title: "Resizing Wubi partition"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by haziz on 2008-04-30
I installed Ubuntu on my Windows Vista machine on a second (partially full) hard drive. I accepted the default partition size of 15 Gig but in retrospect should have selected a larger size, partly for programs that I am installing like crazy and partly for media that I am ripping to my music folder.

Is there a way of resizing my Wubi partition/file without messing up the system or should I reinstall. I would rather avoid the latter since I just spent the last 3 days tweaking the system.

Thanks.

Sincerely,

Hany.

---

### Post by haziz on 2008-05-01
Bump

---

### Post by bilal.17 on 2008-05-01
if you boot the live CD then you go to the partition editor in System->Administration, then  I think there you might be able to do it

---

### Post by mlentink on 2008-05-01
> **bilal.17 said:**
> if you boot the live CD then you go to the partition editor in System->Administration, then  I think there you might be able to do it

I don't think so. Wubi does not install in a real partition, but in a wrapper, a 'virtual partition', which is actually a file in Windows ntfs-filesystem. So I hardly think GParted would be able to do something with it.


EDIT: you might want to take a look at this, which I found by googling for "change size wubi disk" : [https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b](https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b)

---

### Post by Paqman on 2008-05-01
Normally you'd use LVPM to change the size of a Wubi image, but I believe it needs to be updated to be compatible with Hardy. You might be stuck with the size you've got for now.

You could always try backing up your /home partition, making a [list of your installed packages](http://ubuntuforums.org/showthread.php?t=261366) and reinstalling Wubi with a bigger chunk of the disk.

---

### Post by piju on 2010-07-06
hey,
check out here.

i was successfully resize my home partition with this guide

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by bodhi.zazen on 2010-07-07
> **piju said:**
> hey,
check out here.

i was successfully resize my home partition with this guide

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

It can be done, as you say, but ....

Most people who use wubi are new to Linux.

IMO, if you want to stay with Ubuntu, rather then messing with all that, I highly advise you bite the bullet and perform a standard installation, including partitioning the hard drive and installing grub.

You do not *have* to, but it is easier.

---

### Post by kismeras on 2010-08-01
> **bodhi.zazen said:**
> It can be done, as you say, but ....

Most people who use wubi are new to Linux.

IMO, if you want to stay with Ubuntu, rather then messing with all that, I highly advise you bite the bullet and perform a standard installation, including partitioning the hard drive and installing grub.

You do not *have* to, but it is easier.

Hey Guys, 

I was wondering the same thing. I used the default 20GB that WUBI offered, but now i need more space. I've been running Linux Mint9 on my laptop, installed in Windows 7 Pro via Wubi. Here's my question:
Can i make an image of my Mint installation? That way when i go to reinstall using WUBI, i can allocate more space to it and just install my image so that i don't have to start from scratch. Thereby avoiding the need to resize the existing virtual disk. Thanks.

P.S. - I'm not trying to hijack this thread. Maybe my idea of making an image and using that would work for the OP as well.

---

### Post by Elfy on 2010-08-01
> **kismeras said:**
> Hey Guys, 

I was wondering the same thing. I used the default 20GB that WUBI offered, but now i need more space. I've been running Linux Mint9 on my laptop, installed in Windows 7 Pro via Wubi. Here's my question:
Can i make an image of my Mint installation? That way when i go to reinstall using WUBI, i can allocate more space to it and just install my image so that i don't have to start from scratch. Thereby avoiding the need to resize the existing virtual disk. Thanks.

P.S. - I'm not trying to hijack this thread. Maybe my idea of making an image and using that would work for the OP as well.

You could move the wubi to a new and seperate partition using lvpm - [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

The OP has not been here for over a year. Closing thread - if you need more help I suggest you start a new thread.

---

