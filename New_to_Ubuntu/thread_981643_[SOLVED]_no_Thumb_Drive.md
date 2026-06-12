---
title: "[SOLVED] no Thumb Drive"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by johnhouk on 2008-11-13
My thumb drive dosnt seem to be detected to be automounted

---

### Post by Crafty Kisses on 2008-11-13
See if you can mount it from a terminal:
```
sudo mkdir /media/thumbdrive
sudo mount -t ntfs-3g /dev/sdc1 /media/thumbdrive
```
I'm just assuming your USB thumbdrive is **/dev/sdc1** and that's it's **NTFS**.

---

### Post by johnhouk on 2008-11-13
First command return no error

john@ubuntu:~$ sudo mount -t ntfs-3g /dev/sdc1 /media/thumbdrive
ntfs-3g: Failed to access volume '/dev/sdc1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.

---

### Post by johnhouk on 2008-11-14
.

---

### Post by bennachie on 2008-11-14
The thumb drive is more likely to have been formatted as FAT32, unless the owner has specifically reformatted it under Windows.

---

### Post by epswinde on 2008-11-14
Please post the output of the command
```
sudo fdisk -l
```

---

### Post by johnhouk on 2008-11-14
sorry 1st day ubuntu user, does lunix not support fat&fat32?
is that why it sees my large thumb drive.
the one i cant access is a 64mb i bought with preinstalled form filling software Roboform. I'm guessing i need a windows machine to copy the stuff off, reformat it to ntfs, then copy it back on?

---

### Post by epswinde on 2008-11-14
Linux does indeed support fat32.  It may not need to be formatted.  Some older usb drives might not automount (I have one that doesn't for some reason, in any distro i've tried it with.)  post the output of the command I listed above -- Codename was right on with the command, but may be using the wrong device/file system for your case, and fdisk -l will tell you what to change.

---

### Post by johnhouk on 2008-11-14
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb623b623

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4676    37559938+  83  Linux
/dev/sda2            4677        4864     1510110    5  Extended
/dev/sda5            4677        4864     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 4059 MB, 4059561984 bytes
229 heads, 32 sectors/track, 1081 cylinders
Units = cylinders of 7328 * 512 = 3751936 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1082     3964400    b  W95 FAT32

---

### Post by johnhouk on 2008-11-14
oh wait wrong thumb drive

---

### Post by johnhouk on 2008-11-14
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb623b623

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4676    37559938+  83  Linux
/dev/sda2            4677        4864     1510110    5  Extended
/dev/sda5            4677        4864     1510078+  82  Linux swap / Solaris

---

### Post by johnhouk on 2008-11-14
i think the drive is bad i couldn't get windows to do a full format, only a quick format.

---

### Post by epswinde on 2008-11-14
Yeah, that might be the case.  Post the output to 
```
lsusb
```

The system might not be picking it up at all, which means it could be something wrong with the connector, or the drive at all.

---

### Post by johnhouk on 2008-11-14
Yea i got the files transfered over to the drive that does automount. Unfortunatly the portable win32 apps run at a crawl. i'm using portable firefox & pass2go (portable roboform) I'm going to see if firefoxs new native password abilitys can do the job of roboform. I don't think firefox will remember your credit card info and such. And im just gonna forget about portable firefox on this machine, i can sync the bookmarks easily enough.

---

### Post by johnhouk on 2008-11-15
Yea bad thumb drive.
Case closed.
Feel free to delete this usless tread. Unless these motions could be usefull for someone else.

---

