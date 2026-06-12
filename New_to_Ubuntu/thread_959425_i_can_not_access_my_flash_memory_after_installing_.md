---
title: "i can not access my flash memory after installing ubuntu from flash"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by eramax on 2008-10-26
hi;

i have a problem in using my usb flash memory ;
this problem occur when installing ubuntu from usb flash only;
after that i can not use my flash and can not mount it and i get the message 
> "Invalid mount option when attempting to mount the volume 'ERAMAX'"

[IMG]http://img204.imageshack.us/img204/5791/ee1rg8.jpg[/IMG]
since ERAMAX is my flash volume;
but if i used terminal to mount it manualy by using this command
> sudo mount /dev/sdb1 /mnt/flash

then i can access my flash for read only Not write ;
so this is my problem 

i have another thing that may help that if i put another usb-flash memory while my flash in computer ,i can access the last usb-flash which will be at /dev/sdb2 because the first one at /dev/sdb1 
so i can access any usb-flashes except the first flash i put which its device will be at /dev/sdb1

my fstab file is :-



```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=e6ff228f-5693-4c36-8f1f-0581b1c0ce7d /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=07f6a11d-8502-430f-92aa-0d71d51856ca none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

thanks;

---

### Post by eramax on 2008-10-27
The problem solved by commenting the line :-
> /dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

