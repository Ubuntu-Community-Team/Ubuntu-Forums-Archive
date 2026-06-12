---
title: "Ubuntu Can't Detect My Secondary Drive"
date: 2013-08-26
forum: New to Ubuntu
---

### Post by desmond_t2 on 2013-08-26
Hi guy,

My primary drive is an SSD and my secondary is a HDD.
The thing is when I start my computer, I have to click on the secondary drive icon then ubuntu will "see" the HDD. 
If i didnt click the HDD icon ubuntu thinks that my computer only has a primary drive.
I tot all hard drive are auto detected in ubuntu? (Please see attachment)

Is this normal?

Please help thanks in advance=)

---

### Post by bkline on 2013-08-26
This looks like it might be useful:

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by r_avital on 2013-08-26
Hi,

What version of Ubuntu is this?

I have the same behavior in Lucid (two HDDs, no SSD, the one that is not the Root needs to be clicked on before other apps recognize it).  My 13.04 machine has only one HDD, so I can't test it in this version.

I assume you mean that applications other than the file manager (your "home" icon/menu item) don't recognize it, correct?  Because from your thumbnail, it looks like it is recognized ok on your home folder.

---

### Post by vishal_agarwal2 on 2013-08-27
what is the output of 
1. lsusb
2. fdisk -l
3. mount

---

### Post by desmond_t2 on 2013-08-28
Hi guy sorry for the late reply. here is what i get when i key in the command.

> **vishal_agarwal2 said:**
> what is the output of 
1. lsusb
2. fdisk -l
3. mount

1. lsusb

> Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 1235:8004 Novation EMS 
Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 005: ID 2433:b111  


2. fdisk -l

> Disk /dev/sda: 512.1 GB, 512110190592 bytes
255 heads, 63 sectors/track, 62260 cylinders, total 1000215216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1000215215   500107607+  ee  GPT


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x746fa931


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907026943  1953512448   83  Linux


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x17009ff8


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953521663   976759808    7  HPFS/NTFS/exFAT


Disk /dev/sdd: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312579695 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe3eae3ea


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048   312575999   156286976    7  HPFS/NTFS/exFAT




3. mount

> /dev/sda2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda1 on /boot/efi type vfat (rw)
rpc_pipefs on /run/rpc_pipefs type rpc_pipefs (rw)
gvfs-fuse-daemon on /home/desmond/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=desmond)
/dev/sdc1 on /media/1TB type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


---

### Post by 3rdalbum on 2013-08-28
> **desmond_t2 said:**
> Hi guy,

My primary drive is an SSD and my secondary is a HDD.
The thing is when I start my computer, I have to click on the secondary drive icon then ubuntu will "see" the HDD. 
If i didnt click the HDD icon ubuntu thinks that my computer only has a primary drive.
I tot all hard drive are auto detected in ubuntu? (Please see attachment)

Is this normal?

Please help thanks in advance=)

Yes, this is 100% normal. Internal disks are not mounted until you click on them.

It's not that "Ubuntu thinks I only have one drive", it knows the other drive but wont mount it without your explicit permission.

If you want to mount it automatically, you can add it to /etc/database either by editing that file in a text editor, or by using a program that makes it simple for you.

---

### Post by desmond_t2 on 2013-08-28
> **3rdalbum said:**
> Yes, this is 100% normal. Internal disks are not mounted until you click on them.

It's not that "Ubuntu thinks I only have one drive", it knows the other drive but wont mount it without your explicit permission.

If you want to mount it automatically, you can add it to /etc/database either by editing that file in a text editor, or by using a program that makes it simple for you.

Hi 3rdalbum,

may i know which program should i use to automatically mount it??

thanks

---

### Post by 3rdalbum on 2013-08-28
> **desmond_t2 said:**
> Hi 3rdalbum,

may i know which program should i use to automatically mount it??

thanks

I couldn't find a program that I had heard of before, but all such programs just edit the /etc/fstab file. You can certainly do this manually, it's not hard. This little writeup will help:

