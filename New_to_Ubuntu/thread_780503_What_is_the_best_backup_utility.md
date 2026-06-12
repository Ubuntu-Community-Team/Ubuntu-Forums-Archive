---
title: "What is the best backup utility?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by mac9416 on 2008-05-03
Any suggestions?

---

### Post by SlappyPappy on 2008-05-03
Dude, you have options.

[http://www.debianhelp.co.uk/backuptools1.htm](http://www.debianhelp.co.uk/backuptools1.htm)

I'm just starting to sort through this myself so I haven't picked one yet as the best. Happy hunting!   :)

---

### Post by mac9416 on 2008-05-03
Thanks, dude, but yikes! Those are all a little over my head. Can anyone point me to something that will be kind of like a RAID on one HD. So, if I goof up one installation I can just use GRUB to boot to the same thing except yesterday's version.
I can figure out the partitioning thing, but I need your opinion. What is the simplest backup utility that can do want I want?
Thanks for any help!

---

### Post by FreewheelinFrank on 2008-05-03
I was looking for a simple backup program myself: I might try this-


[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)

---

### Post by mac9416 on 2008-05-03
I have used that, but didn't have such good luck with it.
What I really want is a RAID-without-a-RAID setup. Something that will make a 1:1 copy of one partition to another, so there is no down-time. It doesn't sound that complicated to me, but maybe there's something about it I don't know (everything, probably :) ).

Tanks for the good will anyway, Frank.:KS

---

### Post by FreewheelinFrank on 2008-05-03
No problem- hope you find what you're looking for!

---

### Post by mac9416 on 2008-05-03
I ahve been watching another thread: "Which is the "best" program for complete backup?", and here's what they're saying:

> Re: Which is the "best" program for complete backup? 

--------------------------------------------------------------------------------

partimage
pros: fast, reliable, full partition backup and restore. Can be run from command line or nursors interface. option to compress image.

cons: must be run from a live CD, ancient ncursors interface. Full - all or nothing backup and restore (cannot selectively restore individual files).

What can I say? partimage is what I use before making major changes to my system such as the every 6 month distribution upgrade.


I just couldn't force myself to backup using a live disc. I'll keep looking.

---

### Post by HotShotDJ on 2008-05-03
> **mac9416 said:**
> Any suggestions?What is "best" truly depends upon your specific needs.  For my home systems (one laptop and one desktop) I use the built in rsync command via a simple bash script to make backups to an external USB or Firewire harddrive.  Don't panic... it sounds harder than it is.  You will need an elementary knowledge on how to operate within a terminal, but again, what you will be doing here is really very easy.

Step 1: Create your bash script
[LIST=1]
[*]Open "Places --> Home Folder"
[*]Right-click in an empty area.  Select "Create Folder"
[*]Name the newly created folder "bin" (no capital letters!)
[*]Open the the "bin" folder.  Right click in an empty area. Choose "Create Document" and then "Empty File"
[*]Name the newly created empty file "backup"
[*]Open "backup" by double-clicking on it
[*]Copy the following code into the file
[/LIST]```
#!/bin/bash
rsync -ap --delete-excluded --delete --progress --stats /home /media/USBDRIVE
```
[LIST]
[*]IMPORTANT!  Change "USBDRIVE" to the path on your computer.  You can easily determine this by plugging in your USB drive.  When nautilus opens, simply click on the "paper & pencil" icon to the left of the media discription (just below the Tool Bar) to toggle the Location Bar to show the complete path.
[*]NOTE: You can limit the script to just backing up a single user rather than the entire "home" directory by changing "/home" to "/home/USER" (of course, changing USER to the correct user name).
[*]NOTE: You can also exclude certain directories and/or file types using an exclude file. That, however, complicates things a bit and is beyond the scope of this post.
[/LIST]
Step 2: Make Executable and Run
[LIST=1]
[*]After you have saved and closed the file you just created, right click on its icon.
[*]Choose "Properties" (at the bottom of the pop-up menu).
[*]Now, at the top of the "Properties" dialog, click on the "Permissions" tab
[*]Find "Execute" and then click on the check box to "Allow executing file as program"
[*]Click "Close" at the bottom right of the Properties dialog
[*]Close remaining open windows.  Unmount and remove any usb drives.
[*]Press simultaneously "Ctrl+Alt+Delete" to restart gnome (if you don't do this, your newly created "bin" directory will not be in your path -- you WANT this directory in your path)
[*]When you log back into gnome attach the external drive that you want to use for backing up your home directory.
[*]Open a terminal (Applications --> Accessories --> Terminal)
[*]Type "backup"
[*]After awhile, your entire home directory will be mirrored to your external USB harddrive.
[/LIST]
This method is only for **mirroring** your home directory. Don't try to use it on your "root" directory (/).

DISCLAIMER:  This "Works for Me."  Your Mileage May Vary. No Warranties. If this script breaks anything, you get to keep all the pieces.

---

### Post by mac9416 on 2008-05-03
That looks easy enough. Two questions:
[LIST=1]
[*]How can I make it back up to another partition?
[*]Will I be able to simply boot off of the other partition if my first one breaks?
[*]How can I automate the process to do this every day?
[/LIST]

Thanks!

---

### Post by mac9416 on 2008-05-03
Back to start...

---

### Post by HotShotDJ on 2008-05-03
> **mac9416 said:**
> [LIST=1]
[*]How can I make it back up to another partition?
[*]Will I be able to simply boot off of the other partition if my first one breaks?
[*]How can I automate the process to do this every day?
[/LIST][LIST=1]
[*]Simply replace "/media/USBDISK" with the path to another mounted partition on your system.
[*]No.  This method only mirrors your "/home" directory. I'm sure it is possible to create a bootable partition using a similar method, but I've never done it myself.  For my root partition, I use partimage once a month, or just before making significant changes to my system, using a LiveCD (you can't use partimage on a mounted partition).  My current favorite LiveCD for this purpose is [SystemRescueCD]("http://www.sysresccd.org/Main_Page").
[*]Yes.  Using Synaptic (System --> Administration --> Synaptic Package Manager), install "gnome-schedule"   Use this to automatically run the backup script on a schedule of your choosing.
[/LIST]

---

### Post by mac9416 on 2008-05-03
Thanks, man.

---

### Post by HotShotDJ on 2008-05-03
I mentioned the following in a PM with the OP, but I thought I should add it to the public thread for the benefit of others who might find it helpful:

The previously mentioned SystemRescueCD can be installed to a partition on your system and then run from GRUB when you boot up.  This would be a good solution for those who want to have a bootable rescue partition without the need of having the LiveCD on hand.

---

