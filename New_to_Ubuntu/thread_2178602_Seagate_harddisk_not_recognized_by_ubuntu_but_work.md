---
title: "Seagate harddisk not recognized by ubuntu but working fine in windows"
date: 2013-10-04
forum: New to Ubuntu
---

### Post by Surya_Pratap_Singh on 2013-10-04
Hello,the problem I am facing is with my Seagate Backup plus portable drive....I have two hard disks of same model..One harddisk is working fine,gets auto mounted and doing good in all functioning..


But problem is with my second harddrive..I have tried all forum discussions ,but nothing works...
```


root@bt:~# mount -t ntfs /dev/sdb /


Error opening '/dev/sdb': No medium found
Failed to mount '/dev/sdb': No medium found





```

fdisk -l is only showing my internal drive while my drive is connected.. 
```


root@bt:~# fdisk -l


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x80d2f3ee


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          45      358400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              45        9184    73408512    7  HPFS/NTFS
/dev/sda3            9184       22239   104865792    7  HPFS/NTFS
/dev/sda4           22240       38913   133932447    f  W95 Ext'd (LBA)
/dev/sda5           22240       32683    83891398+   7  HPFS/NTFS
/dev/sda6           32684       38913    50041016   83  Linux

```





lsusb is showing presence of my hardisk  (i.e.   Bus 002 Device 018: ID 0bc2:a003 Seagate RSS LLC   )


```
root@bt:~# lsusb


Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:231d Hewlett-Packard 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 018: ID 0bc2:a003 Seagate RSS LLC 
Bus 002 Device 004: ID 04f2:b159 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```







I checked my log messages ,and result was this-->


```
root@bt:~# sudo tail -f /var/log/messages
Oct  4 15:39:15 bt kernel: [ 6006.930463] sd 16:0:0:0: [sdc] Synchronizing SCSI cache
Oct  4 15:39:15 bt kernel: [ 6006.930511] sd 16:0:0:0: [sdc]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Oct  4 15:39:23 bt kernel: [ 6014.576110] usb 2-3: new high-speed USB device number 18 using ehci_hcd
Oct  4 15:39:23 bt kernel: [ 6014.723307] scsi17 : uas
Oct  4 15:39:44 bt kernel: [ 6035.872094] scsi 17:0:0:0: uas_eh_abort_handler tag -1
Oct  4 15:39:44 bt kernel: [ 6035.872111] scsi 17:0:0:0: uas_eh_device_reset_handler tag -1
Oct  4 15:39:44 bt kernel: [ 6035.872119] scsi 17:0:0:0: uas_eh_target_reset_handler tag -1
Oct  4 15:39:44 bt kernel: [ 6035.872127] scsi 17:0:0:0: uas_eh_bus_reset_handler tag -1
Oct  4 15:39:44 bt kernel: [ 6035.984119] usb 2-3: reset high-speed USB device number 18 using ehci_hcd
Oct  4 15:39:44 bt kernel: [ 6036.117373] scsi 17:0:0:0: Device offlined - not ready after error recovery
```




Please help me out...Thanx in advance...

---

### Post by Mark Phelps on 2013-10-04
Linux won't mount NTFS volumes if it suspects filesystem corruption, so the first thing you should do is connect it when running Windows and run CHKDSK on it.

---

### Post by Surya_Pratap_Singh on 2013-10-04
No problem detected in Windows CHKDSK..
works all good

---

### Post by whitesmith on 2013-10-04
Connect it to another computer and see if it works there.

---

### Post by Surya_Pratap_Singh on 2013-10-04
checked out...similar problem...
i have another same harddisk and that is working fine...

---

### Post by whitesmith on 2013-10-04
If it fails similarly on another computer then something is bad: drive, housing, cable, etc.

---

### Post by Surya_Pratap_Singh on 2013-10-04
but its working good in windows...

---

### Post by rburkartjo on 2013-10-04
had the same problem years ago and never could get it to work. i ended up returning.

---

### Post by whitesmith on 2013-10-04
Then it's formatting. Connect it to your Linux computer and--assuming there's nothing valuable on it--see if the Disks utility recognizes it. If it does, format it as ext3 or 4. Also make sure it is FAT (file allocation table). Windows uses different schemes today (like GUID) and that could be the issue. FAT is what you want.

---