[http://askubuntu.com/questions/231880/pysdm-missing-in-ubuntu-12-10-and-higher](http://askubuntu.com/questions/231880/pysdm-missing-in-ubuntu-12-10-and-higher)

---

### Post by desmond_t2 on 2013-08-28
> **3rdalbum said:**
> I couldn't find a program that I had heard of before, but all such programs just edit the /etc/fstab file. You can certainly do this manually, it's not hard. This little writeup will help:

[http://askubuntu.com/questions/231880/pysdm-missing-in-ubuntu-12-10-and-higher](http://askubuntu.com/questions/231880/pysdm-missing-in-ubuntu-12-10-and-higher)

Hi 3rdalbum,

thanks for the reply. I have try the link above but i receive this error msg.

> Unable to mount 2TB

Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdb1 on /media/2TB


What does it mean??

please help. thanks

---

### Post by oldfred on 2013-08-29
Where are you getting error message? May be related to new systems now default mount to /media/$USER not just /media.
Is that drive an external drive or an internal drive.

Usually best not to use fstab to mount external drives as now system boots so quickly that an external USB drive will not come up to speed and still give error messages.

If an internal drive:
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

Do you actually have a 1TB drive in FAT format? 
Generally not recommended unless you have to have it for compatibility with another system like xbox or Mac. FAT has no journal so file corruption will be a lot more difficult to fix with chkdsk and chkdsk on a very large partition may literally take days. Also FAT32 has a maximum file size of 4GB so no very large files.

---

### Post by desmond_t2 on 2013-08-30
> **oldfred said:**
> Where are you getting error message? May be related to new systems now default mount to /media/$USER not just /media.
Is that drive an external drive or an internal drive.

Usually best not to use fstab to mount external drives as now system boots so quickly that an external USB drive will not come up to speed and still give error messages.

If an internal drive:
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

Do you actually have a 1TB drive in FAT format? 
Generally not recommended unless you have to have it for compatibility with another system like xbox or Mac. FAT has no journal so file corruption will be a lot more difficult to fix with chkdsk and chkdsk on a very large partition may literally take days. Also FAT32 has a maximum file size of 4GB so no very large files.

Hi oldfred,

All my drives are internal HDD. I have read Post #6 as you suggested. But I am a nood, so i dont really understand what are they talking about...

when i key in > sudo blkid -c /dev/null, I got this

> /dev/sdb1: LABEL="2TB" UUID="3F9871C62D89C73C" TYPE="ntfs" 
/dev/sdc1: LABEL="1TB" UUID="C03C-3E15" TYPE="vfat" 
/dev/sdd1: LABEL="New Volume" UUID="D614FEB114FE9429" TYPE="ntfs" 

As of now I can mount the 1TB automatically but the rest of the drive is a no go...

Please help...

Thanks in advance

---

### Post by oldfred on 2013-08-30
I do not like spaces so I would not use New Volume. Linux has to have quotes or you have to escape the space every time so it is just a tad harder to work with. I prefer to use CamelCase, under_score or justaname.

You do not have to mount with same name as the label. And in fact I labelled my data partition Data and used a mount of /mnt/data. Of course with Linux Data and data are not the same as it is case sensitive.

While label will work as mounts and you can actually directly use them, I normally create my own mount point.

       sudo mkdir /mnt/2TBdata

      
 ```

# Entry for /dev/sdb1
UUID=3F9871C62D89C73C /mnt/2TBdata ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0

```

The above is mounted in /mnt and will not directly show in Nautilus, use /media if you want in to directly see it in Nautilus. 

Use these commands and copy & paste above entry. If you change mount (/mnt) or want to change mount point (2TBdata) just be sure to be consistent in all places. Then do the same for your sdd1 with a different mount point.
      
 sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab


   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. 
Make sure you have partition unmounted if previously mounted:
sudo mount -a

---

