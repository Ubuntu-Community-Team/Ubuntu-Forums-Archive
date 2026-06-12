---
title: "How to force format a USB device?"
date: 2012-07-21
forum: New to Ubuntu
---

### Post by manuganji on 2012-07-21
Hi, my USB says it's write protected when I try to format it. Is there a way to force format it?

It's a Sandisk Cruzer 8 GB drive with USB 2.0.

---

### Post by NikTh on 2012-07-21
> **manuganji said:**
> Hi, my USB says it's write protected when I try to format it. Is there a way to force format it?

It's a Sandisk Cruzer 8 GB drive with USB 2.0.

Hi , 
Do you have windows ? if yes , then plugin the Usb stick and [U]immediately
[/U]right click and "Quick Format". 
This is one solution, as i assume that window's not properly disconnect of Usb-stick, is responsible for this. 

Or (from Ubuntu)
you can try to correct filesystem with **fsck** tool.

Plug in your usb-stick and open a terminal 
First give this command ```
sudo fdisk -l
``` to see what is the dev name of the partition. 
**We assume that is /dev/sdb1 **
From terminal write ```
sudo umount /dev/sdb1 
sudo fsck.vfat -f -p /dev/sdb1
```Thanks

---

### Post by gnusci on 2012-07-21
Try with: palimpsest

---

### Post by manuganji on 2012-07-21
Thanks for the quick replies. I tried formatting with disk utility. It failed with this error.
> Error creating partition table: helper exited with exit code 1: cannot open /dev/sdb: Read-only file system

Tried the steps given by NikTh. This is what happened.

> manu@manu-Inspiron-N5010:~$ sudo fdisk -l
[sudo] password for manu: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7429fb3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      258047      128000   de  Dell Utility
/dev/sda2   *      258048    20004863     9873408    7  HPFS/NTFS/exFAT
/dev/sda3        20004864    84598783    32296960    7  HPFS/NTFS/exFAT
/dev/sda4        84600830   625141759   270270465    5  Extended
/dev/sda5        84600832   294389759   104894464    7  HPFS/NTFS/exFAT
/dev/sda6       294391808   479733759    92670976    7  HPFS/NTFS/exFAT
/dev/sda7       479735808   582676479    51470336    7  HPFS/NTFS/exFAT
/dev/sda8       582678528   613224447    15272960   83  Linux
/dev/sda9       613226496   625141759     5957632   82  Linux swap / Solaris

Disk /dev/sdb: 8004 MB, 8004304896 bytes
247 heads, 62 sectors/track, 1020 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a9ca0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              62    15620279     7810109    c  W95 FAT32 (LBA)
manu@manu-Inspiron-N5010:~$ umount /dev/sdb1
manu@manu-Inspiron-N5010:~$ fsck.vfat -f -p /dev/sdb1
dosfsck 3.0.12, 29 Oct 2011, FAT32, LFN
open: Permission denied
manu@manu-Inspiron-N5010:~$ sudo fsck.vfat -f -p /dev/sdb1
dosfsck 3.0.12, 29 Oct 2011, FAT32, LFN
open: Read-only file system
manu@manu-Inspiron-N5010:~$ 


---

### Post by NikTh on 2012-07-21
Hi , 
please try these commands again , and give the results 
```
sudo umount /dev/sdb1 
sudo fsck.vfat -f -v /dev/sdb1
``` 
Thanks

---

### Post by manuganji on 2012-07-21
Hi NikTh, these is the output I got. I didn't know which option to choose at that prompt to select 'which FAT?'. So, I tried both the options.

> manu@manu-Inspiron-N5010:~$ sudo fsck.vfat -f -v /dev/sdb1
dosfsck 3.0.12 (29 Oct 2011)
dosfsck 3.0.12, 29 Oct 2011, FAT32, LFN
Checking we can access the last sector of the filesystem
Boot sector contents:
System ID "mkdosfs"
Media byte 0xf8 (hard disk)
       512 bytes per logical sector
      4096 bytes per cluster
        32 reserved sectors
First FAT starts at byte 16384 (sector 32)
         2 FATs, 32 bit entries
   7798784 bytes per FAT (= 15232 sectors)
Root directory start at cluster 2 (arbitrary size)
Data area starts at byte 15613952 (sector 30496)
   1948715 data clusters (7981936640 bytes)
62 sectors/track, 247 heads
         0 hidden sectors
  15620218 sectors total
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT
? 1
Reclaiming unconnected clusters.
Checking free cluster summary.
Leaving file system unchanged.
/dev/sdb1: 4 files, 212206/1948715 clusters
manu@manu-Inspiron-N5010:~$ sudo fsck.vfat -f -v /dev/sdb1
dosfsck 3.0.12 (29 Oct 2011)
dosfsck 3.0.12, 29 Oct 2011, FAT32, LFN
Checking we can access the last sector of the filesystem
Boot sector contents:
System ID "mkdosfs"
Media byte 0xf8 (hard disk)
       512 bytes per logical sector
      4096 bytes per cluster
        32 reserved sectors
