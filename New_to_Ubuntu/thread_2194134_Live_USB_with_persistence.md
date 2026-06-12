---
title: "Live USB with persistence"
date: 2013-12-16
forum: New to Ubuntu
---

### Post by rp7183 on 2013-12-16
I have a liveusb provided to me by my employer. I don't have the root password info and I'm trying to use virtualbox to run it. I can succesfully do this fairly easily by creating the VMDK file and using that to boot, however, when I try to install the guest additions (wanting full screen of course) and I restart all of the changes are gone since there is no persistence. I have tried adding a casper-rw file in the root of the usb stick and also appending persistent to the end of the append line in the syslinux.cfg file and this does not seem to work, and virtual box starts giving IO errors. Any suggestions?

---

### Post by sanderj on 2013-12-16
Suggestion: write a new, fresh Ubuntu liveusb with Unetbootin (which works more reliably than usb-creator-gtk)

---

### Post by asus-user on 2013-12-16
> **rp7183 said:**
> I have a liveusb provided to me by my employer. I don't have the root password info and I'm trying to use virtualbox to run it. I can succesfully do this fairly easily by creating the VMDK file and using that to boot, however, when I try to install the guest additions (wanting full screen of course) and I restart all of the changes are gone since there is no persistence. I have tried adding a casper-rw file in the root of the usb stick and also appending persistent to the end of the append line in the syslinux.cfg file and this does not seem to work, and virtual box starts giving IO errors. Any suggestions?

Usually one can use a Loopback file to save persistent information. It must be named casper-rw and must be in the root of the partition.
you said that you tried to add this file, but:
1- Make sure you did it right int the first place. If the usb is mounted at /media/hda1, type in Terminal:
```
dd if=/dev/zero of=/media/hda1/casper-rw bs=1M count=128
mkfs.ext3 /media/hda1/casper-rw

```
2- When you boot and when the Live CD menu gets displayed hit the <F6> key to enter “Other Options”. This will display the arguments that the Live CD passes to the kernel. At the end of this argument list just add a space and add the word “persistent”. This will instruct the Live CD to maintain and use persistence. 

All these steps and further information you can find [here]("https://help.ubuntu.com/community/LiveCD/Persistence#Using_a_Loopback_File").

---

### Post by rp7183 on 2013-12-18
Unfortunately, this doesn't work for me as I don't have the root password. Is there any way of creating a virtual disk in VB that will allow this?

---

