---
title: "Ubuntu 12.10 installation gone wrong"
date: 2013-04-01
forum: New to Ubuntu
---

### Post by Nozzilrox on 2013-04-01
So i have this external hard drive that I've been using as a back-up (my old hard drive died) and the last 2 things i did on it before its started giving me an error is: partioned the drive to NTSF and back to ext4, and then tried installing 12.10 ubuntu onto this (now) blank HDD.(but i think somewhere in the installation it screwed up.) Anyway here's the error code:


Error mounting /dev/sda1 at /media/ubuntu/6c0313da-d2a0-4bd9-9b47-78552015d153: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda1" "/media/ubuntu/6c0313da-d2a0-4bd9-9b47-78552015d153"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


please help me asap. IF anyone even gets on this forum.

P.S if you do ur a freaking godsend.
P.P.S This is all im getting when i run dmesg | tail:
[35373.968739] sd 10:0:0:0: >[sda]  
[35373.968742] Sense Key : Illegal Request [current] 
[35373.968747] Info fld=0x0
[35373.968751] sd 10:0:0:0: >[sda]  
[35373.968755] Add. Sense: Logical block address out of range
[35373.968760] sd 10:0:0:0: >[sda] CDB: 
[35373.968762] Write(10): 2a 00 1e 41 09 20 00 00 18 00
[35373.968777] end_request: critical target error, dev sda, sector 507578656
[35373.968804] JBD2: recovery failed
[35373.968812] EXT4-fs (sda1): error loading journal

P.P.P.S im running off a live CD atm. :( this HDD is 500gb. half a TB is wasted.

---

### Post by daslinkard on 2013-04-02
I understand you tried installing to your external HD but have you tried making it a live usb?  Instructions [here]("http://www.upubuntu.com/2012/10/how-to-create-live-usb-for-ubuntu-1210.html").

---

### Post by Nozzilrox on 2013-04-02
I have. i mean i can run a live usb/CD the problem is i cant put anything on my HDD in ubuntu and windows ever since i had a bad reinstall of ubuntu

---

### Post by lisati on 2013-04-02
Please be patient. We are all volunteers here, from multiple time zones. The person who is best equipped to help you might not have seen your thread yet.

---