First FAT starts at byte 16384 (sector 32)
         2 FATs, 32 bit entries
   7798784 bytes per FAT (= 15232 sectors)
Root directory start at cluster 2 (arbitrary size)
Data area starts at byte 15613952 (sector 30496)
   1948715 data clusters (7981936640 bytes)
62 sectors/track, 247 heads
         0 hidden sectors
  15620218 sectors total
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT
? 2
Cluster 196606 out of range (78118970 > 1948716). Setting to EOF.
Cluster 196609 out of range (4064259 > 1948716). Setting to EOF.
Cluster 196612 out of range (6169609 > 1948716). Setting to EOF.
Cluster 196616 out of range (16777215 > 1948716). Setting to EOF.
Cluster 196620 out of range (23199743 > 1948716). Setting to EOF.
Cluster 196624 out of range (12910591 > 1948716). Setting to EOF.
Cluster 196627 out of range (31400841 > 1948716). Setting to EOF.
Cluster 196629 out of range (268370507 > 1948716). Setting to EOF.
Cluster 196631 out of range (31326464 > 1948716). Setting to EOF.
Cluster 196633 out of range (268371614 > 1948716). Setting to EOF.
Cluster 196635 out of range (41287936 > 1948716). Setting to EOF.
Cluster 196637 out of range (268371615 > 1948716). Setting to EOF.
Cluster 196639 out of range (96338176 > 1948716). Setting to EOF.
Cluster 196641 out of range (268371616 > 1948716). Setting to EOF.
Cluster 196643 out of range (5636865 > 1948716). Setting to EOF.
Cluster 196646 out of range (142475392 > 1948716). Setting to EOF.
Cluster 196648 out of range (268371617 > 1948716). Setting to EOF.
Cluster 196650 out of range (51773952 > 1948716). Setting to EOF.
Cluster 196653 out of range (111345858 > 1948716). Setting to EOF.
Cluster 196655 out of range (16777226 > 1948716). Setting to EOF.
Cluster 196657 out of range (111542464 > 1948716). Setting to EOF.
Cluster 196659 out of range (16777226 > 1948716). Setting to EOF.
Cluster 196661 out of range (111608128 > 1948716). Setting to EOF.
Cluster 196663 out of range (67108874 > 1948716). Setting to EOF.
Cluster 196665 out of range (25035136 > 1948716). Setting to EOF.
Cluster 196668 out of range (75366912 > 1948716). Setting to EOF.
Cluster 196670 out of range (268371624 > 1948716). Setting to EOF.
Cluster 196672 out of range (22939419 > 1948716). Setting to EOF.
Cluster 196675 out of range (42861312 > 1948716). Setting to EOF.
Cluster 196678 out of range (70648704 > 1948716). Setting to EOF.
Cluster 196681 out of range (106299398 > 1948716). Setting to EOF.
Cluster 196683 out of range (268371631 > 1948716). Setting to EOF.
Cluster 196685 out of range (155058688 > 1948716). Setting to EOF.
Cluster 196688 out of range (113181824 > 1948716). Setting to EOF.
Cluster 196690 out of range (33554441 > 1948716). Setting to EOF.
Cluster 196692 out of range (140378310 > 1948716). Setting to EOF.
Cluster 196694 out of range (268371648 > 1948716). Setting to EOF.
Cluster 196696 out of range (29753856 > 1948716). Setting to EOF.
Cluster 196699 out of range (113902784 > 1948716). Setting to EOF.
Cluster 196701 out of range (67108873 > 1948716). Setting to EOF.
Cluster 196703 out of range (102630656 > 1948716). Setting to EOF.
Cluster 196706 out of range (128320896 > 1948716). Setting to EOF.
Cluster 196708 out of range (268371659 > 1948716). Setting to EOF.
Cluster 196710 out of range (41288192 > 1948716). Setting to EOF.
Cluster 196713 out of range (114427456 > 1948716). Setting to EOF.
Cluster 196715 out of range (16777225 > 1948716). Setting to EOF.
Cluster 196717 out of range (114755200 > 1948716). Setting to EOF.
Cluster 196719 out of range (16777234 > 1948716). Setting to EOF.
Cluster 196721 out of range (146998976 > 1948716). Setting to EOF.
Cluster 196723 out of range (87293963 > 1948716). Setting to EOF.
Cluster 196725 out of range (129892610 > 1948716). Setting to EOF.
Cluster 196728 out of range (137232520 > 1948716). Setting to EOF.
Cluster 196731 out of range (148975491 > 1948716). Setting to EOF.
Cluster 196733 out of range (50331657 > 1948716). Setting to EOF.
/install_status.log
  Contains a free cluster (590893). Assuming EOF.
