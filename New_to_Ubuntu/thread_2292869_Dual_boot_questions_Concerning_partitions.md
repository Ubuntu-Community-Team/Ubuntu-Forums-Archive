---
title: "Dual boot questions: Concerning partitions"
date: 2015-08-31
forum: New to Ubuntu
---

### Post by Boyntonstu on 2015-08-31
**Dual boot questions:** [SIZE=1][/SIZE]             
            
        
         2 partitions:  Win 8.1 and Ubuntu 
 
1>  Can  I access and save files from one OS partition to the other? 
 
2> Must I use a USB hard drive for each OS?

---

### Post by yetimon_64 on 2015-08-31
1. From Windows to Ubuntu, no. From Ubuntu to Windows, yes. Though it is not a good idea to use Ubuntu to write to the Windows OS partition as it is possible to corrupt the Win OS doing so. It is usually recommended to have a separate shared NTFS data partition for both systems to write to.

2. No. Though I am wondering why a USB hard drive is even being mentioned here. 
Most dual-booters just partition an internal HDD and install both systems; or sometimes use 2 separate internal drives, one for each separate OS with Grub installed to the first drive to boot both systems.

---

### Post by yancek on 2015-08-31
> 
Can  I access and save files from one OS partition to the other? 

You can access windows directories/files from Linux and this should be available by default.  You cannot access Linux partitions from windows without downloading and installing third party software.

> Must I use a USB hard drive for each OS?         

No.  You can install pretty much and Linux system on a usb drive.  If you try to install windows on a usb drive you will likely see this message:

>  "windows setup does not support configuration or installation to a disk connected through usb or IEEE 1394 ports

You can have data partitions for windows on a usb.

---

### Post by Boyntonstu on 2015-08-31
I have a 1TB backup USB drive H: on win 8.1.

If I dual boot, will the H: drive be visible in Ubuntu?

---

### Post by yetimon_64 on 2015-08-31
It won't be called "H" drive in ubuntu but it will be available and most likely automatically mounted being an external USB drive. Basically, yes it will be available.

---

