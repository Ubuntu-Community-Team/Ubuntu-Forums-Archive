---
title: "Filesystem root and efi showns as external HDD in file explorer"
date: 2021-02-18
forum: New to Ubuntu
---

### Post by emilio-11 on 2021-02-18
I've recently noticed that in the file bar/explorer **filesystem root** and **efi** shown as external HDD. It is kind of weird I don't know it does affect the system processes or not. Furthermore, usb drives are not shown up, but I run **lsusb **command i can see that usb drive is connected. Any insight or help are appreciated

---

### Post by yancek on 2021-02-18
How many hard drives do you have attached?
Could you post the output of either/both commands below which will show actual information on the drives?

>  sudo fdisk -l
sudo blkid

How did you attempt to see if USB drives are attached?  Generally, they are available under /media/username.

---

### Post by emilio-11 on 2021-02-18
The output of **fdisk -l**:

> Disk /dev/loop0: 218.102 MiB, 229629952 bytes, 448496 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 97.9 MiB, 102637568 bytes, 200464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 98.36 MiB, 103129088 bytes, 201424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 55.48 MiB, 58159104 bytes, 113592 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 31.9 MiB, 32600064 bytes, 63672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 162.89 MiB, 170778624 bytes, 333552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 51.4 MiB, 53522432 bytes, 104536 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 217.92 MiB, 228478976 bytes, 446248 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: TOSHIBA MQ01ABD1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: EC7C0DD1-5B5C-49CE-8C81-483CDB4FEAB4

Device       Start        End    Sectors  Size Type
/dev/sda1     2048    1050623    1048576  512M EFI System
/dev/sda2  1050624 1953523711 1952473088  931G Linux filesystem




Disk /dev/loop8: 51.2 MiB, 53501952 bytes, 104496 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 64.36 MiB, 67477504 bytes, 131792 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 64.79 MiB, 67915776 bytes, 132648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 31.9 MiB, 32595968 bytes, 63664 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 172.99 MiB, 181366784 bytes, 354232 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 129.10 MiB, 136286208 bytes, 266184 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop14: 149.76 MiB, 157016064 bytes, 306672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop15: 55.39 MiB, 58073088 bytes, 113424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop16: 149.76 MiB, 157016064 bytes, 306672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes



Output of **blkid**:

> /dev/sda2: UUID="f3023789-28b0-4138-b6c8-6c10b8219ca2" TYPE="ext4" PARTUUID="99b4c4fc-3a52-435a-a601-ae10cb06371c"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: UUID="B04C-7CC4" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="ab146d04-bfae-4c6f-8b7f-9d8b3607fcb3"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop16: TYPE="squashfs"
[COLOR=#800000]/dev/sdb1: LABEL="SARDAR" UUID="926B-0C3A" TYPE="vfat" PARTUUID="4668a8dd-01"







[/COLOR]The last highlighted line is the my usb driver name but somehow it does not show up in file explorer. Filesystem root and efi are recognized as external HDD.

---

