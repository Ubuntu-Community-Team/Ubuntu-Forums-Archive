---
title: "Ubuntu start up not detecting windows"
date: 2015-08-25
forum: New to Ubuntu
---

### Post by gaddam_suneel_kuma on 2015-08-25
Hi ,

i am not able to boot into windows even after using boot repair tool to dual boot.
Plese help me how to proceed
 
Here i am attaching the boot-repair log
[http://paste.ubuntu.com/12192824/](http://paste.ubuntu.com/12192824/)

---

### Post by drohhyn2 on 2015-08-25
But you still have access to ubuntu?

I had a similar issue some days ago (when upgrading/installing windows 10 in a dual boot environment). I had to fix the windows installation with fixmbr etc and after that rebooting from a linux live usb stick and do the boot repair.

---

### Post by gaddam_suneel_kuma on 2015-08-25
No actually i don't have access to Ubuntu. I performed the boot repair with live usb stick, as i am unable to boot to windows installation to perform any tasks in windows.

---

### Post by deadflowr on 2015-08-25
> **gaddam_suneel_kuma said:**
> No actually i don't have access to Ubuntu. I performed the boot repair with live usb stick, as i am unable to boot to windows installation to perform any tasks in windows.

So, you can't access either system?

---

### Post by yancek on 2015-08-25
The boot repair info looks correct for Ubuntu, Grub in the mbr with the core.img file where it should be and entries for it pointing to the correct partition and using the correct UUID.  What exactly happens when you select Ubuntu to boot?  You're using the older MBR boot so it should boot.  You can't boot windows because there is no entry in the grub.cfg menu so what you need to do is post info on what happens when you try to boot into Ubuntu and someone may have a suggestion.  Once you do that, you should be able to run:  sudo update-grub and get a windows entry.

---

