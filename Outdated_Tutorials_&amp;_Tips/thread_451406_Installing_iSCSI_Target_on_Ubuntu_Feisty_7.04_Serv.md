---
title: "Installing iSCSI Target on Ubuntu Feisty 7.04 Server - From Base Install (VM)"
date: 2007-05-22
forum: Outdated Tutorials &amp; Tips
---

### Post by dfligel on 2007-05-22
**Before we begin:** 

[COLOR="Red"]This procedure is posted as is - no guarantees :)
This was all done in a x86 VMware Virtual Machine w/1 Processor and 256MB RAM
Running a base install of Ubuntu Server 7.04 Fesity Fawn
[/COLOR]


**What you get when you are done:**
A *hopefully* working iSCSI target to point your other machines at, all on one machine.
[B]
Why?[/B]
I needed a quick and dirty remote storage to make a Microsoft Cluster (don't ask - it's secret) and it had to be portable and cheap. And a single VM running a quality free operating system with minimal changes required and self contained was definintely the way to go.

**Assumptions:**
You know your way around the operating system terminal, comfortable with aptitude, fdisk, etc.
You have correctly given your machine an IP Address and the like.

[B]Important Information for iSCSI
[/B]
[LIST]
[*]/etc/ietd.conf - Main Configuartion file
[*]/etc/init.d/iscsi-target - Initialization and Control Script
[*]Listens on port :3260 - Use ```
sudo netstat -antp
``` to check if it is listening after install
[/LIST]

[B]The Procedure
[/B]

