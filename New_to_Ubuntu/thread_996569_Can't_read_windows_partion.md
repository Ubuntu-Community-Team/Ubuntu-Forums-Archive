---
title: "Can't read windows partion"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by WillT87 on 2008-11-29
Windows Xp Pro Sp3 on the partition of my hard drive has a virus where I can't even boot correctly. Is it possible to move files from xp to ubunu without installing anything to xp?:confused:

---

### Post by Afkpuz on 2008-11-29
Yes.  Have you already installed ubuntu?  If not, just boot from a live cd and copy your data to a jump drive/usb hard drive.

---

### Post by nhasian on 2008-11-29
you could even run a virus scanner from ubuntu and have it clean any virii from the windows partition :KS

---

### Post by WillT87 on 2008-11-29
Yes I have installed ubuntu I am using it right now. What virus scanners are there for ubuntu? I tried Malwarebytes it installed but wouldn't load with wine

---

### Post by cdtech on 2008-11-29
If you just want to pull files from the drive just mount the device to a directory.

What problem do you have booting the drive?

---

### Post by WillT87 on 2008-11-29
As I mentioned in my first post I am using Windows Xp pro. It prompts me for my user name and password like I am trying to access a server. On all my accounts in both safe mode and regular. I can log on and see my background but I get booted

---

### Post by WillT87 on 2008-11-29
Bump

---

### Post by nhasian on 2008-11-30
> **WillT87 said:**
> What virus scanners are there for ubuntu?

Give clamAV a try

```
sudo apt-get install clamav
```

---