Reclaiming unconnected clusters.
Unable to create unique name
manu@manu-Inspiron-N5010:~$ 


---

### Post by NikTh on 2012-07-21
So , what now ? 
Did fsck corrected the problem ? 

Unplug and plug in again Usb-stick and try to format it with Disk Utility . 
Do not just format , but follow this
1)Umount it 
2)Delete (click delete ) 
3)Add new.. (Fat) 

Thanks

---

### Post by manuganji on 2012-07-21
NikTh, thanks for the patient answers.

On clicking delete partition, I get this error in disk utility - > Error erasing: helper exited with exit code 1: In part_del_partition: device_file=/dev/sdb, offset=31744

---

### Post by NikTh on 2012-07-21
Hmm.. strange problem. 
Are you sure that Usb  doesn't has any switch button , for write protect ON/OFF ? 

I don't know any other method . 
dd command of course it a way , but i am not sure if fix the problem or will make it worse.
If you want to try dd (with your own risk) , post back . 

**Edit:** Unplug usb and plug in again , then open a terminal and write 
```
dmesg | tail -n25
```post back the results.

Also we can try to format Usb-stick with Fdisk. Post back if you want to try. 
Regards

---

### Post by kurt18947 on 2012-07-21
Good point about the hardware switch.  Some of them are quite inconspicuous.  If all else fails, would it be worthwhile to look at the USB drive with Gparted?  Perhaps delete and recreate the partition then format?

---

### Post by manuganji on 2012-07-21
This is dmesg output

> manu@manu-Inspiron-N5010:~$ dmesg | tail -n25
[ 4296.489526] hub 2-1.6:1.0: USB hub found
[ 4296.489719] hub 2-1.6:1.0: 3 ports detected
[ 4296.764440] usb 2-1.6.1: new full-speed USB device number 17 using ehci_hcd
[ 4296.864600] input: HID 413c:8161 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.1/2-1.6.1:1.0/input/input14
[ 4296.864812] generic-usb 0003:413C:8161.0003: input,hidraw0: USB HID v1.11 Keyboard [HID 413c:8161] on usb-0000:00:1d.0-1.6.1/input0
[ 4296.935596] usb 2-1.6.2: new full-speed USB device number 18 using ehci_hcd
[ 4297.044216] input: HID 413c:8162 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.2/2-1.6.2:1.0/input/input15
[ 4297.047474] generic-usb 0003:413C:8162.0004: input,hidraw1: USB HID v1.11 Mouse [HID 413c:8162] on usb-0000:00:1d.0-1.6.2/input0
[ 4534.257681] audit_printk_skb: 45 callbacks suppressed
[ 4534.257684] type=1701 audit(1342854216.057:27): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=7495 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7f5fd088aeb0 code=0x50002
[ 4534.257698] type=1701 audit(1342854216.057:28): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=7495 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7f5fd088aeb0 code=0x50002
[ 4534.310496] type=1701 audit(1342854216.109:29): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=7501 comm="chrome" reason="seccomp" sig=0 syscall=59 compat=0 ip=0x7f5fd0864427 code=0x50002
[ 7015.994856] usb 2-1.2: new high-speed USB device number 19 using ehci_hcd
[ 7016.088906] scsi15 : usb-storage 2-1.2:1.0
[ 7016.306193] usb 2-1.2: USB disconnect, device number 19
[ 7016.505703] usb 2-1.2: new high-speed USB device number 20 using ehci_hcd
[ 7016.599820] scsi16 : usb-storage 2-1.2:1.0
[ 7017.596720] scsi 16:0:0:0: Direct-Access     SanDisk  Cruzer Edge      1.20 PQ: 0 ANSI: 5
[ 7017.597824] sd 16:0:0:0: Attached scsi generic sg2 type 0
[ 7017.601317] sd 16:0:0:0: [sdb] 15633408 512-byte logical blocks: (8.00 GB/7.45 GiB)
[ 7017.602606] sd 16:0:0:0: [sdb] Write Protect is on
[ 7017.602613] sd 16:0:0:0: [sdb] Mode Sense: 43 00 80 00
[ 7017.603397] sd 16:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 7017.613268]  sdb: sdb1
[ 7017.616873] sd 16:0:0:0: [sdb] Attached SCSI removable disk


There is no hardware switch on this usb. It's a simple pen drive. I don't know how to use this dd command. Please tell me how to use it. And what could be the risk involved? Yeah I can try that fdisk command too.

@kurt18947 I am unable to delete it in gparted even.

Here are the gparted error details
> GParted 0.11.0 --enable-libparted-dmraid

Libparted 2.3

Delete /dev/sdb1 (fat32, 7.45 GiB) from /dev/sdb  00:00:00    ( ERROR )
    	
