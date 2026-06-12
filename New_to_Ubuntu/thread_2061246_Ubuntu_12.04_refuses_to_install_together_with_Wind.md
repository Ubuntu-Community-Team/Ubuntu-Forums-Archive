---
title: "Ubuntu 12.04 refuses to install together with Windows 7"
date: 2012-09-22
forum: New to Ubuntu
---

### Post by petran79 on 2012-09-22
I have a laptop with Windows 7 Home preinstalled.

When I tried to install Ubuntu 12.04 64-bit (DVD image through USB stick) the following problem occurs:

I have two external drives connected to the laptop. When they are present Ubuntu gives me 3 options. To install side by side with Windows 7, to replace Windows 7 completely or to manually adjust the partitions.

I want Ubuntu to be installed on the same HDD as Windows 7, so I choose the first option. But then the installer  wants to install Ubuntu on the external hard drive instead. The laptops drive does not appear in this option. 

When I plug out the external hard drives, the installer gives me only two options. To replace Windows 7 or to adjust manually the Windows 7 partition. The first obviously is not an option. The latter  I refuse to do since there are so many risky options. 

Why cant the installer automatically install Ubuntu together with Windows on the internal drive where I can adjust the space available?  Is it locked by Windows 7? 

Another option would be through Wubi but it is risky having the Ubuntu boot folder on drive C: and it also limits the installation at 30 GB. Plus because I didnt know I deleted it on the desktop and Ubuntu refused to boot. Wubi should give a warning message not to delete that folder. Users think it is not needed anymore after installation.

 It was less hassle installing it again than going all that trouble to solve the issue.

---

### Post by NikTh on 2012-09-22
> **petran79 said:**
> 
Why cant the installer automatically install Ubuntu together with Windows on the internal drive where I can adjust the space available?  Is it locked by Windows 7?  
Hi ,
Probably Windows gets stronger and beat Ubuntu in this fight (just a joke) .
First off all , External Usb drives must be unplugged. 
How many partitions you have ? Are all primary ? 
You said Windows was pre-installed , so we have 2 primary partitions for sure. 
Do you have any other partitions in that disk ? (internal) 
You can see that from Ubuntu LiveUsb , click "Try Ubuntu" , open a terminal (Ctrl+alt+t) and give this command ```
sudo parted -l
```

Thanks

---

### Post by petran79 on 2012-09-22
hallo

No, in the internal laptop drive there is only one primary partition of 500 GB. Windows and installed programs occupy half the space, so I was thinking of installing Ubuntu on a 50  GB partition at least. If I choose the third option in the installer and have no other drives plugged, the Windows partition (sda) appears, ready to be modified manually.

The problem is that it does not appear in the first option in the installer, where things would be much easier. Thing is, the first option does not appear at all! As if Windows 7 does not allow the installer to create a separate partition automatically. It has either to be erased completely (second option) or modified manually (third option).

Ubuntu 10.04 allowed me to choose to install it on the same partition with Windows XP. I was given the option to adjust the free space with a slider. So it created a linux partition of my choice and the partition of Windows was reduced.  

Here though that option is only present if I plug in an external USB3 hard drive. If I want to install it on the same partition with Windows 7, I have to do it manually and things get more confusing. 

This is a major issue really, if the simplest option cant be present.

---

### Post by spjackson on 2012-09-22
The safest thing to do is to shrink the Windows partition using Windows. Then the Ubuntu installer can use the freed space to install alongside Windows.

Right-click on Computer in the Start menu, select Manage from the pop-up menu, then pick Storage->Disk Management. From here you can shrink the Windows partition to the size you want.

---

### Post by barrykgerdes on 2012-09-22
You can shrink the main HDD partition as suggested and install 12.04 along side or do what I did. Install Ubuntu as a folder in Win 7.

The last option is not available from my iso written disk (probably the same as your USB stick). However I ran the Wubi.exe directly from the instruction page of the web site directions for installing 12.04 in windows and got the same intall screen as was on earlier versions. 

I was then able to set the folder size etc. and then install from the disk (usb stick?). 12.04 installed from there without any further trouble and runs correctly when selected from the windows menu.

Barry

---

### Post by barrykgerdes on 2012-09-22
There is also the third option that I also use and that is to install VMware into Win 7 and create a virtual drive. This also works perfectly for me.

Barry

---

### Post by petran79 on 2012-09-23
I know I have those options, but the main problem is why is the easiest option not available in the installer in the first place? Namely adjust just a slider with the size you want in the main hard disk drive partition (C:)  and you are set. 


 If it is just on my system then I would not mind, but I fear this has more to do with Windows 7 stricter security

this will cost Ubuntu's user base, since the majority of users dont have separate partitions and they dont even know what this is

---

### Post by Mark Phelps on 2012-09-23
> **petran79 said:**
> I know I have those options, but the main problem is why is the easiest option not available in the installer in the first place? Namely adjust just a slider with the size you want in the main hard disk drive partition (C:)  and you are set. 
Because ... if you use a Linux utility to shrink a Win7 partition, you risk corrupting the Win7 file system.  Much safer to use Win7 to shrink the filesystem.


> If it is just on my system then I would not mind, but I fear this has more to do with Windows 7 stricter security
NOT related to Windows 7 security. The option to shrink is NOT shown when there are already 4 partitions on the drive.

> this will cost Ubuntu's user base, since the majority of users dont have separate partitions and they dont even know what this is
ALL this will cost is a little time -- spent reading HOW to do this right.

---

