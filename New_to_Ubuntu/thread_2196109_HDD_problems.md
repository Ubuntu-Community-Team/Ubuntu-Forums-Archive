---
title: "HDD problems"
date: 2013-12-27
forum: New to Ubuntu
---

### Post by harvey.barnett on 2013-12-27
Hi all, I have recently developed a problem, making my HDD unreadable. It all started when one of my laptops DC port broke, as it was going to be a while before I fixed it I went and bought a 2.5'' external enclosure with the intent of using the drive as a boot drive on an identical laptop (Acer 5332 if anyones interested). Everything was working fine, I was using the external drive with ubuntu on and then the next day when I try to boot from it I get this just after the bios screen:
[B]error: attempt to read or write outside of disk 'hd0'.
error: attempt to read or write outside of disk 'hd0'.
error: terminal 'gfxterm' isn't found.[/B]
As there are some recent pictures on the drive that I hadn't recently backed-up I then changed the boot order and boot windows 7 on the other HDD. When I plugged in the external drive the drivers  installed but the drive was not recognised in windows so I done some googleing and tryed to assign a drive letter in disk management but I couldn't, apparently as linux file systems are different as I later found out. Getting desperate now I found my ubuntu usb, installed ubuntu to a 500gb 3.5'' HDD and tryed to access the drive, listed as 157GB filesystem and got the error:
[B]Unable to mount 157GB filesystem
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/B]
I am at a loss now, all I need to do is access the files on the drive to copy them to usb. Can anyone help ?
Thanks in advance,
Harvey.

---

### Post by sandyd on 2013-12-27
> **harvey.barnett said:**
> Hi all, I have recently developed a problem, making my HDD unreadable. It all started when one of my laptops DC port broke, as it was going to be a while before I fixed it I went and bought a 2.5'' external enclosure with the intent of using the drive as a boot drive on an identical laptop (Acer 5332 if anyones interested). Everything was working fine, I was using the external drive with ubuntu on and then the next day when I try to boot from it I get this just after the bios screen:
[B]error: attempt to read or write outside of disk 'hd0'.
error: attempt to read or write outside of disk 'hd0'.
error: terminal 'gfxterm' isn't found.[/B]
As there are some recent pictures on the drive that I hadn't recently backed-up I then changed the boot order and boot windows 7 on the other HDD. When I plugged in the external drive the drivers  installed but the drive was not recognised in windows so I done some googleing and tryed to assign a drive letter in disk management but I couldn't, apparently as linux file systems are different as I later found out. Getting desperate now I found my ubuntu usb, installed ubuntu to a 500gb 3.5'' HDD and tryed to access the drive, listed as 157GB filesystem and got the error:
[B]Unable to mount 157GB filesystem
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/B]
I am at a loss now, all I need to do is access the files on the drive to copy them to usb. Can anyone help ?
Thanks in advance,
Harvey.

The first error is because of grub - normally, grub denotes your first HDD as hd0, then hd1, and so on. Grub, as a result, thinks this is still an internal drive and boots from that laptop's internal drive instead of the external one where the Ubuntu install is.

For the second error, can you post the output of the Boot Info Script?
```

wget http://softlayer-ams.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.61/bootinfoscript-061.tar.gz
tar xvf bootinfoscript-061.tar.gz
./bootinfoscript
```

Thanks.

---

### Post by plurga on 2013-12-28
hi 

1.-Try boot from live DVD or USB ,then run sudo e2fsck /dev/root_partition.After that check if the issue was resolved.
2.- have u tried use boot-rapair ??  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

3.-most of the linux-users redirect to this link  bcs this helped them to resolve the issue same like u. may be it can help u 
   [http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/boot-problem-after-installing-ubuntu-11-04-kernel-panic-not-syncing-vfs-919143/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/boot-problem-after-installing-ubuntu-11-04-kernel-panic-not-syncing-vfs-919143/)

thanks.

---

### Post by harvey.barnett on 2013-12-28
The first error still occurs when only the drive is inside the laptop. I am just trying the boot repair now and if that doesn't work I'll post the Boot Info Script and then try to run sudo e2fsck /dev/root_partition. Thanks for the quick replies guys :p

---

