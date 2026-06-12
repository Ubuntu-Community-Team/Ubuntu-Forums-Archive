---
title: "[SOLVED] sound card and hard drive intermittently inaccessible"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by fr.theo on 2008-08-26
Hello All,

it is I your troubled ubuntu user, 


I have a problem, on occasion i find that my sound card does not work under certain applications e.g. KXMAME, but unbuntu initial start up the sound works and media player also works but other application do not. Rebooting occasionally fixes this problem but it takes several boots to regain the use of my sound under these applications.

my hard drives "I have more than one" seems to deny me access at times and i require to reboot in order to gain access once again, but this does not always work. The message i receive is "you are not privileged to access this drive" i might not be born privileged but i should be able to access my own drive.

I have tried to modify my account to root privileges that i may try to overcome this problem but i cannot, it still wont grant me access.

any thoughts as to why any help would be much appreciated.

Kind Regards

Theodore.

---

### Post by stevereef on 2008-08-26
I also have 5 hard drives on Ubuntu; I just loaded Ubuntu 8.04 and I too can't access the drives... These drive on information on them and I'll new to Ubuntu.

Steve..

---

### Post by fr.theo on 2008-08-26
i have been having this problem for a while now, i have tried to keep my ubuntu updated but the problem still persists.

---

### Post by thomasyen on 2008-08-26
Could you list the contents of /etc/fstab?

---

### Post by fr.theo on 2008-08-26
thanks for your help, I am not sure how to present this properly but here is the /ETC/fstab file you requested.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d6bf02e0-6cda-46f2-b1f6-b9842a921d5d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=731bca13-8e71-494e-919f-06cf4d9d3e0a /boot           ext3    relatime        0       2
# /dev/sda4
UUID=75a36a79-302d-4a4b-9b15-39b815057813 /tmp            ext3    relatime        0       2
# /dev/sda2
UUID=4798ce8b-2ac4-4267-9a64-9336664258a9 none            swap    sw              0       0
# /dev/sdb3
UUID=1bf2c5b9-1c1d-4384-8398-d7a07af97ba7 none            swap    sw              0       0
/dev/sdc1       /media/WD5000 ntfs-3g force 0 0
/dev/sdc1       /media/WD5000 
/dev/sde1       /media/NEXTSTAR3 nrfs-3g force 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       
```

---

### Post by thomasyen on 2008-08-27
Have you tried mounting the disks from the terminal?
```

sudo mount /dev/*XXX* /media/*XXX*

```
Replace XXX with the disk you're trying to mount, e.g. sda1
Also, what exactly do you mean by "giving yourself root privileges"?

---

### Post by fr.theo on 2008-09-20
to thomasyen, thanks for the help i have tried but with no luck still cannot gain access to my Hard Drives.


What i meant by root privileges is that i have the administration rights in Ubuntu to change or modify or access any thing I need without the need of a password or any other kind of permission. 


Still having trouble gaining access to my Hard Drives.

---

### Post by fr.theo on 2008-09-20
Hello all,

I still cant get my Hard Disk Drives to work although I try to mount them within ubuntu i am either told that "i do not have privileges to mount" or nothing happens at all can any one help me?

---

### Post by fr.theo on 2008-09-23
Please help, every time i reboot some of my drives either won't mount or will not allow me to mount them this is frustrating.  

[PHP][
[6:0:0:0]    disk    ATA      WDC WD3200KS-00P 21.0  /dev/sdc
[6:0:1:0]    cd/dvd  PIONEER  DVD-RW  DVR-212  1.21  /dev/scd0
[8:0:0:0]    disk    ATA      WDC WD5000AAKS-0 12.0  /dev/sde
[9:0:0:0]    disk    ATA      WDC WD5000AAKS-2 12.0  /dev/sdf
[/PHP]

i have tried to mount them in terminal but with no luck, it keeps on telling me that the device can not be found in either "fstab" or "mtab" files. any help.

---

### Post by fr.theo on 2008-10-19
I have solved my Sound card problem, it seems that my volume settings were reset or changed during my attempt to install software and get my network working, all I did was raise my volume controls back up so that i would hear my long on sound and the sounds in which applications also stopped working now work.

I am using Ubuntu Hardy LTS 64 bit version

Just encase any one reads this.

---

