---
title: "Windows7, Windows8 and Ubuntu"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by chairedup on 2012-05-24
Hello I am new to linux. my system has 2 drives with multiple partitions on each. on one i win7 and the other win8 preview. on the win8 drive i have a blank partition. if i install ubuntu will the boot screen for win7 and8 still be accessible? will it turn the 2 choices into 3 choices? will i have to modify something in ubuntu to make 3 choices? would it be easier to setup a separate system?
thanks chairedup:confused:

---

### Post by MadmanRB on 2012-05-24
Ubuntu should be able to detect both and add them to the bootloader, I dont see why not

---

### Post by wilee-nilee on 2012-05-24
> **chairedup said:**
> Hello I am new to linux. my system has 2 drives with multiple partitions on each. on one i win7 and the other win8 preview. on the win8 drive i have a blank partition. if i install ubuntu will the boot screen for win7 and8 still be accessible? will it turn the 2 choices into 3 choices? will i have to modify something in ubuntu to make 3 choices? would it be easier to setup a separate system?
thanks chairedup:confused:

If you have boot partitions for each windows the MS boot you see know will be what grub leads you to, from the windows controlling their boot.

If you use no boot partitions on the windows installs you would have the straight to either windows from grub, don't go removing the boot partitions though now.

This is from my experience, yours may be different.

---

### Post by oldfred on 2012-05-24
WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by chairedup on 2012-05-24
ok each drive has a boot partition, the first partition. the empty partition i want to use is on the win8 drive. so i just need to choose the blank partition for ubuntu and it will take care of the boot menu, correct?
thanks for quick replies from both.
chairedup

---

### Post by wilee-nilee on 2012-05-24
> **chairedup said:**
> ok each drive has a boot partition, the first partition. the empty partition i want to use is on the win8 drive. so i just need to choose the blank partition for ubuntu and it will take care of the boot menu, correct?
thanks for quick replies from both.
chairedup

Grub should get you to all the windows basically.

I would check the links by oldfred though.

You have made a recovery disc in W7 right?

---

### Post by chairedup on 2012-05-24
thanks again. 7 and 8 work fine dual booting for now i think i will put ubuntu on a different box. i would like to get the feel of it. one more question, are virus' a concern as much with linux?

---

### Post by wilee-nilee on 2012-05-24
> **chairedup said:**
> thanks again. 7 and 8 work fine dual booting for now i think i will put ubuntu on a different box. i would like to get the feel of it. one more question, are virus' a concern as much with linux?

A kind of complex area for discussion, basically you are safer in general, there are different definitions of a virus for linux and MS setups, here is the security section.
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

---

