---
title: "Recovering Brick WD World Book ---- Newbie"
date: 2015-12-14
forum: New to Ubuntu
---

### Post by simonong on 2015-12-14
hi:
   I am trying to recover data from Western Digital World Book (2 TB Caviar Green) hard like using Ubuntu boot with USB memory stick.

this is what i had been doing (googling around)
ubuntu@ubuntu:~$ sudo mdadm --examine --scan
ARRAY /dev/md0 UUID=*********************************************  
ARRAY /dev/md1 UUID=1111111111111111111111111111111
ARRAY /dev/md126 UUID=111111111111111111111111111
ARRAY /dev/md127 UUID=111111111111111111111111111111111

ubuntu@ubuntu:~$ sudo mount /dev/md0 /mnt
mount: special device /dev/md0 does not exist
ubuntu@ubuntu:~$ sudo mount /dev/md1 /mnt
mount: special device /dev/md1 does not exist
ubuntu@ubuntu:~$ sudo mount /dev/md126/mnt
mount: can't find /dev/md126/mnt in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount /dev/md126 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/md126,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount /dev/md127 /mnt
mount: Structure needs cleaning


I am new to ubuntu and linux. Can some someone guide me ?

Thanks

---

