---
title: "LUKS Disk Encryption and External NTFS Drives = Not working"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by TechDragon on 2008-10-15
Apparently you can't plug in an external usb NTFS formatted hard drive to a luks encrypted hard drive.

I have tried,
NTFS-3g
NTFS-3g Config
NTFS-3g tools

AutoFS

Fuse

Pmount

Etc etc etc with no luck

---

### Post by Nxion on 2008-10-17
That is a little strange. I have a virtual machine with Hardy loaded and it is encrypted. I am able to view anything I plug into it weather it be FAT32 or NTFS. Are you sure that the external hard drive is OK? Can you plug it into another machine to verify that it will come up?

---

### Post by bodhi.zazen on 2008-10-17
No, that is not the way to mount a LUKS partition.

You first unlock he crypt if you will :

The basic syntax is :

sudo cryptsetup luksOpen <device> <crypt_name>

You crypt will then be in 
[FONT=monospace]
[/FONT]/dev/mapper/crypt_name

You mount it with

mount /dev/mapper/crypt_name /mount_point

So in your case ...


```
sudo cryptsetup luksOpen /dev/sdb1 crypt_name

sudo mount /dev/mapper/crypt_name /mount_point
```

you will need to change "crypt_name" to the name of your crypt , "/dev/sdb1" to the name of your physical partition, and "/mount_point" to your mount point.

See also :

[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)

[http://www.debuntu.org/how-to-encrypted-partitions-over-lvm-with-luks](http://www.debuntu.org/how-to-encrypted-partitions-over-lvm-with-luks)

[http://www.saout.de/tikiwiki/tiki-index.php?page=EncryptedDeviceUsingLUKS](http://www.saout.de/tikiwiki/tiki-index.php?page=EncryptedDeviceUsingLUKS)

[http://www.saout.de/tikiwiki/tiki-index.php?page=HOWTO](http://www.saout.de/tikiwiki/tiki-index.php?page=HOWTO)

---

### Post by Nxion on 2008-10-17
> **bodhi.zazen said:**
> No, that is not the way to mount a LUKS partition.

You first unlock he crypt if you will :

The basic syntax is :

sudo cryptsetup luksOpen <device> <crypt_name>

You crypt will then be in 
[FONT=monospace]
[/FONT]/dev/mapper/crypt_name

You mount it with

mount /dev/mapper/crypt_name /mount_point

So in your case ...


```
sudo cryptsetup luksOpen /dev/sdb1 crypt_name

sudo mount /dev/mapper/crypt_name /mount_point
```you will need to change "crypt_name" to the name of your crypt , "/dev/sdb1" to the name of your physical partition, and "/mount_point" to your mount point.

See also :

[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)

[http://www.debuntu.org/how-to-encrypted-partitions-over-lvm-with-luks](http://www.debuntu.org/how-to-encrypted-partitions-over-lvm-with-luks)

[http://www.saout.de/tikiwiki/tiki-index.php?page=EncryptedDeviceUsingLUKS](http://www.saout.de/tikiwiki/tiki-index.php?page=EncryptedDeviceUsingLUKS)

[http://www.saout.de/tikiwiki/tiki-index.php?page=HOWTO](http://www.saout.de/tikiwiki/tiki-index.php?page=HOWTO)

Learn something new everyday :)

---

