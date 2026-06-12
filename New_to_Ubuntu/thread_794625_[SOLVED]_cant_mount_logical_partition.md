---
title: "[SOLVED] cant mount logical partition"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by stoppage on 2008-05-14
Could somebody please help me mount an extra logical (sda9) partition on my „Feisty“ please? Ive created mount point sda9 in media and added following line to fstab....
# /dev/sda9				   /media/sda9    reiserfs     defaults,umask=007,gid=46           0  1 	 
but when I try to mount in terminal I get..
:~$ sudo mount sda9

mount: can't find sda9 in /etc/fstab or /etc/mtab

even though its clearly visible!
Im on a dual-boot with XP, everything else works and Im slightly baffled here. Obliged

---

### Post by macaholic on 2008-05-14
Someone correct me if I'm wrong, but is if that # sign is really there, it is telling mount to ignore that line, try removing it.
Also, I don't think that entry is formatted correctly, one of mine looks like this```
# /dev/sdb1
UUID=e9838908-74d5-49cf-9dc7-35f032739c8b /               ext3    defaults,errors=remount-ro 0       1

```

---

### Post by stoppage on 2008-05-14
I'd already tried fstab with # sign removed, no difference. Also Ive read somewhere that UUID entry is not necessary. Copy of fstab...
# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc          proc         defaults                            0  0  

# /dev/sda8

UUID=d71bd99f-8839-42ce-add2-331e5c07215b  /              reiserfs     notail                              0  1  

# /dev/sda1

UUID=13DCF6A55EFADC19                      /media/sda1    ntfs         defaults,nls=utf8,umask=007,gid=46  0  1  

# /dev/sda5

UUID=4F73DA99F0DCD0C4                      /media/sda5    ntfs         defaults,nls=utf8,umask=007,gid=46  0  1  

# /dev/sda6

UUID=B2C4ABDA5DF0D5B9                      /media/sda6    ntfs         defaults,nls=utf8,umask=007,gid=46  0  1  

# /dev/sda7

UUID=0c6ff9d6-ce9c-466b-aec5-b9931bc19d2e  none           swap         sw                                  0  0  

/dev/hdc                                   /media/cdrom0  udf,iso9660  user,noauto                         0  0  

/dev/hdd                                   /media/cdrom1  udf,iso9660  user,noauto                         0  0 

/dev/sda9				   /media/sda9    reiserfs     defaults,umask=007,gid=46           0  1

---

### Post by stoppage on 2008-05-16
To solve this, I had to reformat sda9 to EXT3. My fstab entry for this partition is...
/dev/sda9				   /mnt/sda9    ext3         defaults,auto,			   0  1

---

