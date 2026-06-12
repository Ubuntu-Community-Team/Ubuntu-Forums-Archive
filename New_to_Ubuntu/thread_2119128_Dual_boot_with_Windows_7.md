---
title: "Dual boot with Windows 7"
date: 2013-02-23
forum: New to Ubuntu
---

### Post by nineball69 on 2013-02-23
I am new to linux and want to install it on my laptop. I have downloaded ubuntu from ubuntu.com and saved it on a CD. 

I am using windows 7 and would like to keep it as well. I guess this means I will have a dual boot. Do I need to create a partition in Windows 7 to load ubuntu? If so there lies my problem. My drive already has four partitions (C, system, recovery, hp_tools) and when I try to create the partition I will give for ubuntu I get the warning message " " The operation you selected will convert the selected basic disk(s) to  dynamic disk(s). If you convert the disk(s) to dynamic, you will not be  able to start installed operating systems from any volume on the  disk(s) (except the current boot volume). Are you sure you want to  continue?"

My question is whether I need to create a partition on my system before starting to install ubuntu? If that is a yes, should I ignore the warning message and create the partition OR delete one of the partitions? Deleting one of the partitions is a question by itself.

OR, can I just forget everything and install ubuntu and let it take care of everything.

Thanks.

---

### Post by carl4926 on 2013-02-23
Backup first. And defrag windows.

You need to delete one of the partitions. You can copy/backup it's contents first. But the one I would choose is the HP tools.

You can now shrink windows C to create some unallocated space. Do this in windows.

Next use Gparted to create an extended partition in all the unallocated space.
Then create logical partitions for Ubuntu in the extended space

You need:
swap 2GB or more but not more than 2xRAM
ext4 to use all the remaining space will be for Ubuntu

---

### Post by mapes12 on 2013-02-23
> OR, can I just forget everything and install ubuntu and let it take care of everything.Basically, yes. 


A couple of pre requisites:


1. make sure you have backed up anything you do want to lose from your windoze data.

2. make sure you have your windoze install media and activation key in case you need to reinstall it.


Then go ahead and boot your machine from the live media (CD or USB). The installer will ask if you want to install alongside windoze. Select yes and the installer will do the rest for you including setting up swap.

---

### Post by offgridguy on 2013-02-23
> **nineball69 said:**
> 

OR, can I just forget everything and install ubuntu and let it take care of everything.

Thanks.
Absolutely not, as previously suggested you need eliminate 1 partition as you already have the maximum of 4, Use windows Disk management to edit your windows Partition's and create unallocated space. 

When you install from the live CD, the installer will install to the unallocated space and create the neccesary partitions, home,swap,etc.

gparted tutorial here.
[http://dedoimedo.com/computers/gparted.html](http://dedoimedo.com/computers/gparted.html)

---

### Post by audiomick on 2013-02-23
> **nineball69 said:**
>  
... can I just forget everything and install ubuntu and let it take care of everything.


This wont work because of this

> My drive already has four partitions (C, system, recovery, hp_tools)


You will need to delete one. As far as I know, as the warning you quoted said, if you let the installer make dynamic partitions out of the existing ones, you wont be able to boot your Win7 anymore.

Carl's suggestion to remove the HP tools is ok I suppose, although I don't know what is in there. I gather that once you have used the Windows facility to create a recovery CD, you can remove the recovery partition. That is what I did on my Netbook, I think, but I was also not that concerned about the Win7 on there. 

You should:
Do some house cleaning on the Win7 install. Get rid of any files you don't need any more. Make as much space as you can available.

Backup anything important while you are at it.

Do a de-frag.

Make sure you have backed up anything important.

Use THE WINDOWS TOOL to shrink the Windows partition that your Win7 is on, and remove the partition you have decided to get rid of. While your are at it, move the partitions such that all the empty space is in one spot together. I would aim to have it at the end of the drive.

Boot into Windows a couple of times to let it run it's disk check thing if it wants to.

From here on, you can run the installer and tell it "install beside", I think. I prefer to go into the "someting else" option and do the partitioning manually.

Further to that, I prefer to set up some partitions before I even start the installer. This can be done using Gparted from the live environment, which is the "try ubuntu" option from the CD (or USB) installer medium.

If you remove on partition, you will need to create an extended partition and then logical partitions inside that. You will need at least a system partition to be mounted at /, and a swap partition to be mounted at /swap.

Don't worry too much about what "mount" means. It means the point where a directory is attached to the file system. What you have to do is self evident when you get to the partitioning bit of the install.

Further to those two, I like to make a separate partition for /home.

How big to make swap is a thing to be decided. If you want the machine to be able to hibernate, you will need swap a bit bigger than your RAM. If you don't need to hibernate, about 1GB swap is likely to be enough, except if you do really intense Video editing or something. Swap gets used when the RAM gets full, and from what I have read most people don't get even close to getting the RAM full during "normal" use with a modern amount of RAM.

I would do
swap a bit bigger than RAM
about 10 - 15 GB for the system mounted at /
the rest for the home partition mounted at /home

---

### Post by offgridguy on 2013-02-23
+1  to the post by audiomick.   In case you missed it please read the gparted tutorial
here.

[http://dedoimedo.com/computers/gparted.html](http://dedoimedo.com/computers/gparted.html)

---

### Post by oldfred on 2013-02-23
Good advice above. If you want more detail some links.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

    
       Install options, Do not use erase entire drive unless that is really what you want.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 

    
       Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by offgridguy on 2013-02-23
@ oldfred, i really have to admire your organization of handling all these resources.:D

---

### Post by audiomick on 2013-02-23
Me too.

---

### Post by nineball69 on 2013-03-12
Thank you all for the replies. Got caught with some things and now just reading some of the replies. Let me read some more and will post a more detailed reply of what I have gathered here and elsewhere.

---

### Post by Cheesemill on 2013-03-12
> **offgridguy said:**
> @ oldfred, i really have to admire your organization of handling all these resources.:D

+1

I'm sure he has a massive document full of links somewhere, he always manages to come up with the goods no matter what the question.

---

### Post by oldfred on 2013-03-12
Thanks, but it is more that oldfred's memory is not what it used to be and recall never was a strong point. But recognition was pretty good. So I just search notes, and regularly try to update them with all the new better info the rest of you post.

I used to just have a bunch of text files with gedit, but now converted them to zim which lets me check links easier.

---

### Post by tejpatel98 on 2013-03-12
You can also use Wubi which is designed for running along side Windows. It is found on Ubuntu's website.

---