calibrate /dev/sdb1  00:00:00    ( SUCCESS )
    	
path: /dev/sdb1
start: 62
end: 1,56,20,279
size: 1,56,20,218 (7.45 GiB)
delete partition  00:00:00    ( ERROR )
libparted messages    ( INFO )
    	
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
Can't write to /dev/sdb, because it is opened read-only.
Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only.
========================================

Create Primary Partition #1 (ext2, 7.45 GiB) on /dev/sdb
========================================

---

### Post by NikTh on 2012-07-21
Hi , 
ok first lets try with fdisk . 

Open a terminal and ```
sudo umount /dev/sdb1 
sudo fdisk /dev/sdb
```Then you must hit below keys with order 
> d = delete existing patition
w = write table to disk and exitThen again 
```
sudo fdisk /dev/sdb 
```> n= create a new patition
Then hit "Enter" to other prompts (Enter=default settings)
w = write table to disk and exitIf an error occur , then post it here. 

Regards

---

### Post by manuganji on 2012-07-21
NikTh,

Here is the output of the first step

> manu@manu-Inspiron-N5010:~$ umount /dev/sdb1
umount: /dev/sdb1 is not mounted (according to mtab)
manu@manu-Inspiron-N5010:~$ fdisk /dev/sdb
fdisk: unable to open /dev/sdb: Permission denied
manu@manu-Inspiron-N5010:~$ sudo fdisk /dev/sdb
You will not be able to write the partition table.

Command (m for help): d
Selected partition 1

Command (m for help): w
fdisk: unable to write /dev/sdb: Bad file descriptor


---

### Post by NikTh on 2012-07-21
First try this 
Open terminal and run 
```
sudo hdparm -r0 /dev/sdb
``` 
unplug usb and plug in again.. 

If above not worked then
try something else.. 
Do you have a live cd / usb ? boot from there.. and click "Try Ubuntu" . 
When you are at desktop environment , plug in your problematic usb-stick and open a terminal .. write
```
dmesg | tail -n 25 
```post back here the results. 

Regards

---

### Post by lkraemer on 2012-07-23
manuganji,
Interesting problem..........

There are two ways to proceed....Windows or Linux..


**Windows:**
Use **GOOGLE** to search for one of the two **BOLD** files named below:

HP USB Disk Storage Format Tool **SP27213.exe**
HP USB Disk Storage Format Tool **SP27608.exe**

Which ever is the latest version, execute it in Windows selecting the proper USB Device, then format your USB Flash Drive.
I've never had this software fail when others wouldn't touch the USB Flash Drive.


**Linux:**
To locate your USB Flash Drive that will not mount do the following commands (may need to preface
some commands with sudo depending on the Distro) in order until you locate the USB Flash Drive......DOUBLE CHECK
the SIZE is X Gig so you are 100% SURE it's the device.  (I'm not responsible for mistyped commands
or Data Loss.....You're Driving...)

Execute these commands:  (~1 minute after plugging in the USB Flash Drive)
(Copy & Paste to prevent errors)
```

dmesg | tail
sudo blkid
mount
fdisk -l

```
One of these commands should give a clue as to what the device is detected as................................
Let's assume the device doesn't mount, but shows up as /dev/mmcblk0 with a partition labeled as /dev/mmcblk0p1

Ah, now we know what the device is, and most likely gparted, and fdisk may not recognize the device,
and won't display it's information.  So, let's write the device full of ZERO's so everything is
totally wiped clean.

**WARNING: Make 100% sure it's what you want to do, the Device is Correct, and the command is Correct.**

```

dd if=/dev/zero of=/dev/devicenamefromabove bs=1M

```
This will overwrite the device with all ZERO's.  In my case I just used the default command which was:
```

dd if=dev/zero of=/dev/mmcblk0

```
It takes a long while, but it will finish.  When this is done, remove the device, and after a short period,
plug in the USB device.  Then execute gparted and do:

**DEVICE** - Create a new Partition Table (MSDOS Type)
**CREATE** - a New Partition (assuming Fat32 for allowing Windows access)
**FORMAT** - the new Partition (also Fat32)

Then SAFE REMOVE the device.  You can then plug in the USB Device, it should auto mount, and allow you to read/write normally.


Let us know how it goes.

Larry

---

### Post by ratcheer on 2012-07-24
I am waiting to see the results because I also have one of these Cruzer drives and have never been able to get rid of their stupid software and cleanly reformat it. They somehow have it set to a hard and fast read-only.

Tim

PS - My Cruzer does mount, but it mounts as two devices:

> /dev/sdg1: LABEL="Cruzer2" UUID="6BC7-7E30" TYPE="vfat" 
/dev/sdh1: SEC_TYPE="msdos" UUID="3BE3-0064" TYPE="vfat" So, I'm not sure what to do. I guess I should perform the instructions for dd to the /dev/sdh1, which is the damnable read-only thing that SanDisk puts on it. 

