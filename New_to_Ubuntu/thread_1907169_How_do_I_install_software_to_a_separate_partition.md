---
title: "How do I install software to a separate partition?"
date: 2012-01-10
forum: New to Ubuntu
---

### Post by alockrem on 2012-01-10
As the forum topic suggests, I am new to the world of Linux.  I have chosen to install Ubuntu 11.10.

I am using a work laptop and am afraid of causing problems with windows if I dual boot.  Instead, I decided to install Ubuntu on a 16 Gb flash drive and run it from there.

The installation works fine, but I am struggling to install software (Eclipse to be exact).  I keep getting errors that I have no more room on the hard drive.  I have over 13 Gb free and I'm not sure how to resolve this.

I have a 40 Gb partition on my permanent hard drive that was formatted and is accessible to Ubuntu.  I would like to install software there or on the remaining 13 Gb of the flash drive if possible.  I'm not sure what setting to update.

Thank you for any assistance.

---

### Post by Paqman on 2012-01-10
16GB should be plenty to run an Ubuntu system. Where are you reading that you have 13GB free? You can have a good look at what files are taking up what space by launching the Disk Usage Analyser as root. Hit Alt-F2 and type:
```
gksu baobab
```

---

### Post by alockrem on 2012-01-10
I get an error that the disk only has 14.5 Mb free.  When I open the disk usage analyzer it shows:

Total filesize capacity: 16.9 GB (used: 3.5 GB available: 13.4 GB)

The / directory is highlighted in red  and shows 100% usage.  It shows 8.4 GB in the size column, which is obviously wrong.

When I click "Scan Home" it shows:

ubuntu - Usage is red (100%).  Size = 1 GB.  Contents = 37 items

Any help is appreciated.

---

### Post by alockrem on 2012-01-11
I'm not sure if my response was made at a bad time or if my issue is too complicated to resolve over a forum conversation.  If you know that it is too complicated please let me know.

Thank you

---

### Post by Mark Phelps on 2012-01-11
In Linux, you install software various ways, including using the Software Center, but unlike as with Windows, you're not given a choice as to WHERE to install it. There is no single equivalent to Program Files in Linux.

---

### Post by mastablasta on 2012-01-11
> **Mark Phelps said:**
> In Linux, you install software various ways, including using the Software Center, but unlike as with Windows, you're not given a choice as to WHERE to install it. There is no single equivalent to Program Files in Linux.
 
 
To continue PC-BSD seems to have such an option, however that is not Linux but BSD based OS. In linux libraries from different programmes are shared. so porgammes have to be installed on same place as i understand it.

---

### Post by Kniveau600s on 2012-01-11
Try installing/repairing/updating your program with the following command, just use your Console (it will prompt for your password):

```
sudo apt-get update
sudo password for User:
sudo apt-get install eclipse eclipse-jdt
```

Hope that works, but are you only installing Eclipse? It seems you may need additional packages and if so you may install them in the same way.

I agree Ubuntu doesn't prompt you for any "location installing".:popcorn:

---

### Post by ratcheer on 2012-01-11
I am not sure what all you are installing, but on my system, most software is in the /usr directroy (2.9 GB of 4.2 GB total used in root). To answer your original question, if you want your software installed in a separate partition, the best thing to do would be to migrate /usr to its own partition. This is almost always done on professionally administered UNIX systems.

Tim

---

### Post by oldfred on 2012-01-11
Did you just do a liveUSB install not a full install?

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

How to create a bootable Ubuntu USB Flash Drive
[http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/](http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

---

### Post by Mark Phelps on 2012-01-11
Sorry folks ... not meaning to be argumentative ... but this is specifically a question about Linux, not about BSD, and not about Unix.

I tried my best to give a "simple" answer -- one that would not confuse the OP, as this is ABT, and here, the more details we provide, the more we run the risk of confusing folks.

So, if anyone is aware of how you can designate different "target" SW installation folders in "Linux", I'd be glad to hear that -- as I am personally unaware of how to do that (apart from modify installation scripts).

In the absence of that info, I revert back to my original answer to the OP's question with -- you can't (install to a separate partition, that is).

---

### Post by alockrem on 2012-01-11
Thank you everyone for all of your help.  It sounds like the educated Linux user may have some options that are far beyond my ability level at this point.

Is it easier to update the partition sizes?  Based on my stats I posted above, is there something I can do to access the 13 GB for software installations?  Changing partition sizes is what I'm imagining.

Thank you again for all of your help.

---

### Post by mlentink on 2012-01-11
I think you should ask a different question.
16GB is ample for an ubuntu installation, including quite a bit of software. Installing Eclipse should not set you back that much, perhaps 500MB max. My filesystem uses up 7.6GB at present, with quite a bit of software. 

So... what's taking up so much space in yours? E.g. have you deleted a lot of files using sudo? I'd take a look at that first, before contemplating complex methods of installing stuff in non-standard ways.

---

### Post by Mark Phelps on 2012-01-11
> **alockrem said:**
> Is it easier to update the partition sizes? 
Two tools that can be used to do partitioning changes are GParted (Gnome Partition Editor) and Disk Utility.  The first has to be installed, as it is not included by default anymore.  The second is included by default.

However, to change a partition that is in use (as would be the case with the Linux partition containing the OS -- when Ubuntu is running from the hard drive), you have to make sure it is not mounted.

This means, to make changes to the Ubuntu OS partition, you need to boot from CD or USB -- and run the partitioning app from there.
>  Based on my stats I posted above, is there something I can do to access the 13 GB for software installations?
If the 13GB partition is NOT the one in which you installed Ubuntu, then I revert to my original answer -- NO.

However ... that said, unless you installed Ubuntu into a really small partition (e.g., 4GB), you should have plenty of room still there to install other apps.

---

### Post by gordintoronto on 2012-01-11
Could you open a terminal window and enter this command:
df -h

Then paste the results into a message here.

There was a relevant question asked: how did you create the flash drive? Did you actually "install" Ubuntu, or use a program which creates a bootable flash drive, such as Pendrive?

A command which might help a bit:
sudo apt-get clean
will remove any .deb files from any updating you have done. They are no longer needed.

---

