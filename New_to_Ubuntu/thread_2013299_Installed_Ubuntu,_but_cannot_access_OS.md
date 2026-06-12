---
title: "Installed Ubuntu, but cannot access OS"
date: 2012-06-30
forum: New to Ubuntu
---

### Post by ApUUbunU on 2012-06-30
Hi all,

I recently installed Ubuntu 12.04 using on my laptop alongside Windows 7. However, upon restarting the computer following the installation Windows 7 loads immediately and the grub menu does not appear - it seems as if I cannot access my Ubuntu installation.

Does anyone know of a solution to this problem? I've done a bit of searching on this forum, but unfortunately cannot find anyone with the same problem.

Thanks for the help!

---

### Post by mapes12 on 2012-06-30
Try Boot Repair:-

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ApUUbunU on 2012-06-30
Yep, that worked, thanks so much!

---

### Post by NikTh on 2012-06-30
Can you say please how did you the installation ? i mean what media did you use ? LiveUsb ? 
Cause i smell a bug ... but i am not sure. 
I recently installed ubuntu from LiveUsb alongside another linuxOS. When installation finished i discovered that grub installed in usb(/dev/sdb)  and not hdd.(/dev/sda).

---

### Post by jmfal on 2012-06-30
Your right Nikth 
Been seeing to many posts with the same problem.

---

### Post by oldfred on 2012-06-30
The auto installs default to sda. 

We have seen some BIOS that promote the flash drive to sda, so the installer installs to the flash drive when it should install to the hard drive.

It also can be whether you reset BIOS to default to flash drive or used one time boot key to select flash drive. 

Some testing required to prove if a bug or not.

---

### Post by NikTh on 2012-06-30
> **oldfred said:**
> The auto installs default to sda. 
I know this . When i selected "something else" i saw that usb recognized as /dev/sdb from Ubuntu installer.

> **oldfred said:**
> We have seen some BIOS that promote the flash drive to sda, so the installer installs to the flash drive when it should install to the hard drive.
I didn't know this but i cannot see it as in auto install.

> **oldfred said:**
> It also can be whether you reset BIOS to default to flash drive or used one time boot key to select flash drive. 
I didn't use one time boot key . I configured bios to boot from usb first - CD/DVD second - HDD third.

> **oldfred said:**
> Some testing required to prove if a bug or not.
I know this so i didn't filed a bug . I wrote "smell" but "smell" can be wrong :)

I will test it again with bios reset and one boot key.
Thanks.

---

### Post by NikTh on 2012-07-03
Same results @oldfred. 
I reset Bios and select one boot key . I saw from "something else" section that usb recognized as /dev/sdb . Move back to auto install installer installs grub on usb 
**BUT**
maybe you have point here. This happened only with this specific BIOS. Neither to another desktop i have or laptop. 
I will not report this as bug for now. 
Thanks.

---