But, I'm still not sure how to get it down to just one device that I can create a new partition table on.

---

### Post by deano724 on 2012-08-02
I am slightly surprised how recent this thread is.  I have been trying to solve the same problem and came across this thread.  Thanks for the help up to now.  Similar to manuganji, I have a USB pendrive of unknown manufacturer that has gotten stuck in read-only mode.  I originally installed Ubuntu with Persistance on it, but one day I tried starting up and it could not mount '/'.  

All attempts at using WinXP, Win7 formatting, GParted (Live CD or in Ubuntu Live CD), fdisk, and dd have resulted most of the time with the words "read-only file system".  I am starting to fear the drive is hopeless even though I read it just fine.

Picking up at the end of trying everything, fdisk resulted in "Bad file descriptor" when trying to delete the partition or write a new one, and dd stopped immediately while opening my /dev/sdb saying it was a "read-only file system".

I still have to try the "HP USB Disk Storage Format Tool" since this is a FAT32 formatted drive.  But I thought I would look for one last set of advice.  One other thing I tried is the following with dosfsck (wasn't sure if I should call the device or the partition):
```

ubuntu@ubuntu:~$ sudo dosfsck -a -v /dev/sdb
dosfsck 3.0.9 (31 Jan 2010)
dosfsck 3.0.9, 31 Jan 2010, FAT32, LFN
open: Read-only file system
ubuntu@ubuntu:~$ sudo dosfsck -a -v /dev/sdb1
dosfsck 3.0.9 (31 Jan 2010)
dosfsck 3.0.9, 31 Jan 2010, FAT32, LFN
Checking we can access the last sector of the filesystem
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  3:53/4d, 4:59/53, 5:53/44, 6:4c/4f, 7:49/53, 8:4e/35, 9:55/2e, 10:58/30
  , 90:fa/33, 91:fc/c9, 92:31/8e, 93:c9/d1, 94:8e/bc, 95:d1/f4, 96:bc/7b
  , 97:76/8e, 98:7b/c1, 99:52/8e, 100:06/d9, 101:57/bd, 102:1e/00, 103:56/7c
  , 104:8e/88, 105:c1/4e, 106:b1/02, 107:26/8a, 108:bf/56, 109:78/40
  , 110:7b/b4, 111:f3/08, 112:a5/cd, 113:8e/13, 114:d9/73, 115:bb/05
  , 116:78/b9, 117:00/ff, 118:0f/ff, 119:b4/8a, 120:37/f1, 121:0f/66
  , 122:a0/0f, 123:56/b6, 124:20/c6, 125:d2/40, 126:78/66, 127:1b/0f
  , 128:31/b6, 129:c0/d1, 130:b1/80, 131:06/e2, 132:89/3f, 133:3f/f7
  , 134:89/e2, 135:47/86, 136:02/cd, 137:f3/c0, 138:64/ed, 139:a5/06
  , 140:8a/41, 141:0e/66, 142:18/0f, 143:7c/b7, 144:88/c9, 145:4d/66
  , 146:f8/f7, 147:50/e1, 148:50/66, 149:50/89, 150:50/46, 151:cd/f8
  , 152:13/83, 153:eb/7e, 154:62/16, 155:8b/00, 156:55/75, 157:aa/38
  , 158:8b/83, 159:75/7e, 160:a8/2a, 161:c1/00, 162:ee/77, 163:04/32
  , 164:01/66, 165:f2/8b, 166:83/46, 167:fa/1c, 168:4f/66, 169:76/83
  , 170:31/c0, 171:81/0c, 172:fa/bb, 173:b2/00, 174:07/80, 175:73/b9
  , 176:2b/01, 177:f6/00, 178:45/e8, 179:b4/2b, 180:7f/00, 181:75/e9
  , 182:25/48, 183:38/03, 184:4d/a0, 185:b8/fa, 186:74/7d, 187:20/b4
  , 188:66/7d, 189:3d/8b, 190:21/f0, 191:47/ac, 192:50/84, 193:54/c0
  , 194:75/74, 195:10/17, 196:80/3c, 197:7d/ff, 198:b8/74, 199:ed/09
  , 200:75/b4, 201:0a/0e, 202:66/bb, 203:ff/07, 204:75/00, 205:ec/cd
  , 206:66/10, 207:ff/eb, 208:75/ee, 209:e8/a0, 210:eb/fb, 211:0f/7d
  , 212:51/eb, 213:51/e5, 214:66/a0, 215:ff/f9, 216:75/7d, 217:bc/eb
  , 218:eb/e0, 219:07/98, 220:51/cd, 221:51/16, 222:66/cd, 223:ff/19
  , 224:36/66, 225:1c/60, 226:7c/66, 227:b4/3b, 228:08/46, 229:e8/f8
  , 230:e9/0f, 231:00/82, 232:72/4a, 233:13/00, 234:20/66, 235:e4/6a
  , 236:75/00, 237:0f/66, 238:c1/50, 239:ea/06, 240:08/53, 241:42/66
  , 242:89/68, 243:16/10, 244:1a/00, 245:7c/01, 246:83/00, 247:e1/80
  , 248:3f/7e, 249:89/02, 250:0e/00, 251:18/0f, 252:7c/85, 253:fb/20
  , 254:bb/00, 255:aa/b4, 256:55/41, 257:b4/bb, 258:41/aa, 259:e8/55
  , 260:cb/8a, 261:00/56, 262:72/40, 263:10/cd, 264:81/13, 265:fb/0f
  , 266:55/82, 267:aa/1c, 268:75/00, 269:0a/81, 270:f6/fb, 271:c1/55
  , 272:01/aa, 273:74/0f, 274:05/85, 275:c6/14, 276:06/00, 277:46/f6
  , 278:7d/c1, 279:00/01, 280:66/0f, 281:b8/84, 282:90/0d, 283:78/00
  , 284:00/fe, 285:00/46, 286:66/02, 287:ba/b4, 288:00/42, 289:00/8a
  , 290:00/56, 291:00/40, 292:bb/8b, 293:00/f4, 294:80/cd, 295:e8/13
  , 296:0e/b0, 297:00/f9, 299:81/58, 300:3e/66, 301:1c/58, 302:80/66
  , 303:c5/58, 304:ed/66, 305:5a/58, 306:70/eb, 307:75/2a, 308:74/66
  , 309:e9/33, 310:f8/d2, 311:02/66, 312:66/0f, 313:03/b7, 314:06/4e
  , 315:60/18, 316:7b/66, 317:66/f7, 318:13/f1, 319:16/fe, 320:64/c2
  , 321:7b/8a, 322:b9/ca, 323:10/66, 324:00/8b, 325:eb/d0, 326:2b/66
  , 327:66/c1, 328:52/ea, 329:66/10, 330:50/f7, 331:06/76, 332:53/1a
  , 333:6a/86, 334:01/d6, 335:6a/8a, 336:10/56, 337:89/40, 338:e6/8a
  , 339:66/e8, 340:60/c0, 341:b4/e4, 342:42/06, 343:e8/0a, 344:77/cc
  , 345:00/b8, 346:66/01, 347:61/02, 348:8d/cd, 349:64/13, 350:10/66
  , 351:72/61, 352:01/0f, 353:c3/82, 354:66/54, 355:60/ff, 356:31/81
  , 357:c0/c3, 358:e8/00, 359:68/02, 360:00/66, 361:66/40, 362:61/49
  , 363:e2/0f, 364:da/85, 365:c6/71, 366:06/ff, 367:46/c3, 368:7d/4e
  , 369:2b/54, 370:66/4c, 371:60/44, 372:66/52, 373:0f/20, 374:b7/20
  , 375:36/20, 376:18/20, 377:7c/20, 378:66/20, 379:0f/00, 380:b7/00
  , 381:3e/00, 382:1a/00, 383:7c/00, 384:66/00, 385:f7/00, 386:f6/00
  , 387:31/00, 388:c9/00, 389:87/00, 390:ca/00, 391:66/00, 392:f7/00
  , 393:f7/00, 394:66/00, 395:3d/00, 396:ff/00, 397:03/00, 400:77/00
  , 401:17/00, 402:c0/00, 403:e4/00, 404:06/00, 405:41/00, 406:08/00
  , 407:e1/00, 408:88/00, 409:c5/00, 410:88/00, 411:d6/00, 412:b8/00
  , 413:01/00, 414:02/00, 415:e8/00, 416:2f/00, 418:66/00, 419:61/00
  , 420:72/00, 421:01/00, 422:c3/00, 423:e2/00, 424:c9/00, 425:31/00
  , 426:f6/00, 427:8e/00, 428:d6/0d, 429:bc/0a, 430:68/52, 431:7b/65
  , 432:8e/6d, 433:de/6f, 434:66/76, 435:8f/65, 436:06/20, 437:78/64
  , 438:00/69, 439:be/73, 440:da/6b, 441:7d/73, 442:ac/20, 443:20/6f
  , 444:c0/72, 445:74/20, 446:09/6f, 447:b4/74, 448:0e/68, 449:bb/65
  , 450:07/72, 451:00/20, 452:cd/6d, 453:10/65, 454:eb/64, 455:f2/69
  , 456:31/61, 457:c0/2e, 458:cd/ff, 459:16/0d, 460:cd/0a, 461:19/44
  , 462:f4/69, 463:eb/73, 464:fd/6b, 465:8a/20, 466:16/65, 467:74/72
  , 468:7b/72, 469:06/6f, 470:cd/72, 471:13/ff, 472:07/0d, 473:c3/0a
  , 474:42/50, 475:6f/72, 476:6f/65, 477:74/73, 478:20/73, 479:65/20
  , 480:72/61, 481:72/6e, 482:6f/79, 483:72/20, 484:0d/6b, 485:0a/65
  , 486:00/79, 487:00/20, 488:00/74, 489:00/6f, 490:00/20, 491:00/72
  , 492:00/65, 493:00/73, 494:00/74, 495:00/61, 496:00/72, 497:00/74
  , 498:00/0d, 499:00/0a, 504:fe/00, 505:02/ac, 506:b2/cb, 507:3e/d8
  , 508:18/00, 509:37/00
  Not automatically fixing this.
Boot sector contents:
System ID "SYSLINUX"
Media byte 0xf8 (hard disk)
       512 bytes per logical sector
      4096 bytes per cluster
        36 reserved sectors
First FAT starts at byte 18432 (sector 36)
         2 FATs, 32 bit entries
   7889920 bytes per FAT (= 15410 sectors)
Root directory start at cluster 2 (arbitrary size)
Data area starts at byte 15798272 (sector 30856)
   1972358 data clusters (8078778368 bytes)
63 sectors/track, 255 heads
       520 hidden sectors
  15809720 sectors total
Reclaiming unconnected clusters.
Checking free cluster summary.
/dev/sdb1: 250 files, 965593/1972358 clusters

```Also for reference, here is my dmesg info:
```

dmesg | tail
[ 1594.485897] sd 4:0:0:0: [sdb] Write Protect is on
[ 1594.485903] sd 4:0:0:0: [sdb] Mode Sense: 03 00 80 00
[ 1594.486391] sd 4:0:0:0: [sdb] No Caching mode page present
[ 1594.486397] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1594.489525] sd 4:0:0:0: [sdb] No Caching mode page present
[ 1594.489534] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1594.491145]  sdb: sdb1
[ 1594.493889] sd 4:0:0:0: [sdb] No Caching mode page present
[ 1594.493895] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1594.493900] sd 4:0:0:0: [sdb] Attached SCSI removable disk

```Thanks for any ideas for me and manuganji.  I'm hoping two test cases might help.

---

### Post by TheMTtakeover on 2012-08-02
Not to hop on the bandwagon here but I also have a flash drive that is stuck in read-only mode and if anyone has tried any of these solutions and they have worked for you, could you please post back here with your results and exactly what you did. Thanks.

---

### Post by lkraemer on 2012-08-03
I searched for "USB Flash Drive  stuck in read-only mode" and found this URL:
[http://www.tomshardware.com/forum/77357-45-remove-write-protection-memory-stick](http://www.tomshardware.com/forum/77357-45-remove-write-protection-memory-stick)

Which has a zip file for a Windows Program that is supposed to work, according to the postings.
You will have to format the USB Flash Drive after removing the read-only mode.

Be sure to scan it with the typical Windows software before use.  I can't guarantee it's clean as downloaded........from either site.


REF:
HP USB Disk Storage Format Tool SP27213.exe  -- This is Version 2.0.0.B
HP USB Disk Storage Format Tool SP27608.exe  -- This is the latest Version 2.1.8
[http://download.cnet.com/HP-USB-Disk-Storage-Format-Tool/3010-2094_4-10974082.html](http://download.cnet.com/HP-USB-Disk-Storage-Format-Tool/3010-2094_4-10974082.html)

I also have the original HP files that I downloaded from their site in 2008.  PM with a valid email address if you want a specific file.

Another interesting URL I stumbled across tells how to use Windows "DISKPART" to clear the READ-ONLY SETTING of USB Flash Drives.

[http://www.rmprepusb.com/tutorials/54---how-to-fix-write-protected-disks](http://www.rmprepusb.com/tutorials/54---how-to-fix-write-protected-disks)

[http://technet.microsoft.com/en-us/library/cc766465%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc766465%28v=ws.10%29.aspx)

To test this I used Windows XP "Diskpart" as follows:

1. Start Menu - Run Program - CMD 
2. When the command console opens, type DISKPART
3. List the drives by typing LIS DIS  
4. Select the USB drive by typing  SEL DIS 1         (if disk 1 is your USB drive)
5. Inspect the details for that disk by typing  DET DIS
    Check if the disk is marked as Read-only
6. Type ATT DIS CLEAR READONLY    to clear the ReadOnly attribute and then type DET DIS again to check it has been cleared.
   
(optional - if the drive still is Readonly try this) Type CLEAN  to erase all contents from the drive
(make sure you have selected the correct drive!!!!!)

7. Finally type EXIT  to quit Diskpart

If this process works it might be the easiest fix.  I executed DISKPART on XP, and looked at the commands via HELP.  But, I don't
have a USB Flash Drive that is READ-ONLY right now.


A Linux equivalent command should be hdparm.  To locate the device use the following commands after inserting the device to
determine what the USB Device is detected as:
```

dmesg | tail
sudo blkid
mount
fdisk -l

```
To turn off disk device`s write protect, use the low level system utility hdparm like this: (where x is the letter of
your device [a..z])
```

man hdparm
sudo hdparm -r0 /dev/sdx

```
where we assume that /dev/sdx is the Physical disk device we're working on.


Larry

---

### Post by manuganji on 2012-10-27
I am sorry for not keeping you updated. I contacted SanDisk with my problem. They confirmed that this a hardware problem. 

> The flash drive has detected a potential fault and become write protected to prevent data loss. There is no method to fix this. You will need to backup your data and replace the flash drive.

After that I got it replaced. It was easy as I didn't have any sensitive data on it. Otherwise, I wouldn't have been able to delete it before getting a replacement. Anyway, thanks all for taking time to respond.

---

### Post by Atitudes on 2012-11-13
[@lkraemer]("http://ubuntuforums.org/member.php?u=365139") Well, and thanks to the search help I just experimented your tips and unfortunately it didn't worked for me :(  

@manuganji Unlike you the pen is working perfectly, it doesn't have any kind of switch and it's a very nasty pen offered by some laboratory to their clients with a small read-only partition of 50mb that cannot be formatted :(

@NikTh I will try the other tips but i did found them similar to the ones I just performed (except for the "dd" thing) and as I'm not experienced (although I've been using ubuntu for years) I'm a bit afraid to go so far...

Anyway, I've already tried a bunch of solutions and it's not about 50mb that i'm worried...it's more about the challenge now :D since it seems that this is still an unsolved matter!! I will read the thread more carefully now and if I try anything new that works I'll post back.

Now :guitar: and feel free to help!! Gladly appreciate!

(I confirm now, tried all the other tips (not dd yet tho) and none have solved the problem)

---

### Post by Zaphod B. on 2013-02-15
> **lkraemer said:**
> 
Larry
Attached Files
	Repair_v2.9.1.8A.zip (142.9 KB, 26 views)

This man's file works!  Just cured my 16gb drive locked drive that  I have been trying to fix for MONTHS.

---

### Post by simplelogic on 2013-06-28
> **TheMTtakeover said:**
> Not to hop on the bandwagon here but I also have a flash drive that is stuck in read-only mode and if anyone has tried any of these solutions and they have worked for you, could you please post back here with your results and exactly what you did. Thanks.


hi format your card/usb stick once in windows, and then later you can delete the partition 
with "sudo fdisk  /dev/sdb" command in you linux machine.
it will work

---

### Post by boss2022003 on 2013-07-20
@Zaphod B. I am having the same problem and I tried using the Repair_v2.9.1.8A.zip file, but I got a 'USB Flash Drive not found' error, while the usb flash drive is inserted and loaded. Please provide a little more insight in what you did to cure your flashdrive.

---

### Post by georgewsmit on 2013-08-11
Hi all,

I tried to format my flash disk variour ways and cant seem to get it right.
I tried using Disk Utility from Ubuntu 12.04, also tried to follow steps above!

Here is what I did in terminal:

```

sudo fdisk /dev/sdb

```
This is the outcome:
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x619ad5e7.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): n
Partition type:
   p   primary (0 primary, 0 extended, 4 free)
   e   extended
Select (default p): e
Partition number (1-4, default 1): 4
First sector (2048-30530687, default 2048): 
Using default value 2048
Last sector, +sectors or +size{K,M,G} (2048-30530687, default 30530687): 
Using default value 30530687

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 5: Input/output error.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)

Error closing file

---

### Post by vmalep on 2014-04-22
Hi!

In my case, I eventually figured out that I had simply to umount the device as root in order to perform the partition manipulation without complain:
sudo umount /dev/[device]

BR
Pierre

---

### Post by hill-benny on 2014-08-17
Interesting:

an 1GB Kingston Data Traveler II showed up **only 103MB **of complete available space in fdisk and all other tools as Gparted.
Even dd if=/dev/null or /dev/zero, different bs did not work: first it took olny some bytes, later it dd'd only the 103 MB.

Then i tried to format with Repair_v2.9.1.8A.zip from Page 2 of this thread.
---> [B]FORMAT FAILED !!!

[/B]After that failed Format (Device internal descriptor changed from "datatravelerII" to "USB Disk X28" **_AND_** "FLASH DRIVE".
_Now DD /dev/zero with bs=1M worked for the complete 1GB_ !!!!!!!!!!! Hallelujah !!!!
Tried it for 5 years every year!

---

