---
title: "External HD won't mount?"
date: 2013-02-27
forum: New to Ubuntu
---

### Post by secuono on 2013-02-27
My external HD will not mount, it told me to restart and try again, didn't help any. 

I'm using Ubuntu version 8.04, only version that will install properly on my laptop. HD is a SeaGate.

---

### Post by kevdog on 2013-02-27
How is your external hard drive connected?  Via usb or other interface?

---

### Post by secuono on 2013-02-27
Usb.

---

### Post by secuono on 2013-02-28
I'm guessing it won't work unless I redo something. Do they make flashdrives compatible with linux and windows?

---

### Post by collisionystm on 2013-02-28
The drive should mount fine. When are you getting the 'restart and try again' message? The hard drive might be formatted with an NTFS partition and with having 8.04 you may need to manually install NTFS support. Just out of curiousity, what model laptop do you have? I am just wondering why you were not able to install something more recent. Even 10.04, which reaches an EOL in April would be far better than 8.04.

---

### Post by secuono on 2013-03-01
Whenever I plug it in, a window shows saying 
"cannot mount volume. >details 
$logfile indicates unclean shutdown [0,0] failed to mount '/dev/sdb2': operation not supported mount is denied because ntfs is marked to be in use. choose one action: choice 1: if you have win, disconnect by using safely remove hardware and then shut down win cleanly. choice 2: if you dont have win, use force option at your own risk. "




"manually install NTFS support"
 How do you do that and would that erase the stuff already on the drive?

Laptop is a Gateway cx210x

---

### Post by Mark Phelps on 2013-03-01
You should try two things ...

First, don't just unplug it in Windows, but safely remove it.  Then, plug it back in and see if the same error message is shown.

Second if that doesn't fix it, you would need to run CHKDSK in Windows -- as there is no equivalent for doing this in Ubuntu.  To do that, when the drive is connected in Windows, in Computer, right-click the drive, select Properties, and then select the option to scan the drive and fix errors.  And THEN ... safely remove it.

When you then connect it in Ubuntu, you should see it OK.

---

### Post by Bashing-om on 2013-03-01
secuono; Hi ! Welcome to the forum.

Indications are that when you last used the usb device (in Windows) you failed to "safely remove" the drive.
The easier solution is to replace the usb drive in a windows machine and "safely remove" there. There are ways to do it from ubuntu.. but it is a rather involved process and doing it from the native windows environmnet is the recommeded method.

The above post are correct that in order for 8.04 to cope with window's file system "ntfs", the proper packages must be installed in ubuntu.
In addition as the file system is "ntfs" will require mounting the file system (fat will auto mount).

As support for 8.04 is ending, might I suggest that you see about upgrading to 12.04 ?
Check system requirements to see if or what version of 'buntu you can run on perhaps older hardware.
[INDENT=2]hope this helps

[/INDENT]

---

### Post by secuono on 2013-03-01
So plug it into windows first, remove it safely, then plug it into ubuntu?

---

### Post by Bashing-om on 2013-03-01
secuono;

Yes and no... see Mark's most excellent advise... "safely remove" the drive in windows then run window's check disk utility on the usb drive prior to unplugging it. Then see what results when plugged into ubuntu ... as it is "ntfs" file system it may not mount without installing the ntfs-3g tools AND mounting the drive manually or making edits to ubuntu filse system table to recognize the drive. [INDENT=2]just try'n to help

[/INDENT]

---

