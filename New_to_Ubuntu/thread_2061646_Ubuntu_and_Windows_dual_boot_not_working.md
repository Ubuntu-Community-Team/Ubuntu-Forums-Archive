---
title: "Ubuntu and Windows dual boot not working"
date: 2012-09-23
forum: New to Ubuntu
---

### Post by Swoorup on 2012-09-23
I downloaded a copy of Ubuntu 64-bit OS iso images and booted up in the thumb drive. I then created a live USB using Unetbootin. I then booted the live USB up in non EFI mode and installed Ubuntu in a separate partition so that I could have 2 Operating System on my computer. 

But I could not get the dual boot option. And then again after following up some forum posts from this website, I tried using boot-repair and it installed GRUB 2.

Here's what the instruction said after the boot-repair completed its task.
> 
Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/1221979/](http://paste.ubuntu.com/1221979/)

In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/grubx64.efi file!

The boot files of [Ubuntu 12.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))
I then rebooted the system and I could get an option booting up Ubuntu and Windows 7 alongside with it, but the problem is that when choosing Ubuntu it does not seem to do anything. The screen just goes blank. 

The grub configuration file is attached within this post if it helps.

Please help. I am new to linux but I am eager to learn it.

---

### Post by oldfred on 2012-09-24
With UEFI, there were some issues on shift key not working. Try holding shift key from "BIOS" until grub menu appears. But with dual boot you should get grub menu automatically.

You may have video issues and need to set a boot parameter on the grub menu linux line. Often nomodeset, but different video cards may need different settings.

What video card/chip do you have?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Swoorup on 2012-09-24
Both the ubuntu boot option does not work with or without nomodeset parameter. I have tried that already. 

The other recovery mode itself has the nomodeset parameters set though.

Please help.

---

### Post by Bashing-om on 2012-09-24
We are trying to help, please help us to help you.
Re-read old fred's post, have you read the suggested links ? Are you able to provide the info on your graphics card?

After selecting ubuntu to boot to in the grub menu all you get is a totally blank screen ? No error messages at all ? Or not any type of command line, not even a blinking cursor ?

Bear in mind we are not setting before your terminal and can not see what you see, you must relay to us what is happening and the results of the instructions provided.

 There are a number of causes to investigate and together we will find resolution. 

[INDENT]kindest regards ==>BDQ
[/INDENT]

---

### Post by Swoorup on 2012-09-26
My graphic card is AMD Radeon HD 7520G.

I have tried that option setting the parameter to nomodeset, but there is the same problem still. 

And yes, after I selected the Ubuntu option in the grub menu, it does not show anything but only blank. I'd have to press the power to restart the computer.

---

### Post by Bashing-om on 2012-09-26
Swoorup;
 OK ...making progress... from the hints I have found, xorg.conf will have to be edited:

"I am using AMD/ATI's proprietary firegl driver, version 12.6, with XOrg  server 1.12.2 and everything seems to be working fine. I even have  OpenGL acceleration, etc. working just fine. I would caution that the  AMD driver stack will not auto detect the GPU so you will have to  manually add the driver section into your xorg.conf to specify where the  card is located on the PCI bus. "

Graphics ChipWorksUsing  AMD fglrx driver 12.6. Driver complains it cannot detect supported  video card. Must specify PCI location in xorg.conf to get working-----------------
will continue to find the required edit and advise.

[INDENT][INDENT]regards <==BDQ

[/INDENT][/INDENT]

---

### Post by Swoorup on 2012-10-17
I didn't find xorg.conf in etc/X11 folders? Can you please intepret me step-by-step. I am new to linux

---

### Post by gerrman97 on 2012-10-17
use a different program to move the iso to usb then try it again. i had the same problem. otherwise download wubi.exe from ubuntu website and it should work.

---

### Post by oldfred on 2012-10-17
Do you get grub menu now? Have you tried recovery mode? Or second line in menu?

But, we may need to start over.

You have to have both systems in the same boot mode. Or if Windows is UEFI, then Ubuntu should be UEFI. Since you also installed Ubuntu in BIOS mode, Boot-Repair can convert it to UEFI mode. Check the options that it gives, one should be to totally uninstall grub2's BIOS verison grub-pc and install the UEFI version or grub-efi. It also makes some other updates to make it work correctly.

