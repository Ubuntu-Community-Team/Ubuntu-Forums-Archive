---
title: "what is the best way to format flash drive?"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by 007casper on 2012-03-14
The flashdrive was corrupted or something.  I couldnt access it at all.  So, I decided to reformat it.  

so I followed this link
[http://www.linuxforums.org/forum/miscellaneous/122254-solved-cant-remove-files-usb-flashdrive.html](http://www.linuxforums.org/forum/miscellaneous/122254-solved-cant-remove-files-usb-flashdrive.html)

then 
```

dd if=/dev/zero of=/dev/sdb1
```

then try to format it without any luck.

I used gparted and tried to format it to fat16 without any success.  Then tried fat32 without success.  NTFS doesnt work either.  So, I format it to ext4 file format.  Now the permissions for flash disk is root.  I cant chown.

What is the best way to format the flash drive from the terminal?

fdisk -l

```
Disk /dev/sdb: 8011 MB, 8011120640 bytes
255 heads, 63 sectors/track, 973 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d71f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         973     7815591   83  Linux
```

---

### Post by 007casper on 2012-03-14
I did have some good luck
```

chown user:group FLASHDRIVE

```

that allowed me to use it as a regular user.  However, if I mounted the flashdrive to PC, it asked me to format the flashdrive.

So, I reformatted the flashdrive to fat32, then back to kubuntu and it works.  I checked on gparted it does show as fat32.  

I wonder ~ why I couldnt formated as fat32 on gparted on kubuntu?

---

### Post by kurt18947 on 2012-03-14
> **007casper said:**
> I did have some good luck
```

chown user:group FLASHDRIVE

```that allowed me to use it as a regular user.  However, if I mounted the flashdrive to PC, it asked me to format the flashdrive.

So, I reformatted the flashdrive to fat32, then back to kubuntu and it works.  I checked on gparted it does show as fat32.  

I wonder ~ why I couldnt formated as fat32 on gparted on kubuntu?

I don't know the answer to your question but have seen the same thing.  Using gparted to format a flash drive to fat32 will create a device that works with *nix but is not recognized by Windows for whatever reason. Live USBs created on flash drives formatted with gparted won't boot on some systems as well.  Some systems will boot a flash drive formatted fat32 with gparted, others will display an boot error message.

---

### Post by mastablasta on 2012-03-14
what is the solution then? to use format.exe via wine or dosbox? :-D

---