Download iscsitarget-0.4.15.tar.gz from [http://iscsitarget.sourceforge.net/](http://iscsitarget.sourceforge.net/) and extract to /usr/local/src with a sudo ```
tar -zxvf -C /usr/local/src
``` then goto /usr/local/src/iscsitarget-0.4.15 which has just been created.
       
From a terminal window
run  ```
sudo aptitude update
```
run  ```
sudo aptitude install openssh-server build-essential libssl-dev make gcc linux-headers-`uname -r` linux-source-2.6.20
```

All the requirements should now be there and we can install the target

run ```
sudo make
```
run ```
sudo make install
``` 

NB: Out the box there is a little flaw! The first line in the init script is a bit special, change as below.
/etc/init.d/iscsi-target and change #!/bin/sh to #!/bin/bash in line 1 

Then you can run ```
sudo /etc/init.d/iscsi-target status
``` and get something that looks like this:
*iSCSI enterprise target is running at pid 3976*

If you don't get this do not despair just run ```
sudo /etc/init.d/iscsi-target restart
``` and then ```
sudo netstat -antp
``` to see if it is running. 
Note: If you have no configure devices you may have issues.

**Creating Block File Devices:**
a.k.a to cheap or lazy to create other drives or would like to make a portable pickup and move single file system.

For ease of use in the example I have used a file block device created as follows
This will create a block file system in the file /iscsifs/public with a size of 2GB or 4k*512000 

```
run sudo mkdir /iscsifs
```
```
run dd if=/dev/zero of=/iscsifs/public bs=4k count=512000
```

Example /etc/ietd.conf to match the Block file created

```
Target iqn.2007-05.public.iscsi:storage1.public
        Lun 0 Path=/iscsifs/public,Type=fileio
        Alias public

```

If you are particularly paranoid you can now do:
```
 sudo /etc/init.d/iscsi-target restart
``` and then ```
sudo netstat -antp
``` to see if it is running.      

[COLOR="Red"]--- WARNING NON-UBUNTU AHEAD---
At this point I hopped on to my Windows Server (again - don't ask) and connected to the "drive" with the Microsoft iSCSI Initiator 2.4. At this point you have a non-initialized, unformatted, "drive" attached to the Windows Machine - configure this is Drive Management or your favourite 3rd party-tool
-------- END NON-UBUNTU --------------
[/COLOR]

VMWARE Notes - Trick for fun and portability.

For portability of the volumes. Shut down the VM create a second scsi VMDK.
In this case the volume is /dev/sdb1 mounted on /iscsifs
Create all the block devices in here and then edit the /etc/ietd.conf file appropriately.

That is all. Good Luck.

---

### Post by jakethecake on 2007-06-04
[FONT="Times New Roman"]I'm [SIZE="3"]trying to make iSCSI and OCFS2 work together. :-)

When it is up and running, then peformance is exellent. I get 95mb-120mb/sek from my raid array locally and about the same via iSCSI mount.

My Setup

```
Feisty Desktop (QUAD)                       Feisty Server (TERRA)
-----------------------------------------------------
Node1 acting as client             Node0 acting as server and client

open-iscsi                                iscsi-target + open-iscsi 
OCFS2                                    2TB OCFS2 disk
iscsi drive mounted                 iscsi drive mounted and also shared.

```
A poweroff/reboot hangs both machines, since open-iscsi and the iscsi-target is unloaded before OCFS2.
anyone know of a fix for that?

If I mount the iscsi drive on Node1(QUAD) before i mount it on Node0(TERRA) then OCFS2 errors out and won't mount the drive:

jake@QUAD:~$ sudo iscsiadm --mode node --targetname iqn.2007-06.se.terra:storage --portal 192.168.1.227 --login
jake@QUAD:~$ sudo mount -U ef45fd5c-600a-4bb7-9334-06e5fd408f73 /media/sdb
jake@QUAD:~$


jake@TERRA:~$ sudo mount -U ef45fd5c-600a-4bb7-9334-06e5fd408f73 /media/sdb
mount.ocfs2: Value too large for defined data type while mounting /dev/disk/by-uuid/ef45fd5c-600a-4bb7-9334-06e5fd408f73 on /media/sdb. Check 'dmesg' for more information on this error.
jake@TERRA:~$ 

jake@TERRA:~$ dmesg 
....
[  919.731817] o2net: accepted connection from node quad (num 1) at 192.168.1.220:7777
[  923.238387] ocfs2_dlm: Nodes in domain ("EF45FD5C600A4BB7933406E5FD408F73"): 0 1 
[  923.239925] kjournald starting.  Commit interval 5 seconds
[  923.240732] (6155,3):ocfs2_broadcast_vote:606 ERROR: status = -75
[  923.240738] (6155,3):ocfs2_do_request_vote:679 ERROR: status = -75
[  923.240743] (6155,3):ocfs2_mount_volume:1125 ERROR: status = -75
[  923.249814] (6155,3):ocfs2_broadcast_vote:606 ERROR: status = -75
[  923.249819] (6155,3):ocfs2_do_request_vote:679 ERROR: status = -75
[  923.249823] (6155,3):ocfs2_dismount_volume:1187 ERROR: status = -75
[  927.276933] ocfs2: Unmounting device (8,32) on (node 0)
[  929.242791] o2net: no longer connected to node quad (num 1) at 192.168.1.220:7777
jake@TERRA:~$

(It works if I mount the iscsi drive on node0 first then on node1.) Anyone seen this behaviour before?


jake@QUAD:~$ ls -la /dev/disk/by-path/
totalt 0
drwxr-xr-x 2 root root 200 2007-06-04 21:04 .
drwxr-xr-x 6 root root 120 2007-06-04 21:04 ..
*lrwxrwxrwx 1 root root   9 2007-06-04 21:04 ip-192.168.1.227:3260-iscsi-iqn.2007-06.se.terra:storage-lun-0 -> ../../sdb*
lrwxrwxrwx 1 root root   9 2007-06-04 21:04 pci-0000:00:0d.0-ide-0:0 -> ../../hda
lrwxrwxrwx 1 root root   9 2007-06-04 23:04 pci-0000:00:0e.0-scsi-0:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root  10 2007-06-04 23:04 pci-0000:00:0e.0-scsi-0:0:0:0-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2007-06-04 23:04 pci-0000:00:0e.0-scsi-0:0:0:0-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2007-06-04 23:04 pci-0000:00:0e.0-scsi-0:0:0:0-part3 -> ../../sda3
lrwxrwxrwx 1 root root  10 2007-06-04 23:04 pci-0000:00:0e.0-scsi-0:0:0:0-part4 -> ../../sda4
lrwxrwxrwx 1 root root  10 2007-06-04 23:04 pci-0000:00:0e.0-scsi-0:0:0:0-part5 -> ../../sda5
jake@QUAD:~$ 


jake@QUAD:~$ sudo hdparm -t /dev/sdb 

/dev/sdb:
 Timing buffered disk reads:  338 MB in  3.04 seconds = 111.12 MB/sec
jake@QUAD:~$[/FONT][/SIZE]

---

### Post by jadfer on 2007-09-26
I followed the directions for editing the file and making the block file.

When I ran the restart command it keeps failing saying connection refused. What could I have done wrong?

Thanks

---

### Post by jadfer on 2007-09-26
Ok I got all the way to the Microsoft Initiator and connected to the host but there are no Luns available. 

I have no idea what to check. Any ideas?

I am pretty sure its in the target config but I dont really know what each part does yet.

any help is needed and appreciated.

Thanks

---

### Post by jakethecake on 2007-09-26
iSCSI kind of works, I think it is broken.

I went ahead with NFS and Samba instead, and added 'data=writeback,noatime 0' to the drive in fstab, to speed it up.

---

