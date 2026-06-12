---
title: "Hard drive not found by Live disk on crashed windows 8"
date: 2016-09-04
forum: New to Ubuntu
---

### Post by jerryl2 on 2016-09-04
Windows 8 froze on Desktop with blue install wheel still spinning.  Waited 30 minutes, no change.  Closed computer by press and hold power button.  On restart, nothing comes up but the Acer logo, and no more activity.  Tried "refresh", nothing.  Went into bios, changed safe start to disable, and installed Ubuntu Live USB on thumb drive and booted it.  On the Files page, no hard drive appears.  Under "Network" there is an icon labeled Windows Network, but double-click brings up UNABLE TO ACCESS LOCATION.  Failed to retrieve share list from server: No such file on directory.  Does this mean that the hard drive is totally incapacitated?

---

### Post by Bashing-om on 2016-09-04
jerryl2; Hello; And Welcome to the forum ;

Not enough info to make any call yet.

Let us see what we can learn about that hard drive.
Boot the ububtu liveUSB in the - "try ubuntu" mode to the desk top -> key combo ctl+alt+t to gain a (C)ommnad (L)ine (I)interface,
Post back - between code tags -  the terminal outputs of :
```

sudo parted -l
sudo blkid

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
As a place to start. See where we can go from here.

[INDENT][INDENT]establish what we are standing on
[INDENT][INDENT][INDENT]then push
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2016-09-04
Are you dual booting Windows 8 with Ubuntu? If so, then Windows fast startup (hibernation) should be off. Otherwise even if ubuntu was detecting the hard disk it would not be able to access any windows partition. The file manager would show the partition in an unsafe state.

You could try the Disks utility from a live session. Does that detect the hard drive?

Regards

---

### Post by jerryl2 on 2016-09-04
Thank you both for your response: 

graham - No, I am not dual booting.  Windows fast startup is off.  The Disks utility does not find the hard drive.  It finds the CD/DVD drive (which is empty), the thumb drive with Ubuntu on it and the 1.5 GB loop dev.

Bashing-om - Here is what I got: parted -l gave me the thumb drive with Ubuntu on it and blkid gave me:
/dev/sda1: LABEL="UUI"  and: /dev/loop0:  TYPE="squashfs"

I am totally new to Ubuntu so please bear with me if I seem a little slow to understand something.

Thanks.

---

### Post by Bashing-om on 2016-09-04
jerryl2; Sorry;

If parted (PARTition EDitor) does not see that hard drive, I do not know what one can do .
Have you checked the cable connections ?
Does the firmware (bios) see the drive - bios post messaging enabled ?

can you change the sata port that the cable is plugged into ?

If bios does not see the drive, can not tell the operating system about it .

[INDENT][INDENT]all starts in bios
[/INDENT][/INDENT]

---

### Post by jerryl2 on 2016-09-04
Looks like it's a dead drive.  I have important files backed up, but there is a nagging thought that there might be something in there somewhere that I would like to have.  But I have spent enough time on it.  I will open up the case to see if all cables are tight, but it hasn't been moved for a year or two so I doubt if that is the problem.  When I look in the bios, I do not see the hard drive referenced anywhere, and I suppose that tells the tale.  I didn't know they just suddenly quit with no warning like that.

Thanks again for your help.
Jerry

---

### Post by Bashing-om on 2016-09-04
jerryl2; Yeah;

Bad things do happen.
Loose connection from vibration ( I switched to locking sata cables due to that )
Failed sata controller
bad sata port 
failed sata cable
dust shorting out the sata circuitry
hard drive controller gave up the ghost

and the list goes on and on and on

Gotta get bios to see the hard drive . If ya got another good drive around .. easiest is to spare that drive off and see if bios then sees the hard drive.

[INDENT][INDENT]fault isolation
[INDENT][INDENT][INDENT]to restoration
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

