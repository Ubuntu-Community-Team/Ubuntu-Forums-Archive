---
title: "External HD not mounting, what is broken?"
date: 2011-10-07
forum: New to Ubuntu
---

### Post by TanssivaLapanen on 2011-10-07
Hi all!

I have an external USB HD that doesn't respond really to anything. Xubuntu 11.4 doesn't say anything when I plug it in

fdisk -l says the following (sorry, some is in Finnish, as the computer needs also be used by my wife)


> mestapaikka@ruttu-aakkeri:~$ sudo fdisk -l
[sudo] password for mestapaikka: 

Levy /dev/sda: 40.0 Gt, 40007761920 tavua
255 päätä, 63 sektoria/ura, 4864 sylinteriä
Yksiköt = 16065 * 512 = 8225280 -tavuiset sylinterit
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Levyn tunniste: 0x00034bcd

    Laite Käynn     Alku          Loppu    Lohkot   Id  Järjestelmä
/dev/sda1               1         122      975872   82  Linux-sivutus / Solaris
Osion 1 loppu ei ole sylinterin rajalla.
/dev/sda2   *         122        1338     9765888   83  Linux
/dev/sda3            1338        4864    28325889    5  Laajennettu
/dev/sda5            1338        4864    28325888   83  Linuxlsusb doesn't find it either

> mestapaikka@ruttu-aakkeri:~$ lsusb
Bus 005 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0421:0623 Nokia Mobile Phones 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubmount says this:

> mestapaikka@ruttu-aakkeri:~$ mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mestapaikka/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mestapaikka)
/dev/sda5 on /media/a29fdd00-d8cf-4fae-bf6e-ecec72d4725e type ext4 (rw,nosuid,nodev,uhelper=udisks)When I plug this drive to my Win7-laptop, it does want to format this drive, but then says it is not possible. So is there some trick to find out if the disk is broken or something. I can't recall what the filesystem is on this disk, but I think it should be NTFS (might be ext3 also, but can't remember).

I know that my music-collection is on this drive and it would be sad, but no disaster, if it would dissapear.

Thankful for ideas of how to proceed.

Best regards
-Elmo

---

### Post by TeoBigusGeekus on 2011-10-07
Have you tried different usb ports?

---

### Post by thatguruguy on 2011-10-07
It looks like you have a bad controller on your external hard drive, if neither Linux nor Windows can manage it.

---

### Post by Mark Phelps on 2011-10-08
There's nothing in any of the command results indicating this drive was formatted with NTFS, quite the contrary, it looks like it was formatted containing Linux filesystems.

Win7 won't be able to read it because it doesn't understand Linux filesystems.

---

