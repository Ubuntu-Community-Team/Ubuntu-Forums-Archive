---
title: "PCManFM File Manager in Lubuntu no longer recognizes USB thumbdrive"
date: 2015-12-02
forum: New to Ubuntu
---

### Post by AbleTassie on 2015-12-02
I am using Lubuntu 14.04.3 LTS. I was attempting to encrypt a test folder on my USB thumbdrive using Cryptkeeper, an Encfs system tray applet for GNOME. I could not encrypt the folder and when I tried to unmount the USB drive it said it was busy. I tried to close down any folder or application that was running using the USB, but when I tried to unmount the USB drive it still said it was busy. So I removed the USB drive.

 Now there are problems with the USB drive. The USB drive used to be readable in PCManFM as a 4GB drive.  Now the PCManFM no longer really recognizes the USB drive. But if I use &#8220;Disks&#8221; under Accessories Lubuntu sees the USB drive as 67MB drive with unknown contents under dev/sdb and gives the manufacturer and serial number.  But as I said the drive is 4GB. 

 I have Windows XP on a different machine and Windows XP used to be able to read the USB drive as well. But now, if I insert the USB drive into a USB port, Windows recognizes the drive under &#8220;E, removable drive&#8221;. But  Windows XP says the drive is not formatted, and asks me if I want to format the drive. I was not sure if I should format the drive or not using Windows XP.

 

 QUESTION(S): Should I format the USB drive now in Windows XP?  Should I run chkdsk f/ in Windows or a similar program in Lubuntu? Any suggestions from anybody would be welcomed.

 

 Thanks,
 

 A.

---

### Post by yancek on 2015-12-02
What filesystem did you have on the usb drive?  If it was a Linux filesystem, windows will always do that because it doesn't recognize a Linux filesystem.  If you format it, the data is going to be gone.  Was Cryptkeeper still running when you tried to unmount?

---

### Post by AbleTassie on 2015-12-02
> **yancek said:**
> What filesystem did you have on the usb drive?  If it was a Linux filesystem, windows will always do that because it doesn't recognize a Linux filesystem.  If you format it, the data is going to be gone.  Was Cryptkeeper still running when you tried to unmount?

I do not know what file system it was, but I think both Ubuntu and Windows was able to mount the usb drive. I am not sure if Cryptkeeper was still running when I tried to unmount.

Thanks,

A.

---

### Post by sudodus on 2015-12-03
I think the pendrive's file system was damaged when you unplugged it without unmounting.

If Windows was able to mount the USB drive before it was damaged, it it a good guess, that it has a Microsoft file system, and it should be repaired using Windows. What happens if you run the following command (in Windows)?

```
chkdsk /f X:
```

where X: is the drive letter for the pendrive.

If that does not help, you should decide if there are some valuable files on the drive, that must be recovered. If that is the case, we can discuss how to recover files without a file system or use some advanced tool and try to repair the file system.

Otherwise you can simply create a new partition table and file system (re-format) the pendrive. ***gparted*** should do the job. If not, you can start by wiping the first megabyte, and after that create a new partition table and file system using [mkusb](https://help.ubuntu.com/community/mkusb).

---

### Post by AbleTassie on 2015-12-03
> **sudodus said:**
> I think the pendrive's file system was damaged when you unplugged it without unmounting.

If Windows was able to mount the USB drive before it was damaged, it it a good guess, that it has a Microsoft file system, and it should be repaired using Windows. What happens if you run the following command (in Windows)?

```
chkdsk /f X:
```

where X: is the drive letter for the pendrive.

If that does not help, you should decide if there are some valuable files on the drive, that must be recovered. If that is the case, we can discuss how to recover files without a file system or use some advanced tool and try to repair the file system.

Otherwise you can simply create a new partition table and file system (re-format) the pendrive. ***gparted*** should do the job. If not, you can start by wiping the first megabyte, and after that create a new partition table and file system using [mkusb]("https://help.ubuntu.com/community/mkusb").

If I run ckdsk /f as you suggest I get back:  
"The type of file system is RAW, chkdsk is not available for RAW drives"

I would like to salvage the data on the drive, how do I do that?

Thanks,

A.

---

### Post by sudodus on 2015-12-03
At [http://www.cgsecurity.org/](http://www.cgsecurity.org/) you can find ***testdisk*** and ***photorec*** and information about them.

***testdisk*** can sometimes restore the file system. If it fails, ***photorec*** can still recover files, when the file data is still in the drive's memory (even without a file system). But the file names and directory structures are lost, and it can be a lot of work.

---

### Post by AbleTassie on 2015-12-04
> **sudodus said:**
> At [http://www.cgsecurity.org/](http://www.cgsecurity.org/) you can find ***testdisk*** and ***photorec*** and information about them.

***testdisk*** can sometimes restore the file system. If it fails, ***photorec*** can still recover files, when the file data is still in the drive's memory (even without a file system). But the file names and directory structures are lost, and it can be a lot of work.

Thanks Sudodus, I downloaded and extracted Testdisk. Shouldn it be installed using a terminal command such as:

sudo apt get install testdisk ?

A.

---

### Post by sudodus on 2015-12-04
You should run these programs from a live drive. So boot from a DVD or USB pendrive and install testdisk and photorec (temporarily) into that system, or get an iso file with them already installed.

It is also described at the following link

[TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

---

### Post by Bucky Ball on 2015-12-04
Or grab [SystemRescueCD]("http://www.sysresccd.org/SystemRescueCd_Homepage") which includes both Photorec and Testdisk. Create install media and boot from that. Runs like a customised Xubuntu session.

---

### Post by AbleTassie on 2015-12-04
OK thank you Sudodus and BuckyBall. I actually have used a rescue disk for Windows XP after using Linux several years ago. So I am somewhat familiar with rescue disks. My Windows XP Drivers/Applications DVD that came new with my other laptop got corrupted somehow. In any case, using Linux instead was a good development out of the whole thing. I was eventually able to "rescue" my Windows XP. But I don't think I'll ever go back to Microsoft, except as an operating system I may use occasionally. 

It will probably take me a few days to burn and try the rescue disks, because I am away from home. But I'll let you know how it goes.

Thanks again,

A.

---

