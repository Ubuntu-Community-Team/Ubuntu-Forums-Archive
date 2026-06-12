---
title: "does ubuntu support hot swapping?"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by cheepo on 2012-08-02
Hello all, I'm completely new to Linux. I just installed ubuntu 12.04  And I'm not seeing my usb drives when I plug them in? I see them after I reboot. My question is does ubuntu support hot swapping??? If so how? Thanks.

---

### Post by ranger1021994 on 2012-08-02
Yes,it supports hot swapping

Go to ubuntu icon in Unity,type Disks
See the disks connected..
If you see your USB drive mount it

Or if you have Gparted use it and mount your USB if it is detcted

---

### Post by cheepo on 2012-08-21
I tried that, but nothing shows up after typing in the disk or disks in unity. Also how exactly would I do it in gparted? I don't see the disk there??

---

### Post by anewguy on 2012-08-22
I noticed ranger1021994 has it with the first letter in upper case.  I haven't ever tried this, so I don't know how the disk or disks command works, but since linux/ubuntu is case sensitive, it would mean that "disks" is not the same as "Disks".  Maybe you should try matching case and see if it makes a difference.

---

### Post by mcduck on 2012-08-22
> **anewguy said:**
> I noticed ranger1021994 has it with the first letter in upper case.  I haven't ever tried this, so I don't know how the disk or disks command works, but since linux/ubuntu is case sensitive, it would mean that "disks" is not the same as "Disks".  Maybe you should try matching case and see if it makes a difference.

The Dash search is not case sensitive, and is usually rather smart and searches even for program descriptions etc. information instead of just a dumb name-based search. (ie. search for "photo" or "image" should bring up Gimp even though neither word is part of the program's name)

So searching for "disk" should definitely bring up the Disk Management tool. Unless of course the system is running on a other language than English... ;)

Anyway, the best troubleshooting method, as usually, is using the command line. Running "mount" or "sudo fdisk -l" should list any mounted drives/partitions. And if the drives don't appear there, you can run "tail -f /var/log/syslog" and then plug in the drive to see the log messages about how it's detected by the system and of course also any possible errors/warnings.

---

