---
title: "Ubuntu instalation fails for Lenovo Yoga 710"
date: 2016-09-15
forum: New to Ubuntu
---

### Post by dtom2 on 2016-09-15
Hi, 

i am trying to install Ubuntu 16.04 LTS on a Lenovo Yoga 710 14 ISK alongside windows 10 home edition. I followed all the instructions and solutions (firmware settings and nodemoset)  under [https://ubuntuforums.org/showthread.php?t=2301116](https://ubuntuforums.org/showthread.php?t=2301116) but still no success. Attached the print screens from the error messages after i choose install Ubuntu.

Anybody has an idea? 

Thanks
Dionysios

---

### Post by mastablasta on 2016-09-15
is the image you are installing from good?

---

### Post by dtom2 on 2016-09-15
Yes the image is ok.

---

### Post by Geoffrey_Arndt on 2016-09-15
Did you read the official site install instructions?   (the link in your post#1 doesn't address most important install procedures/instructions).

For example, did you use the custom install option (aka "_something else_") instead of the "_alongside_" option?   Did you disable fast/quick start in Windows prior to install?   Did you temporarily turn off secure boot?  Did you have unallocated space on the HDD?   Did you create a linux partition and pre-format it with ext4 (optional but clarifies install)?

[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

### Post by Bucky Ball on 2016-09-15
And also ... Did you boot to Windows and switch off hibernation? Is Windows installed in UEFI or legacy mode? Ubuntu *_must_* be installed in the same mode. Boot to the BIOS and check (it may also tell you that info somewhere in Windows, don't use so don't know).

BTW, it's 'nomodeset'. If you were typing in the word you gave, it was probably throwing an error.

---

### Post by dtom2 on 2016-09-16
Hi,

thank you all for your replies. Finally i solved the problem  looking around the net. The problem lies with the touchpad driver most  probably. As soon as it was blacklisted installation continued just  fine. 

so you have to blacklist the driver by modprobe.blacklist=i2c_hid.

---

### Post by Bucky Ball on 2016-09-16
Well done, thanks for marking as solved and sharing the fix. Hopefully it will help other in future. :)

Enjoy the ride.

---

