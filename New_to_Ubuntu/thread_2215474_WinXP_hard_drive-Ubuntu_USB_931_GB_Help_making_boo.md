---
title: "WinXP hard drive-Ubuntu USB 931 GB Help making bootable"
date: 2014-04-06
forum: New to Ubuntu
---

### Post by firefoxm54a2 on 2014-04-06
I have downloaded the ubuntu-12.04.4-desktop-1386 ISO image file onto the USB drive. How can I make it bootable? The instructions I read up on appear to be ubuntu programs. So, how do I use XP commands to make it bootable, or is there some software that I can get that will work on XP?  I would like to initially make it so I can run ubuntu off the USB, but also be able to boot up the XP and run it off of the hard disk.  Thank you very much for any help.

---

### Post by quadrplax on 2014-04-06
Are you saying you want to run Ubuntu on a flash drive always (like me), or install it to the hard drive in addition to XP?

---

### Post by firefoxm54a2 on 2014-04-06
Yes, initially I want to run ubuntou off of the flash until I learn enough to be able to convert over without loosing anything.

---

### Post by quadrplax on 2014-04-06
Well, in that case, you should make an Ubuntu Live CD. The easiest way to do this I know of is here: [**[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)**]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")
From the Live CD you can try Linux, and install it later. However, a Live CD is not recommended for long term use, and it resets data every time you reboot. Let me know if you want a persistant USB drive.

---

### Post by firefoxm54a2 on 2014-04-06
I would prefer to make the USB drive bootable and just run off the USB drive until I get  comfortable with ubuntu.

---

### Post by SuperFreak on 2014-04-06
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows")

---

### Post by quadrplax on 2014-04-06
Well, in that case you're going to need two USB drives, a 2GB+ one and an 8GB+ (preferably more) one. Create the Live CD with that installer on the smaller one, and use it to install Ubuntu to the large one. I found a tutorial that explained in-depth how to do that, but I'm having trouble finding it now.

EDIT: I found the tutorial (Slightly modified, original: [http://ubuntuforums.org/showthread.php?t=1708283](http://ubuntuforums.org/showthread.php?t=1708283))

* Turn off and unplug the computer. (See note at bottom)
* Remove the side from the case.
* Unplug the power cable from the hard drive.
* Plug the computer back in.
Insert the Live CD.
Start the computer, the CD should boot.
Insert the larger flash drive.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
(Optional partition for use on Windows machine)
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000MB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = "/windows".
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1000MB, Beginning, Swap Space, then OK.
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = [*Whatever is left*]MB, Beginning, Ext4, and Mount point = "/" then OK.
[B](Important)
Confirm "Device for boot loader installation" points to the USB drive.[/B]
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select forward.
Wait until install is complete.
* Turn off computer and plug in the HDD.
* Stick the side panel back on.


*These steps shouldn't really be necessary, and if you don't have experience with hardware I defiantly don't recommend it. Just be **very** careful that you're installing to the flash drive and not the hard drive, or else I think it will wipe it.

---

### Post by firefoxm54a2 on 2014-04-06
Thanks everyone! Once I realized that the UUI program was a .exe, thanks to SuperFreak, I downloaded it and installed ubuntu on the USB. Now all I have to do is see if it boots.

---

### Post by firefoxm54a2 on 2014-04-07
Well, that sort of worked.I got to the screen where it asks if you want to try  on USB or install on hard drive. I selected try on USB. first time ended up with black screen. second time ended up with three different colors of random patterns. I'll try again tomorrow and see what happens.  Any suggestions?

---

### Post by Impavidus on 2014-04-07
I see some confusion here. It seems you created a live usb, which is the .iso file 'burned' to your usb drive. It's not an installed system. Live usbs are great for testing hardware compatibility and fixing your system if it's broken. They also contain some useful tools for, for example, partitioning your hard drive and also contain the Ubuntu installer. An actual install of Ubuntu would require either a second usb drive to install it on usb, a second hard drive to install it there, or repartitioning your current hard drive to put Ubuntu next to your existing Windows XP. Changing the partitions is quite easy on most WinXP machines.

Now, concerning your black screen or random colours, this is a graphics driver problem. What graphics hardware is present in that computer?

---

### Post by quadrplax on 2014-04-07
If you follow my tutorial instead of using the "Try Ubuntu" feature, then it will be a lot more stable. A Live CD is not good for normal use.

---

### Post by firefoxm54a2 on 2014-04-07
OK, I was confused by the term CD and assumed it meant disk as in optical disk and not an equivalent for a USB stick or drive.  I found a USB stick I had that has 3.77 GB of space on it, so I can try your tutorial method but first I think I need to resolve the graphics problem.  How do I list out the hardware specs on this machine? It was a gift from a friend.  Thanks!

---

### Post by firefoxm54a2 on 2014-04-07
Here is the info on the graphics controller:    Name    Intel(R) 82845G/GL/GE/PE/GV Graphics Controller PNP Device ID PCI\VEN_8086&DEV_2562&SUBSYS_57781462&REV_03\3&13C0B0C5&0&10  Adapter Type    Intel(R) 82845G Graphics Controller, Intel Corporation compatible Adapter Description    Intel(R) 82845G/GL/GE/PE/GV  Graphics Controller Adapter RAM    64.00 MB (67,108,864 bytes) Installed Drivers    ialmrnt5.dll     I really appreciate all the help!

---

### Post by quadrplax on 2014-04-07
Ok, sorry, I should have specified that, Live CD is a weird term, probably because that is what they all used to be. As for the graphics issue, I don't know much about that. I think if you install it then it will come with better drivers and stuff. Also, I'm not sure 3.77GB would be enough. I know people have gotten it to work with 4GB before. Does it claim to be a 4GB drive? Because in Linux, it actually shows all of the space on the drive. If you do use that one, you might want your FAT32 and Swap Space partitions to only be 512MB, or maybe even less. Also, in case this isn't obvious, the flash drive will be wiped when you install, unless you do fancy partition resizing stuff.

---

### Post by firefoxm54a2 on 2014-04-07
Thanks! I am just using the small flash drive to install the system on the large flash drive in order to bypass installing on hard disk at this time. I posted a new thread for help with the graphics controller. Thanks again for getting back to me so quickly!

---

### Post by monkeybrain20122 on 2014-04-07
Just to warn you that Ubuntu insalled on a usb flash drive can be slow and it in no way reflects the performance of installing into the hard drive. You can get real performance if you instead install in an external hard drive.

---

### Post by quadrplax on 2014-04-08
Never thought of that because I use my flash drives on bad computers lol

---