You have to in UEFI/BIOS choose to boot from UEFI mode.


You may still have video issue but need to be booting in correct mode first.

It also looks like you installed grub to the partition boot sector of a NTFS partition. That corrupts the NTFS partition. But NTFS does keep a backup of the boot sector and that often can be used to repair the NTFS partition.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:

[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by gerrman97 on 2012-10-17
like i have said before. im new. so how do you post threads? and what is UEFI

---

### Post by Bashing-om on 2012-10-17
@ gerrman97; Hi !

to start a new thread-> at the top of the forum is a link "thread starter" -> click on it and make a descriptive tittle.
UEFI: These explain much better than my words:
[https://gitorious.org/tianocore_uefi_duet_builds/pages](https://gitorious.org/tianocore_uefi_duet_builds/pages)
[http://ubuntuforums.org/showthread.php?t=2059640](http://ubuntuforums.org/showthread.php?t=2059640)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

see ya in the new thread <==BDQ

---

### Post by Swoorup on 2012-10-19
Yes, I get the grub menu, I have tried both options, I have even tried with every possible parameters mentioned everywhere. nomodeset, nosplash, vga=xxx, video=efifb. 
Nothing seems to work. :(

---

### Post by oldfred on 2012-10-19
Aother users in a recent thread thought it was a video issue. He removed quiet & splash and watched to see where it stopped. He found two other issues that were not video related. 

Have you tried recovery mode?

---

### Post by Swoorup on 2012-10-20
yeah, already tried that number of times. :(

---

### Post by oldfred on 2012-10-20
I had video issues with my nVidia card. screen came up with nothing. Right click did give me a little. But I had to install kernel headers and then the nVidia driver. Cntl-Alt f1 or f2 gave me terminal to work with.

Has what worked for me, install headers & dpkg update.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068942](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068942)

Seems to be the same for the proprietary fglrx driver also.
[https://bugs.launchpad.net/fglrx/+bug/1068456](https://bugs.launchpad.net/fglrx/+bug/1068456)

But if Intel  you should not have to install any extra drivers.
If Intel & nVidia, I am not sure if Bumblebee works or not with 12.10.

---

### Post by Swoorup on 2012-11-24
I installed the latest fglrx drivers. Still does not seem to work. Still the same blank screen.

---

### Post by gerrman97 on 2012-11-27
does windows work when you boot into it? if not maybe the video card is the problem.

---

### Post by Swoorup on 2013-05-05
Finally I found the solution to this. 

ASUS-K55N is just not able to boot an EFI linux. You have to convert to MBR mode to enable both windows and linux. Here is what I did:

i) Create a live CD of Windows Recovery Disk and another live CD for linux
ii) Boot the linux live
iii) Use gdisk and first of all backup the partition table using 'b' switch in default mode.
iv) Next, in recovery mode inside gdisk, choose convert GPT to MBR, deleting all the GPT data and save it with 'w' command. (Don't ever open gdisk after this)
This allows you to have to save partition layout except that it is just using MBR partition table.
v) Next, reboot and now boot from Windows Recovery Disk,
vi) In Command Prompt type the following
[COLOR=#DD1144][FONT=Monaco]bootrec /scanos[/FONT][/COLOR]
[COLOR=#DD1144][FONT=Monaco]bootrec /rebuildbcd[/FONT][/COLOR]
[COLOR=#DD1144][FONT=Monaco]bootrec /fixmbr[/FONT][/COLOR]
[COLOR=#DD1144][FONT=Monaco]bootrec /fixboot

Now, you should be able to boot into windows from your hard disk, where's nothing is changed but it is only booting from MBR.

Then, the rest is history[/FONT][/COLOR]

---

### Post by oldfred on 2013-05-06
Good to know you can convert successfully to BIOS mode. 

Another thread with users who could not make UEFI dual boot work on k55n.
[http://ubuntuforums.org/showthread.php?t=2111720](http://ubuntuforums.org/showthread.php?t=2111720)

---

