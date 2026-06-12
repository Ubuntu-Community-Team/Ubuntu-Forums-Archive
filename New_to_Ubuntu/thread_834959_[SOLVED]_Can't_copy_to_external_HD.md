---
title: "[SOLVED] Can't copy to external HD"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by Bigtime_Scrub on 2008-06-20
I think I'm missing something. I have a USB HD connected and mounted properly but I cant add anything to it. I thought it was a permissions problem but I used gksu thunar (I use Xubuntu) and I still cant drag and drop files to it. Im pretty sure Im missing a step but I dont know what that step would be. Id appreciate any help.

---

### Post by Fingers &amp; Thumbs on 2008-06-20
Hmmmmm, I'm not quite sure how to solve this, but in the meantime, if you need to get files onto your external hdd, you could try to move the files using terminal?

```
cd /path to folder where your file is
```
```

sudo mv /filename /path to hdd
```

---

### Post by Dynaflow on 2008-06-20
Are you getting an error message of some sort?  Try navigating to the thing's mount point with your all-access file browser (probably somewhere in /media), right-click it to check and possibly correct any permissions that aren't what they should be, and then try copying to it again.

Out of curiosity, what filesystem does the external drive use?  If it's NTFS and you don't have read-write support for that (through the ntfs-3g package), that might be causing problems.  Most of those things are formatted in FAT, though.

---

### Post by Bigtime_Scrub on 2008-06-20
I dont know what file system it uses I dont know how to check. I thought Id be able to plug it in and just drop files. 

I got this error when I tried to copy files over and also when I tried to create a partition.

 Opened disk read-only - you have no permission to writelast_lba(): I                       FATAL ERROR: Cannot get disk size

---

### Post by kansasnoob on 2008-06-20
I don't use Thunar but I don't think what I'm suggesting matters.

Try adding either:

usbmount

or: 

pmount &
hal

I prefer usbmount but the pmount + hal combo creates a desktop icon when it's plugged in. (Don't do both!)

Then also install:

ntfs-config

And if that doesn't cut it then install:

ntfsprogs

You can have ntfs-config and ntfsprogs installed together.

