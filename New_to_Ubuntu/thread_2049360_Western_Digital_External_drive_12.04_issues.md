---
title: "Western Digital External drive 12.04 issues"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by intoutdoor on 2012-08-28
Hello,

    I've searched the forums and have found somewhat relevant information pertaining to older distros of ubuntu, but none for 12.04.  I understand that Western Digital external drives are not kind to linux. I was just curious if anyone knew of any fairly simple (I'm new to ubuntu and not a skilled computer guy) resolutions.  I no longer have a windows on my machine, so I can not easily go into the WD and remove the native software on it.

Any hints would be very much appreciated

Thanks

---

### Post by mkstallings1 on 2012-08-28
If it is empty, you could use Gparted to reformat the drive.  That would remove any software already on it.

---

### Post by cmcanulty on 2012-08-28
if it just isn't mounting properly these commands have helped me
```
sudo killall udisks

sudo apt-get install udisks libgdu0 gnome-disk-utility policykit-desktop-privileges --reinstall
```

---

### Post by intoutdoor on 2012-08-28
excellent. thank you guys. I will give it a try. It is full at the moment, but I can transfer everything to another pc.  Thank you both very much.

---

### Post by intoutdoor on 2012-08-30
I tried Gparted, but it won't recognize my drive, all that I find is my machines hard disk. I tried rebooting but that did not work.  Not sure what the problem is.  Also, to get my WD drive to work in Ubuntu, do I need to format as fat32 or ext3?

Thanks guys!

---

### Post by coffeecat on 2012-08-30
> **intoutdoor said:**
> I understand that Western Digital external drives are not kind to linux.

As a generalisation that is not so. I have used a couple of WD external drives with Ubuntu and they work out of the box. However, a couple of years ago WD had a range of external drives that had some sort of pseudo-partition in flash memory which did something allegedly useful in Windows, but which caused real problems in both Linux OSs and in MacOS. I can't remember the precise details or the name of the product line that was the problem, but if you post details of the exact model of WD drive you have that might help. You might have one of those.

> **intoutdoor said:**
> I tried Gparted, but it won't recognize my drive, all that I find is my machines hard disk.

That's a significant observation. Plug the WD drive in and switch it on. Wait a few seconds and then run these two terminal commands:

```
dmesg | tail
sudo fdisk -lu
```

Post the output between [noparse]```
 and 
```[/noparse] tags to preserve formatting and for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar. For ease of pasting into your post, highlight the output with your mouse, right-click -> copy.

---

### Post by intoutdoor on 2012-08-30
Thank you coffeecat.

I did as you said and got the following:

```
[ 1852.701550] sd 8:0:0:0: [sdb]  Sense Key : Data Protect [current] 
[ 1852.701553] sd 8:0:0:0: [sdb]  Add. Sense: Logical unit access not authorized
[ 1852.701556] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[ 1852.701561] end_request: critical target error, dev sdb, sector 0
[ 1852.702423] sd 8:0:0:0: [sdb] Unhandled sense code
[ 1852.702426] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[ 1852.702428] sd 8:0:0:0: [sdb]  Sense Key : Data Protect [current] 
[ 1852.702430] sd 8:0:0:0: [sdb]  Add. Sense: Logical unit access not authorized
[ 1852.702434] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[ 1852.702438] end_request: critical target error, dev sdb, sector 0
mack@mackmachine:~$ sudo fdisk -lu
[sudo] password for mack: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005c483

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   968816639   484407296   83  Linux
/dev/sda2       968818686   976771071     3976193    5  Extended
/dev/sda5       968818688   976771071     3976192   82  Linux swap / Solaris
```


Though I don't see where it says code as you mentioned.  

Thank you so much for the help.  As a new user to ubuntu and linux in general, this site is invaluable!

---

### Post by coffeecat on 2012-08-30
You haven't posted this requested information:

> **coffeecat said:**
> I can't remember the precise details or the name of the product line that was the problem, but if you post details of the exact model of WD drive you have that might help. You might have one of those.

First...

> **intoutdoor said:**
> Though I don't see where it says code as you mentioned.

I've added the code tags for you, but please read my post again. You either type [noparse]```
 and 
```[/noparse] either side of the terminal output or you can use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar. It makes your posts easier to read and helps those helping you. The code tags are one of many so-called BBCodes - see the link in my sig.

Anyway, to your problem. This:

```

[ 1852.702438] end_request: critical target error, dev sdb, sector 0
```

... is significant. /dev/sdb would be your WD drive. Since Ubuntu cannot mount it, for whatever reason, you won't be able to reformat it until we find out what's wrong. Apart from giving us the WD model name and number, does it still work with Windows?

---

### Post by Mark Phelps on 2012-08-30
Sorry to be the bearer of bad news -- but in many cases, WD drives come with an app that only runs in Windows and prompts you for a password to access the drive.  That is because some drive use hardware encryption and the app is the front-end that must be used to gain access to the data.

You should plug in this drive to a Windows PC and see if a Window opens.  That may give you an option to remove the password.

---

### Post by intoutdoor on 2012-08-30
My apologies coffeecat.  I could not locate the message bar with the # sign.  I understand that you are trying to help me in the simplest means possible, but unfortunately the bit about Code was still over my head, I didn't quite know what that meant, so I just copied and pasted straight from the terminal, and it looked like it did in the terminal so I thought that would suffice. Again, my apologies.

The model is 4610B.  I've opened it in my wifes windows netbook, and it works properly, but does not give an option that I can find to remove the password, which as noted is an .exe file.  Thank you guys for your continual help.

---

### Post by Hadaka on 2012-08-30
hi, here is a link to unlock a western digital drive.
[http://www.ehow.com/how_6120791_unlock-western-digital-hard-drive.html](http://www.ehow.com/how_6120791_unlock-western-digital-hard-drive.html)

further research discovered this link still requires the password.
but...i did find a thread that posted master ata passwords..it an older thread
but might be worth a try..

WDCWDCWDCWDCWDCWDCWDCWDCWDCWDCW <----THIS ONE WORKED FOR ME
WDCWDCWDCWDCWDCWDCWDCWDCWDCWDCWD
&'()*.WDCWDCWDCWDCWDCWDCWDCWDCWDCWDCWD

try these 3, and see if that works.

---

