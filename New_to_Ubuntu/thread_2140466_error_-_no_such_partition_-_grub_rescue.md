---
title: "error - no such partition - grub rescue"
date: 2013-04-29
forum: New to Ubuntu
---

### Post by goslings on 2013-04-29
Thought I would upgrade to 12.04 on my dual boot (xp) medion netbook.
Tried through update manager - which suggested 12.04 
But this failed due to lack of space.
So backed out of this and elected to delete partition with 11.04 Ubuntu and reinstall through windows installer (12Gb) selected.
All reported ok when installed finished 

but when asked on reboot I get 
error: no such partition - grub rescue>
anything I type returns an error 
except ls 
(hdo) (hd0,2) (hd0,1) (fd0)

expect windows intact but (there is a recovery drive uder windows) ..... but this device has no CD/DVD drive.

Can anyone suggest how I can resurrect back to windows / Ubuntu 

thanks
IanS

---

### Post by goslings on 2013-04-29
see my sig is out of date ... medion netbook 1Gb ram 80Gb hard drive - win xp & Ubuntu 11.04 (broke)

---

### Post by oldfred on 2013-04-29
When you uninstall a Linux partitioned install, you have to change to the Windows boot loader. Best to do before you delete Ubuntu, but easy to do with LiveCD.
Without liveCD can you boot flash drive? Or else you have to remove drive and install into some system where you can make repairs.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by goslings on 2013-04-30
Thanks
 I will try at the weekend with usb option
Regards
Ian

---

### Post by goslings on 2013-05-04
I used 10.04 pendrivelinux.com to generate a 10.04 USB (this version said it includes the boot-repair)
Sadly ...It did not ...
so had to follow [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
following 2nd option.

Had to switch on WIFI through Fn-F11 and disable & re-enable wfi for it to find my router ( I remember many lost night with Broadcom & Ububtu)
Thankfully my old Medion Netbook E1210 does not have this.

Auto fixed the problem, it now dual boot to Win XP & Ubuntu 

Many thanks 
IanS

---