[http://www.linux-ntfs.org/doku.php?id=ntfsprogs](http://www.linux-ntfs.org/doku.php?id=ntfsprogs)

---

### Post by Bigtime_Scrub on 2008-06-20
Look at this. Im VERY confused now :confused:

```
gary@gary-desktop:~$ sudo gparted /media/SimpleDrive
======================
libparted : 1.7.1
======================
Unable to open /media/SimpleDrive read-write (Is a directory).  /media/SimpleDrive has been opened read-only.
Unable to open /media/SimpleDrive read-write (Is a directory).  /media/SimpleDrive has been opened read-only.
Unable to open /media/SimpleDrive - unrecognised disk label
```

---

### Post by iaculallad on 2008-06-20
What about posting the results of (your External HD must be plugged):

```
sudo fdisk -l
```

and

```
sudo blkid
```

---

### Post by Bigtime_Scrub on 2008-06-20
> **iaculallad said:**
> What about posting the results of (your External HD must be plugged):

```
sudo fdisk -l
```

and

```
sudo blkid
```



Here it is:

```

gary@gary-desktop:~$ sudo fdisk -l
[sudo] password for gary: 

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc2481aff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4813    38660391   83  Linux
/dev/sda2            4814        4998     1486012+   5  Extended
/dev/sda5            4814        4998     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca7e37f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS
gary@gary-desktop:~$ sudo blkid
/dev/sda1: UUID="ec6641b3-85be-4c87-853e-f27b0bc9376f" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="48119400-4e6d-4ef4-9ebf-0da3e05741a6" 
/dev/sdb1: UUID="68ECD765ECD72C56" LABEL="SimpleDrive" TYPE="ntfs" 
```

---

### Post by iaculallad on 2008-06-20
Kindly post your /etc/fstab file.

---

### Post by Dynaflow on 2008-06-20
NTFS.

Do this:

```
sudo apt-get install ntfs-3g
```

---

### Post by Bigtime_Scrub on 2008-06-20
> **Dynaflow said:**
> NTFS.

Do this:

```
sudo apt-get install ntfs-3g
```

already installed

---

### Post by Bigtime_Scrub on 2008-06-20
> **iaculallad said:**
> Kindly post your /etc/fstab file.

I would love to if I knew how. I typed fstab into terminal and it said command not found. I tried getting there in the file system but it doesnt exist.

---

### Post by iaculallad on 2008-06-20
> **Bigtime_Scrub said:**
> I would love to if I knew how. I typed fstab into terminal and it said command not found. I tried getting there in the file system but it doesnt exist.

```
cat /etc/fstab
```

and post whatever it displays.

---

### Post by Bigtime_Scrub on 2008-06-20
Here it is:

```
gary@gary-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ec6641b3-85be-4c87-853e-f27b0bc9376f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=48119400-4e6d-4ef4-9ebf-0da3e05741a6 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by iaculallad on 2008-06-20
Ok, try this:

Right-click on your USBHD icon in your desktop and unmount volume.

Drop to your terminal create a mount point for your /dev/sdb1 partition:

```
sudo mkdir /mnt/USBDrive
```

Mount /dev/sdb1 to /mnt/USBDrive:

```
sudo mount -t ntfs /dev/sd11 /mnt/USBdrive
```

If mounted, try to copy files to your USB drive.

---

### Post by Bigtime_Scrub on 2008-06-20
> **iaculallad said:**
> Ok, try this:

Right-click on your USBHD icon in your desktop and unmount volume.

Drop to your terminal create a mount point for your /dev/sdb1 partition:

```
sudo mkdir /mnt/USBDrive
```

Mount /dev/sdb1 to /mnt/USBDrive:

```
sudo mount -t ntfs /dev/sd11 /mnt/USBdrive
```

If mounted, try to copy files to your USB drive.



I got this back.

```
gary@gary-desktop:~$ sudo mount -t ntfs /dev/sd11 /mnt/USBdrive
ntfs-3g: Failed to access volume '/dev/sd11': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.

```

---

### Post by iaculallad on 2008-06-20
My mistake, that should be sdb1

```
sudo mount -t ntfs /dev/sdb1 /mnt/USBdrive
```

---

### Post by Bigtime_Scrub on 2008-06-20
Interesting....

```
gary@gary-desktop:~$ sudo mount -t ntfs /dev/sdb1 /mnt/USBdrive
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /mnt/USBdrive -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /mnt/USBdrive ntfs-3g force 0 0
```

---

### Post by iaculallad on 2008-06-20
You try to force mount the drive:

```
sudo mount -t ntfs-3g /dev/sdb1 /mnt/USBdrive -o force
```

---

### Post by Bigtime_Scrub on 2008-06-20
It makes no sense to me. 

```
gary@gary-desktop:~$ sudo mount -t ntfs-3g /dev/sdb1 /mnt/USBdrive -o force
fuse: failed to access mountpoint /mnt/USBdrive: No such file or directory
```

the command right before that was 

```
sudo mkdir /mnt/USBDrive
```

---

### Post by Dynaflow on 2008-06-20
Before you go any further, you might be dealing with a corrupt filesystem. 

Umount the thing and, if you have a Windows PC around, plug it into that, go to My Computer, right click on the portable drive's icon, select Properties, click the Tools tab, and do a disk check, making sure both boxes are checked for attempting repair and checking for bad sectors.  Since the drive is formatted in NTFS, it would be better to have it checked in the operating system from whence its filesystem came.

Once you've determined the filesystem isn't corrupt (might you have yanked it out of something mid-read?), then continue with this sort of troubleshooting.

---

### Post by Dynaflow on 2008-06-20
> **Bigtime_Scrub said:**
> It makes no sense to me. 

```
gary@gary-desktop:~$ sudo mount -t ntfs-3g /dev/sdb1 /mnt/USBdrive -o force
fuse: failed to access mountpoint /mnt/USBdrive: No such file or directory
```

the command right before that was 

```
sudo mkdir /mnt/USBDrive
```

Linux is case sensitive.  Look at the *D*s in "drive."

---

### Post by iaculallad on 2008-06-20
Originally, we created /mnt/USBDrive. Case sensitivity. 'd' <> 'D' in USBDrive

```
sudo mount -t ntfs-3g /dev/sdb1 /mnt/USBDrive -o force
```

---

### Post by Bigtime_Scrub on 2008-06-20
Wow. I went to bed last night because I could barley keep my eyes open it was so late. I took a fresh look at it today and now I can see all the little mistakes I was doing. This should have been an easy process. 

Bottom line is the force mount does work, case sensitivity is important. As usual the community never fails to deliver. Thank you all so very much. 

```
sudo mount -t ntfs-3g /dev/sdb1 /mnt/USBDrive -o force
```

It worked! :):KS:guitar:

---

