---
title: "[ubuntu] Windows won't run alongside Ubuntu"
date: 2014-10-28
forum: New to Ubuntu
---

### Post by flex567 on 2014-10-28
I used this method to change partition type for an USB key [http://askubuntu.com/questions/149984/formatting-usb-flash-memory-for-ubuntu-ext4](http://askubuntu.com/questions/149984/formatting-usb-flash-memory-for-ubuntu-ext4) and today Win7 won't start. I get this error message. Is there a way for me to get into Win7?   [IMG]http://i60.tinypic.com/msdt6t.jpg[/IMG]

---

### Post by Alireza_Zamani on 2014-10-28
Do you have installed Linux after Windows ?

---

### Post by flex567 on 2014-10-28
yes, I first had Win7 and than installed Ubuntu14.04

---

### Post by Alireza_Zamani on 2014-10-28
and in different partition ?

---

### Post by flex567 on 2014-10-28
I belive so, I didn't change anything when I installed Ubuntu so everythin installed with default settings.

---

### Post by Alireza_Zamani on 2014-10-28
i don't understand ...
you need create different partition with Ext4 File System and then install Ubuntu on that partition.

---

### Post by flex567 on 2014-10-28
No I wanted to change the type of the partition on an USB drive. I had Ubuntu and Win7 already installed. I would like to get into Win7 OS and cannot due to the error above.

---

### Post by Alireza_Zamani on 2014-10-28
Where Ubuntu and Win 7 [COLOR=#000000]is installed [/COLOR]? 
on USB Flash ? Hard Drive ? ...

---

### Post by flex567 on 2014-10-28
On Hard drive.

usb key is empty

---

### Post by Impavidus on 2014-10-28
On Linux, run these commands and show us the output:```
sudo parted -l
sudo blkid
```These will show the partitions present on your drives.

---

### Post by flex567 on 2014-10-28
sudo parted -l

```

Model: ATA WDC WD10EZRX-00L (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  815GB   815GB   primary   ntfs            boot
 2      815GB   1000GB  185GB   extended
 6      815GB   996GB   181GB   logical   ext4
 5      996GB   1000GB  4174MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label  

```

sudo blkid

```

/dev/sr0: LABEL="UDF Volume" TYPE="udf" 
/dev/sda1: LABEL="New Volume" UUID="B604B3BB04B37D45" TYPE="ntfs" 
/dev/sda5: UUID="bcd2a988-fcf5-45ad-9a8b-9d8645acc189" TYPE="swap" 
/dev/sda6: UUID="ba19641f-631c-499f-a3ff-69fb6dc0d588" TYPE="ext4"

```

I tried Win7 DVD - system repair wtih no success

---

### Post by LostFarmer on 2014-10-29
If you have not yet got it fixed.  That error with 'invalid signature'  likely can be fixed by running 'testdisk' . first read [http://www.cgsecurity.org/wiki/Running_TestDisk](http://www.cgsecurity.org/wiki/Running_TestDisk)

about the 4th testdisk window, select advance option and highlight the MS partition then at bottom select 'boot' . see  [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

---

