---
title: "partition doesn't mount when restart"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by hubiedo on 2008-10-21
unbuntu 8.

i have a partition /bulin (sdc8) that doesn't mount when restart. i have edited fstab and used blkid to get the uuid. no luck sdc8 was originally smaller and a lot of unallocated space. i redid it by moving data to another partition then deleted it then resized it to full space available.

any help or suggestions appreciated.
hubert

hjk@hjk-linux:~$ sudo blkid
[sudo] password for hjk: 
/dev/sda1: UUID="5A4880B948809603" TYPE="ntfs" LABEL="WIN2K" 
/dev/sda5: LABEL="APPL" UUID="4765-ADED" TYPE="vfat" 
/dev/sda6: LABEL="DOS_BU" UUID="8ECB-5BDE" TYPE="vfat" 
/dev/sda7: UUID="B33605D1872683E9" LABEL="APPL2" TYPE="ntfs" 
/dev/sdb5: UUID="14171E23F0E4F829" LABEL="BIGDISK" TYPE="ntfs" 
/dev/sdc1: UUID="937e2f3b-82a4-4890-aeca-1686c106c50f" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdc2: TYPE="swap" UUID="a8302613-3392-4ec2-9d43-5724a7e73b78" 
/dev/sdc3: UUID="66e6abb9-66cf-4060-b506-5d5b4ede7985" TYPE="ext3" 
/dev/sdc5: UUID="0957cf0a-e821-447d-9d30-12cb907bea86" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdc6: UUID="bf59b4a0-94c8-4ff5-8fb2-d65992f71603" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdc7: UUID="4a21a0ba-18a1-44fb-b65b-1ea7230217df" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdc8: UUID="90b1d6bf-b8c8-4471-8549-58d1cfa30734" SEC_TYPE="ext2" TYPE="ext3" 

hjk@hjk-linux:/etc$ more fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc3
UUID=66e6abb9-66cf-4060-b506-5d5b4ede7985 /               ext3    relatime,error
s=remount-ro 0       1
# /dev/sdc6
UUID=bf59b4a0-94c8-4ff5-8fb2-d65992f71603 /appl           ext3    relatime      
  0       2
# /dev/sdc1
UUID=937e2f3b-82a4-4890-aeca-1686c106c50f /boot           ext3    relatime      
  0       2
# /dev/sdc8
#UUID=dc8243b7-e1e9-4953-bd4e-7e0b9fce7ebf /bulin          ext3    relatime     
   0       2
UUID=90b1d6bf-b8c8-4471-8549-58d1cfa30734	/bulin		ext3	realtime
	0	2	
# /dev/sdc5
UUID=0957cf0a-e821-447d-9d30-12cb907bea86 /home           ext3    relatime      
  0       2
# /dev/sdc7
UUID=4a21a0ba-18a1-44fb-b65b-1ea7230217df /u              ext3    relatime      
  0       2
# /dev/sdc2
UUID=a8302613-3392-4ec2-9d43-5724a7e73b78 none            swap    sw            
  0       0
# orig config below
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# UBUNTU CONFIG TO ALLOW ALL USERS TO MOUNT FD0
/dev/fd0        /media/floppy0  auto rw,users,noauto,fmask=111,dmask=000  0   0

---

### Post by Duck2006 on 2008-10-21
For mounting linux partitions.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

For mounting windoze partitions.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

