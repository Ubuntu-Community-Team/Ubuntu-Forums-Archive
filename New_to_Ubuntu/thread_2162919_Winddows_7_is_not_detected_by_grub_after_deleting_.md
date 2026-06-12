---
title: "Winddows 7 is not detected by grub after deleting one of prober file."
date: 2013-07-16
forum: New to Ubuntu
---

### Post by vsbsc6 on 2013-07-16
I updated ubuntu 12.04 to 12.10 LTS. Then I was unable to load windows 7. There was some disc error to boot the windows. While trying to open c drive ubuntu displayed some problem of hibernation. I succedded to start windows reading an artical for a single time and then I shut it down. Again I tried but the problem of loading windows was not solved though I was able to open C drive in Ubuntu. I had created a file to show windows as first entry in grub. I deleted it. Then the windows 7 was disappered although there is a file named 30_os-prober. Then where is problem? Please answer cosidering me as a new one to linux as well as ubuntu.

---

### Post by su:bhatta on 2013-07-16
Ok, seems like a problem in your Grub.... which i cant help you with...
Just one pointer, Ubuntu 12.10 is not a LTS, actually 12.04 is the LTS, 12.10 is supported for 18 months.... i.e. till 14.04 LTS release.

---

### Post by vsbsc6 on 2013-07-16
I don't know much more about ubuntu. Thanks for your answer.

---

### Post by newb85 on 2013-07-16
Install and run boot-repair.  It should be in the repos for 12.10.

---

### Post by vsbsc6 on 2013-07-16
[http://paste.ubuntu.com/5880977/](http://paste.ubuntu.com/5880977/)

---

### Post by newb85 on 2013-07-16
Partitions 5, 6, and 7 are all listed in the boot info as starting at sector 63.  I don't think that's supposed to be that way.

---

### Post by oldfred on 2013-07-16
You have a copy of 30_os-prober as 06_os-prober which then makes the Windows boot entries first in the grub boot menu. It looks like Boot-Repair made both executeable so now they both run. You should turn one or the other off. Any major updates to grub may add a new 30_os-prober file which then you may want to turn off again if you just want the 06_ version. If 06 version is from a previous older grub you should update it.

Did you every create partitions with Windows and it converted to dynamic partitions? Newest version of grub now tests for LDM data (or dynamic partition) and does not work with that. But you may just have left over meta-data on the drive.
       GRUB2 2.00 recognizes defunct LDM headers from old dynamic partitions
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)

---

