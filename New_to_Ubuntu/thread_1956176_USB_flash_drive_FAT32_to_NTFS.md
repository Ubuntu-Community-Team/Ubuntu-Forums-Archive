---
title: "USB flash drive FAT32 to NTFS"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by KL_72_TR on 2012-04-10
Hello everybody.
How can I format a USB flsh drive from FAT32 to NTFS.
I would like to know how can I do it in Linux.
Thank you all.

---

### Post by dniMretsaM on 2012-04-10
Use GParted. Run this:
```
gksu gparted
```(You can also run it from the menu, but you'll have to look for it.)

Once you have GParted running, select your USB stick from the drop-down list in the upper right-hand corner. Then right click on the bar that represents your USB stick and select "Unmount." Then right click again, select "Format to ->" and select "NTFS."

***Be sure you don't format your hard drive or any other important disks!***

---

### Post by lukeiamyourfather on 2012-04-10
> **dniMretsaM said:**
> Use GParted. Run this:
```
gksu gparted
```(You can also run it from the menu, but you'll have to look for it.)

Once you have GParted running, select your USB stick from the drop-down list in the upper right-hand corner. Then right click on the bar that represents your USB stick and select "Unmount." Then right click again, select "Format to ->" and select "NTFS."

***Be sure you don't format your hard drive or any other important disks!***

I'll plus one on GParted. Though I don't think it comes installed by default anymore so you might have to install it either through the Software Center or with a command (sudo apt-get install gparted).

---

### Post by papibe on 2012-04-10
Alternatively to dniMretsaM's suggestion, you can also use 'Disk Utility' to format an USB flash drive.

Regards.

---

### Post by Mark Phelps on 2012-04-11
You didn't ask, but if your question was one of "converting" from FAT32 to NTFS, and saving the data in the process, realize that reformatting will erase all the data on the drive.

---

### Post by KL_72_TR on 2012-04-11
Thank you for your suggestions.
MARK, I have everything backed up and safe.
But I met some problems. Both GParted and Disk Utility are able to format only in EXT2 and FAT32. For EXT4 and NTFS I was prompted with error messages.
I repeated the process for more than a dozen times but the results were the same.
Is there anything else I should do?

---

### Post by dniMretsaM on 2012-04-11
> **lukeiamyourfather said:**
> I'll plus one on GParted. Though I don't think it comes installed by default anymore so you might have to install it either through the Software Center or with a command (sudo apt-get install gparted).

He's on Lucid, I thought it came with Lucid. If not, well, my bad.

> **KL_72_TR said:**
> Thank you for your suggestions.
MARK, I have everything backed up and safe.
But I met some problems. Both GParted and Disk Utility are able to format only in EXT2 and FAT32. For EXT4 and NTFS I was prompted with error messages.
I repeated the process for more than a dozen times but the results were the same.
Is there anything else I should do?

Post the error messages.

---

### Post by KL_72_TR on 2012-04-11
Using GParted from FAT32 to NTFS
```
GParted 0.5.1

Libparted 2.2
Format /dev/sdd1 as ntfs  00:00:07    ( SUCCESS )
     	
calibrate /dev/sdd1  00:00:00    ( SUCCESS )
     	
path: /dev/sdd1
start: 63
end: 31728374
size: 31728312 (15.13 GiB)
set partition type on /dev/sdd1  00:00:00    ( SUCCESS )
     	
new partition type: ntfs
create new ntfs file system  00:00:07    ( SUCCESS )
     	
mkntfs -Q -v -L "" /dev/sdd1
     	
Cluster size has been automatically set to 4096 bytes.
Creating NTFS volume structures.
Creating root directory (mft record 5)
Creating $MFT (mft record 0)
Creating $MFTMirr (mft record 1)
Creating $LogFile (mft record 2)
Creating $AttrDef (mft record 4)
Creating $Bitmap (mft record 6)
Creating $Boot (mft record 7)
Creating backup boot sector.
Creating $Volume (mft record 3)
Creating $BadClus (mft record 8)
Creating $Secure (mft record 9)
Creating $UpCase (mft record 0xa)
Creating $Extend (mft record 11)
Creating system file (mft record 0xc)
Creating system file (mft record 0xd)
Creating system file (mft record 0xe)
Creating system file (mft record 0xf)
Creating $Quota (mft record 24)
Creating $ObjId (mft record 25)
Creating $Reparse (mft record 26)
Syncing root directory index record.
Syncing $Bitmap.
Syncing $MFT.
Updating $MFTMirr.
Syncing device.
mkntfs completed successfully. Have a nice day.

```
But than I see: /dev/sdd1 followed by a triangle Attention!
Right click on it > Information and this is what I get:
Information about /dev/sdd1

```
File system:	ntfs
Size:		15.13 GiB

Path:		/dev/sdd1
Status:		Not mounted
Label:		
UUID:		

First sector:	63
Last sector:	31728374
Total sectors:	31728312

Warning:
Failed to mount '/dev/sdd1': Input/output error.
NTFS is inconsistent. Run chkdsk /f on Windows then reboot
it TWICE!
The usage of the /f parameter is very IMPORTANT! No
modification was 
made to NTFS by this software.

ntfsresize v2.0.0 (libntfs 10:0:0)
ERROR(5): Opening '/dev/sdd1' as NTFS failed: input/output
error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it
TWICE!
The usage of the /f parameter is very IMPORTANT! No
modification was
and will be made to NTFS by this software until it gets repaired.

Unable to read the contents of this file system!
Because of this some operations may be unavailable.
```

---

### Post by dniMretsaM on 2012-04-11
Do you have access to a Windows machine? If you do, just run the command it told you to (note that it will probably take a long time. Windows takes forever to check/fix a disk).

---

### Post by haqking on 2012-04-11
as stated using gparted will lose the data.

If you have access to a windows machine however then just

```
CONVERT [usbdriveletter]: /FS:NTFS
```

I presume you have a windows machine as using NTFS is of no benefit to Linux use.

---

### Post by KL_72_TR on 2012-04-11
> **dniMretsaM said:**
> Do you have access to a Windows machine? If you do, just run the command it told you to (note that it will probably take a long time. Windows takes forever to check/fix a disk).
In Windows went all fine. No errors and it worked fine.
But when I came back in Ubuntu nothing had changed.
> **haqking said:**
> I presume you have a windows machine as using NTFS is of no benefit to Linux use.
I'm need NTFS because my friends have Windows
I will try everything from the start but this time from my other computer with Ubuntu 11.10.

---

