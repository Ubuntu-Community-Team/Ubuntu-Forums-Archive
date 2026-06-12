---
title: "Fakeraid Linux"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by sc30317 on 2008-10-11
Hey all,

I have attempted to install a couple linux distros (arch,debian,ubuntu)in fakeraid using the wikis from each website.  Each has the same problem -

Grub shows up, and when I try to enter linux, grub error 15 shows up.

I go into a grub command line and type root (hd0,4), and it gives the correct root partition
I type kernel /boot/vmlinuz26 and it gives me an appropriate response

however; when I type boot after this, the boot begins, and it hangs on Booting processor 1/1 eip 3000.  Any solutions?

---

### Post by germanix on 2008-10-11
Go to this URL:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Hope it works

---

### Post by sc30317 on 2008-10-13
Please read my post before responding- that had nothing to do with my post, just how to install raid.  Any other suggestions?

---

### Post by sc30317 on 2008-10-14
no one?

---

### Post by LowSky on 2008-10-14
> GRUB Error 15 : "Error while parsing number"
This error is returned if GRUB was expecting to read a numbur and encountered bad data.


[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) for fixing grub

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) 
germanix's suggestion is a good one, I would look over how you actually set up the raid

---

