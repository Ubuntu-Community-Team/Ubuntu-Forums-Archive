---
title: "newness wearing off, USB booting lost persistence"
date: 2012-01-12
forum: New to Ubuntu
---

### Post by aka-John99 on 2012-01-12
I think it must be the [COLOR=Red]newness wearing off * :o[/COLOR]

I have Ubuntu installed successfully on a laptop,although I may change the install later ( I have a separate thread open about that
[http://ubuntuforums.org/showthread.php?t=1907858](http://ubuntuforums.org/showthread.php?t=1907858)
).

My current problem is that the laptop allows me to boot from a USB stick and I did have a USB stick that was booting, and I thought showing persistence. In fact when I boot it and look in the home folder it does have a document I created in there. I think that indicates at least initialy I had a valid and working USB stick install.

Now it gives warnings about lack of room, and if for instance I try to edit the small text file I get a red warning there is no space.

I am writing this message from the hdd installed ubuntu. I could just try to recreate the bootable memory stick again from the Live CD I have,but thought I would ask because

[LIST]
[*]there is probably a simple quick fix if I knew what I was doing
[*]I would like to figure out the cause or solution rather than just blindly reinstall on the USB
[/LIST]

[LIST]
[*]**[COLOR=Red]* Newness wearing off[/COLOR]**
A favourite phrase of a telecoms engineer I used to work with,
 much more polite than RTFM when user error is the cause of problems.
[/LIST]
The USB stick boot also may have a problem with video settings, the resolution is apparently wrong, so some windows are bigger than the screen windows, for instance the Disk utility window, and although I can drag that sideways to see all the info I don't think It would drag upwards to view the bottom of it.But that is a problem I can look at later.
 (possibly  related [http://ubuntuforums.org/showpost.php?p=11594336&postcount=11](http://ubuntuforums.org/showpost.php?p=11594336&postcount=11)

I have no idea what sort of info is needed to look into this problem but Memory Stick is 16GB Kingston formatted as vFAT. I was under the impression that the original install involved it having a SWAP partition on it, although I am not sure I see that now. When I put it in the laptop whilst the hdd Ubuntu is running it shows as a single volume of 16GB in Disk Utility.

Any help or suggestions appreciated.

---

### Post by C.S.Cameron on 2012-01-12
A typical persistent install uses a file named casper-rw for persistence.
It is limited to 4GB due to being FAT32.
Doing an update will quickly fill it.
You can delete this file and make an ext4 partition named casper-rw if you need more persistence space.
An update is still not recommended.

Another option is to do a Full install to the USB stick, this will act just like a hard drive install.

Following step by step for Full install of 11.10 to USB device, partition sizes given are for 8GB drive, adjust size to suit, you might want the first partition to be about 8GB so you can use the drive for storage and transfer with a windows machine:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the USB drive.
Insert the Live CD or Live USB.
Start the computer, the CD / flash drive should boot, (you need to adjust BIOS to boot USB).
Select language
Select "Forward".
Select Download updates while installing and Select Install this third-party software.
(Notice that at least 4.4 GB drive space is required, 4GB bootable flash drive users must choose another distro for a full install).
Forward
If prompted unmount partitions.
Select "Something else"
Forward
Confirm "Device for boot loader installation:"is correct, (If you left your internal HDD plugged in make sure the USB drive root is selected - sdb not sdb1).
(Optional Windows data partition)
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000
"Location = Beginning".
"Use as: = FAT32 file system"
And "Mount point = windows".
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
(Importent)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and enable the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.

---

### Post by aka-John99 on 2012-01-14
Thanks for the comprehensive reply

If I understand it correctly casper-rw is effectively a temp file sytem.
How does Ubuntu handle updates on a USB install, does it keep the original distro files and merely make changes  within casper.
Or are files elsewhere updated added to or rewritten as required, and is it then possible some updates will persist if casper is removed or replaced?
 
As a newbie I have many gaps in my knowledge that need filling, and new concepts to understand.

The laptop is new and under warranty. Unlike some I have had it may be possible to unplug the hdd without breaking seals or needing tools. I do like the alternative USB install you are suggesting. My laptop already has Ubuntu installed but being able to run not just a rescue disk or trial but a full OS from a USB is a great idea.
I have already learnt it can take a couple of hours to reinstall the Windows 7 OS on the laptop, its much faster re-installing Ubuntu.

**(as an aside, relating to persistence**
I also have a legacy desktop, and am trying to get ubuntu working on that, but that is not suitable at present for USB booting
- BIOS does not support USB booting,only hdd or cd
- USB1 is in use the older sower version 
- I do note however that even on this persistence may be possible, in this instance by using a CD boot
-- [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
no need to answer comment  - i will use another thread for questions re CD booting or installing on the desktop )

I have not yet marked this as solved. It is very much still Work In Progress, but I will post back with progress reports in due course.

---

### Post by C.S.Cameron on 2012-01-14
Casper-rw is sort of like a zip file, it can be copied from one Live install to another.
It can be mounted and the data extracted.
It is the only file in a live install that changes.
The O/S is mostly contained in a compressed file named filesystem.squashfs that does not change.

To do a Full install you do not necessarily need to unplug the HDD as long as you make sure grub goes on the USB stick, see Note at end of step by step.

There are boot managers, (such as plop), that will allow you to boot older machines from USB starting with a CD or that can be installed on the HDD allowing USB boot at each startup.

---

### Post by spacecheck on 2012-01-14
One has to keep in mind, that as long as there is enough space, Updates are possible with the Live USB with persistence file, with the exception of kernel, kernel image and kernel headers, which refuse to update and cause error messages. There are also a number of log files created over time, which can eventually consume space, in addition to any/all of the mail files one stores on the drive, including attachments, etc.

There may also be a maximum single file size recognized by the system at boot (32 bit systems?), which may be a problem for using big partitions on larger USB sticks.

Good luck!

---

### Post by aka-John99 on 2012-01-14
Thanks for reply Cameron,

Clarification about casper useful.

I will keep comments about desktop problems in another thread. I did consider plop, but am in process of installing 2nd hdd. I have power bought power cable for it now, now, and will have to find screws for it next. Not sure where they are at present, may resort to borrowing some out of a yet older machine. Priority with the Desktop is getting another hdd installed.

I had hoped to have a go this afternoon, but now have to go to opticians, at least I ought to be able to see better with new spectacles, may even find the lost screws!

---

### Post by aka-John99 on 2012-01-14
Thanks spacecheck,

At present my intentions are on using  the USB stick as a method of booting into Ubuntu more as a last resort, and better than a rescue disk or live cd. I may keep some documents or bookmarks on it, but not intending to keep mail and all  personal files on that USB.

---

### Post by aka-John99 on 2012-01-15
Thanks for the help,I will mark this as solved as I did install Ubuntu on the USB stick, and at least so far it is working ok.

I did not disconnect the hdd of the laptop, but I did ensure I had backups, and made a Windows 7 disk image before embarking on this. My comments on this experience

[LIST]
[*]Installer Changes 
 The installer for Ubuntu 11.10 differs from the 10.4 installers I had last used and gives slightly different options.
[*]Good Experience as a practice run using USB 
  It was good knowing that I was merely installing onto a memory stick, rather than making changes on this laptops only hdd
[LIST]
[*]I will be making changes to the laptops primary install, and no doubt the partitions on which Ubuntu is installed,so it is good to try out the installer.
[/LIST]
 
[*]Installer heading graphic shows HDD structure not USB ! 
 I did find this slightly odd and disconcerting 
I was creating new partitions on the USB yet the installer graphic at the very top of the window was showing details of the laptops hdd.
 At least the installer was also showing in the main body the full disk partitions of each drive.
[LIST]
[*]also good is the fact the installer shows the size details of each drive, that should make it a lot less likely anyone will inadvertently format the hdd instead of the USB
[/LIST]
 
[/LIST]
Presumably the GRUB bootloader on the laptop may be able to cope with an option to boot from the USB in addition to the options it already has, but if I need to ask about that I will start a new thread.

I installed 11.10, the latest version, as that would then match the insructions for the installer, it is 11.04 Lucid tthe LTS that I had used until now,so I now also have to get used to the Unity Desktop &/or follow the instructions in the sticky for changing things.

Thanks again for all the information, I had not previously known much about how casper worked, and did not know about the option to install like this on a USB stick. I had presumed the instructions I had previously followed were as good as it would get for using a USB with persistence, and I was not going to try the advanced or *something else* install options without checking out in more detail what may be required.

---

### Post by kalmdave on 2012-01-22
Thank you all, i f I may add a query this thread, I have an 8Gb pendrive, with Ubuntu 11.10 32bit installed on it, with 1Gb for/of persistence. It's just not saving the changes at all. Am I wrong somewhere, please enlighten.

Regards

---

### Post by aka-John99 on 2012-01-28
I am new to this so I can not help you. I do know I do have (or did have) persistence on the USB boots, but right at this moment I again am running into out of memory messages. Although  at least I understand now a bit more about what I need to check it, it is likely to be the end of the week before I attempt to look into my own problems.

I am using a 16GB stick, and I am expecting even without using all of that for Ubuntu, it should have plenty of room to include for instance a few files and allow updates, but it will not allow updates at present.

Have you tried to check

[LIST]
[*]  whether all of the 1GB has been used up, or for that matter whether any of it has been used.
[*]Did persistence ever work on your USB stick, for instance has your  browser got bookmarks / favourites in it that you have added. (on your USB not the hdd)
[/LIST]
**edit** P.S
- I see posting bumped the thread and kalmdave has an answer now :-)
- the USB stick I am using was ex-fat, but it now includes ext4 and ext2 partitions.

- changing partition size solved the problem
- - may have been better to add a new partition and move /usr from /root to its own partition

---

### Post by C.S.Cameron on 2012-01-28
> **kalmdave said:**
> Thank you all, i f I may add a query this thread, I have an 8Gb pendrive, with Ubuntu 11.10 32bit installed on it, with 1Gb for/of persistence. It's just not saving the changes at all. Am I wrong somewhere, please enlighten.

Regards

Have a look at the root of the pendrive.
Is there a file named casper-rw? This is the persistence file.
In your case the file should be 1GB in size.
If not, let me know, and we set you up with persistence, one way or another.

---

