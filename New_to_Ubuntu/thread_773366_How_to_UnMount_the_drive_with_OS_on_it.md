---
title: "How to UnMount the drive with OS on it ??"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by t-molli on 2008-04-28
I want to image my Ubuntu hard drive, but am directed to unmount the drive first. How do you unmount the drive your OS is on? gParted won't let you unmount an/the active system, so what's the trick?

Is imaging your active drive only possible via a boot disk and if so, how would you make one in Linux?

Thank you very much in advance...

---

### Post by Tatty on 2008-04-28
Correct, you cannot unmount a filesystem you are using.

You need to boot to a live CD.  how have you installed ubuntu?  You may already have a live cd...  if not then download one here... [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

**Edit:** This link tells you how to image a hard disk with partimage [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by t-molli on 2008-05-02
Thanks for this.

I did use the Live CD to boot. I then looked at the partitions using gParted. I saw the partitions I wanted to experiment with (sda1 and sda2) and even tried to unmount them, but the option to unmount was greyed out.

What am I doing wrong? 

Thanks again..

---

### Post by oedha on 2008-05-02
try gparted liveCD
[http://gparted.sourceforge.net](http://gparted.sourceforge.net)

---

### Post by avtolle on 2008-05-02
> **t-molli said:**
> Thanks for this.

I did use the Live CD to boot. I then looked at the partitions using gParted. I saw the partitions I wanted to experiment with (sda1 and sda2) and even tried to UNmount them, but the option to unmount was greyed out.

What am I doing wrong? 

Thanks again..
I've had this problem, too. What I found, in my situation, was that something mounted the drive (icon showed on the desktop). Navigate there, right click, select unmount volume, then go back to gParted, should show the partitions not mounted, and do your thing. BTW, don't tarry; the system tries to mount the drive again, and you'll find yourself needing to do this process over. You may get an error message while in gParted complaining that the volume cannot be mounted, just close it, and continue on. HTH.

---

### Post by Oldsoldier2003 on 2008-05-02
> **t-molli said:**
> Thanks for this.

I did use the Live CD to boot. I then looked at the partitions using gParted. I saw the partitions I wanted to experiment with (sda1 and sda2) and even tried to UNmount them, but the option to unmount was greyed out.

What am I doing wrong? 

Thanks again..
for a working Linux install you can unmount non system partitions by:
```
sudo umount <device>
```

On the live cd you can try umount or if that doesn't work do sudo umount and just hit enter when prompted for password.

 The [GParted Live CD]("http://gparted-livecd.tuxfamily.org/") shouldn't mount anything so this shouldnt be a problem.

---

