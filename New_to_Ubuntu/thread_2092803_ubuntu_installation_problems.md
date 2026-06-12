---
title: "ubuntu installation problems"
date: 2012-12-08
forum: New to Ubuntu
---

### Post by gleplae on 2012-12-08
I am having problems booting up ubuntu 12.04 from a dvd I burned. I am trying to install ubuntu 12.04 onto an older custom built desk top computer which has windows 7 installed, 1.1 GB AMD processor and 1.5 GB of RAM. When I start up the computer it allows me to choose between windows 7 and ubuntu boot up and when I choose the ubuntu option the screen says completing installation and a countdown appears after which the screen goes blank.

I have used the dvd to successfully install ubuntu on my laptop so it must be an issue with the desktop, is it possible that it is too old ?

---

### Post by Bashing-om on 2012-12-08
gleplae; Hi ! Welcome to the forum.

My first guess is: primary partitions on the hard drive. One may only have 4 primary partitions per disk, and often windows takes up all four of the partitions. If this is the case there are means to make a partition available for ubuntu to be installed on.
To see the partitioning:
Boot up the livecd in "try ubuntu" mode; ctl+alt+t key combo -> command line interface.
Enter these terminal commands:
```
sudo fdisk -lu
sudo parted -l
```Be aware that the use of sudo elevates one to administrative authority.
[INDENT]just try'n to help <== BDQ

[/INDENT]

---

### Post by johnycsf on 2012-12-08
Did you manually try to create the partition or did you just select the options to install ubuntu to run side by side with windows?

---

### Post by gleplae on 2012-12-09
I just selected ubuntu to run side by side with windows I have not done anything to the partition I will try to manually change the partition.

---

### Post by johnycsf on 2012-12-09
> **gleplae said:**
> I just selected ubuntu to run side by side with windows I have not done anything to the partition I will try to manually change the partition.

Try the installation once again. Before you begin installation make sure you are connected to the internet and select the checkbox for download upgrades or updates.

Select to run side by side with windows and when the installation is done it should prompt you to remove the disc or usb and restart!

---

### Post by gleplae on 2012-12-09
Hi Johny,

I am not getting any check box options I am starting up the computer with the dvd in the dvd player and computer starts to bootup then it gives me either the option to bootup with windows7 or ubuntu. when I try the ubuntu option the computer just goes blank after about 5 seconds. 
At this point I am just trying to install ubuntu off the dvd so I am not sure that partitioning the hard drive is the issue. The computer is connected to the internet but there are no options that allow me to download upgrades or updates or to run side by side with windows.

---

### Post by Bashing-om on 2012-12-09
gleplae;

Please do the commands in post #2, so we know what we have to work with/from.
Post the output to this thread within code (#) tags from the top of the post.

[INDENT]still try'n to help <== BDQ

[/INDENT]

---

### Post by critin on 2012-12-09
> **gleplae said:**
> I am having problems booting up ubuntu 12.04 from a dvd I burned.** [COLOR=Red]I am trying to install ubuntu 12.04[/COLOR]**onto an older custom built desk top computer which has windows 7 installed, 1.1 GB AMD processor and 1.5 GB of RAM. [COLOR=Red]**When I start up the computer it allows me to choose between windows 7 and ubuntu**[/COLOR] boot up and when I choose the ubuntu option[COLOR=Red]** the screen says completing installation**[/COLOR] and a countdown appears after which the screen goes blank.

I have used the dvd to successfully install ubuntu on my laptop so it must be an issue with the desktop, is it possible that it is too old ?

The first two statements seem to be contradicting.  If you get a grub screen to choose between the two systems, ubuntu apparently is already installed.  I've never had a ubuntu install say it's 'completing installation ' like this.  My installations always complete before asking to restart.

Are you in fact still trying to install it?  Have you tried to boot without the dvd?  Is some info missing from your description of the problem?
> 
 when I try the ubuntu option the computer just goes blank after about 5 seconds. 

Graphic card problem?

---

### Post by gleplae on 2012-12-18
I tried to enter the commands that were recomended by  Bashing-om but the commands are not recognized. 
I partition the C drive with windows and have 36 gb of available space to install ubuntu. But after partitioning the drive I still can't bootup ubuntu. I successfully reached GNU GRUB menu giving me different options to bootup with. normal mode, safe graphic mode, Acpi workarounds, verbose mode and demo mode none of the options were very sucessful except that I could reach a command prompt when I was in verbose mode. I did not have any options such as "try ubuntu" mode.


**Re: ubuntu installation problems**
 		gleplae; Hi ! Welcome to the forum.

My first guess is: primary partitions on the hard drive. One may only  have 4 primary partitions per disk, and often windows takes up all four  of the partitions. If this is the case there are means to make a  partition available for ubuntu to be installed on.
To see the partitioning:
Boot up the livecd in "try ubuntu" mode; ctl+alt+t key combo -> command line interface.
Enter these terminal commands:
 	Code:
 	sudo fdisk -lu sudo parted -l 
Be aware that the use of sudo elevates one to administrative authority.just try'n to help <== BDQ

---

### Post by JHawk56 on 2012-12-18
> **critin said:**
> I've never had a ubuntu install say it's 'completing installation ' like this.I have -- on a wubi install. Could this be one?

---

### Post by Bashing-om on 2012-12-19
gleplae;

Let's back up a bit and try some things in simpler terms.
1. Set bios to boot the dvd drive as 1st boot priority.
2. Boot up the install disk, will take a while to de-compress, boot to the greeter screen and choose the "try ubuntu" option.
3. Boot continues to the GUI desktop.
4. On this desktop the launcher on the left side of the screen, top icon is the "dash", click on the dash -> search box opens -> enter the term "terminal" -> command line interface opens up.
5. In this CLI enter the terms  -one line at a time:
```
sudo fdisk -lu
``` press the enter key
```
sudo parted -l

``` press the enter key.
Now post the out puts back here. (copy and paste -> between code tags)
These commands will tell us how your disks are set up and what you have installed.

[INDENT][INDENT]still try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by gleplae on 2012-12-19
what is a wubi install?

---

### Post by gleplae on 2012-12-19
I have dvd set as primary booting device.  When I boot up with the dvd in dvd drive computer goes through bios startup then after about 1/2 minute gives me the choice to bootup either windows 7 or xubuntu when I select xubuntu the screen says completing installation and starts counting down from 5 to zero. If I wait a few seconds it then goes to a bluegreen screen and doesn't do anything. If I hit escape before the count down goes to zero it takes me to  GNU GRUB menu giving me different options to bootup with. normal mode,  safe graphic mode, Acpi workarounds, verbose mode and demo mode none of  the options were very sucessful except that I could reach a command  prompt when I was in Acpi mode.  Once in ACPI mode the screen scrolls through a bunch garble and finally ends up at BusyBox  built in shell and has (initramfs) at the command line prompt if I enter "terminal" or "sudo fdisk -lu" it says not found? I never reach a point where I can choose try ubuntu as a boot option. Not sure what I am doing wrong.

---

### Post by williejones on 2012-12-19
> **gleplae said:**
> I have dvd set as primary booting device.  When I boot up with the dvd in dvd drive computer goes through bios startup then after about 1/2 minute gives me the choice to bootup either windows 7 or xubuntu when I select xubuntu the screen says completing installation and starts counting down from 5 to zero. If I wait a few seconds it then goes to a bluegreen screen and doesn't do anything. If I hit escape before the count down goes to zero it takes me to  GNU GRUB menu giving me different options to bootup with. normal mode,  safe graphic mode, Acpi workarounds, verbose mode and demo mode none of  the options were very sucessful except that I could reach a command  prompt when I was in Acpi mode.  Once in ACPI mode the screen scrolls through a bunch garble and finally ends up at BusyBox  built in shell and has (initramfs) at the command line prompt if I enter "terminal" or "sudo fdisk -lu" it says not found? I never reach a point where I can choose try ubuntu as a boot option. Not sure what I am doing wrong. 

Is your DVD spinning when trying to boot?  You should not get a grub screen to select Windows 7 or xubuntu from the live DVD

---

### Post by Bashing-om on 2012-12-19
gleplae;

A "wubi" install is a form of virtual machine in which 'buntu runs inside of windows; many like this type of install, has some disadvantages.

On the present situation. To boot the DVD in "try ububtu" mode; one must set in bios the dvd drive as 1st boot priority. Insert the install disk and wait for it to boot and decompress. Should get to the greeter screen with two options:
a) try ubuntu
b) install ubuntu.

choose "try ubuntu"

[INDENT][INDENT]please advise status <== BDQ

[/INDENT][/INDENT]

---

### Post by gleplae on 2012-12-20
Yes the dvd seems to be spinning when I insert it.  I have never gotten either option install or try ubuntu after insert installation dvd? Is there a way to restart the whole process and uninstall what I have previously done.

---

### Post by Bashing-om on 2012-12-20
I can not imagine where the fault may lie.
Can you take that install disk to another computer and see if that one will boot up the install DVD ? In a process of elimination making sure the install medium is good.

The installation should have no bearing on the ability to boot the DVD - the booting up of the DVD all happens in bios.

As a side note- at a later time if you go with a true dual boot, will want to delete the "wubi" file from within windows.

[INDENT][INDENT]We want to get you up on 'buntu <== BDQ

[/INDENT][/INDENT]

---

### Post by JHawk56 on 2012-12-20
> **gleplae said:**
> what is a wubi install?

Bashing-om explained it well.

My hunch could be way off, but the reason I brought up wubi is I read in your posts some characteristics of a failed wubi install. A wubi install initially takes place in Windows. Upon first reboot, you get:

--Your usual BIOS screen
--A choice of Windows or Ubuntu (This is not grub; it's the MS boot manager. Windows is listed first, and if you make no choice, eventually you'll enter Windows. This is indicative of a wubi install.) But if you choose Ubuntu, the next screen reads:
--"Completing Ubuntu installation.
   For more installation boot options' press 'ESC' now..."
   (5-second countdown)

If you did do a wubi install, you must have either:
-- Used the Windows Installer at ubuntu.com OR
-- Obtained a ubuntu iso (not a disk image but the original file) and run a file called wubi.exe within the same Windows folder OR
-- Run a wubi.exe file by itself, in which case it would have downloaded an iso for you and proceeded with installation.

Whichever method was used, you'd have seen screens in Windows like those marked "3" and higher at this link: [http://www.ubuntu.com/download/help/install-ubuntu-with-windows](http://www.ubuntu.com/download/help/install-ubuntu-with-windows)

I'm wondering if possibly you burned the iso to disk as a file, not as an iso image, and somehow ran wubi.exe with it. Or ran wubi.exe against the file you made your disk image from.

If you did attempt a wubi installation, you should have a log file in Windows, something similar to:
C:\Documents and Settings\yourwindowsusername\Local Settings\Temp\wubi-12.04-rev269.log . (This path is for Windows XP; I don't know where Windows 7 would put it, so you could just search your Windows drive for wubi*. Actually, I'd recommend searching all your partitions used by Windows, in case you come up with a wubi.exe file.

If you do find evidence of wubi, I recommend you de-install Ubuntu via the Win7 equivalent of WinXP's 'Add or Remove Programs' or run wubi.exe again and it will uninstall the old Ubuntu, then give you a chance to cancel before doing anything else. Then burn a new DVD image and start over. There's not much reason for wubi unless you can't write to and boot from either DVD or flash drive (that's my reason), or you REALLY REALLY REALLY want to avoid repartitioning.

---

### Post by Bashing-om on 2012-12-20
@JHawk56; Outstanding !

@gleplae; What is the current situation ?

[INDENT][INDENT]still learning after all these years ==> BDQ

[/INDENT][/INDENT]

---

### Post by gleplae on 2012-12-21
I will have to check my computer and search for a wubi file this does sound like what is going on but I am pretty sure the dvd is functional since when I insert it into my dell laptop ubuntu boots up just fine.

---

### Post by gleplae on 2012-12-21
I am still not 100% sure what a wubi install is. Is it the same as trying ubuntu without fully installing it onto the hard drive, how do I avoid doing it again?

---

### Post by critin on 2012-12-21
> **gleplae said:**
> I am still not 100% sure what a wubi install is. Is it the same as trying ubuntu without fully installing it onto the hard drive, how do I avoid doing it again?

When you chose your version to download, did you choose Windows Installer version?
Such as on this link?

[http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

---

### Post by JHawk56 on 2012-12-22
> **gleplae said:**
> I am still not 100% sure what a wubi install is. Is it the same as trying Ubuntu without fully installing it onto the hard drive, how do I avoid doing it again?My long post above lists the only ways I know to get a wubi installation. It is not the same as running Ubuntu from Live CD without installing. It installs Ubuntu on one of your Windows partitions (that would be another clue--a Ubuntu folder on one of your Windows partitions).

---

### Post by deadflowr on 2012-12-22
If wubi is installed the easiest fastest way to find out is to check the add/remove/whatever they call it now program thingy in windows, and look for anything that says Ubuntu or wubi.
Wubi is a program for windows and will be installed like any other windows program.
From the sound of it the DVD is either burned badly or unreadable.
booting pass the DVD and straight to the boot menu is in my experience the result of a bad burn/bad disk.

---

### Post by gleplae on 2012-12-22
I don't see anything with the name wubi installed on my computer but do have xubuntu installed which I will uninstall and then retry the dvd. I suspect I:popcorn: may have accidentally installed that because I tried installing ubuntu using a usb stick before using the dvd .

---

### Post by gleplae on 2012-12-23
I uninstalled xubuntu and tried ubuntu dvd installation. The computer says booting from cd and after a few minutes boots up with windows 7?

---

### Post by JHawk56 on 2012-12-23
> **gleplae said:**
> I uninstalled xubuntu and tried ubuntu dvd installation. The computer says booting from cd and after a few minutes boots up with windows 7?Was the DVD burned with your laptop? If so, I'm wondering if:
-- your old desktop PC's DVD reader doesn't like the brand of media you are using, or
-- it has a CD reader, not DVD (pretty common for a PC old enough to have a 1.1 gHz CPU).

---

### Post by gleplae on 2012-12-23
Yes I burned the dvd with my laptop, do you think if I burn one using the desktop it will have a better chance of working?

---

### Post by gleplae on 2012-12-23
Actually I am pretty sure the cd drive on my desktop probably won't burn dvds but can read most types. What is the possibility of using a usb drive to install ubuntu, the last time I tried that it didn't work either. I must have done something wrong since I got the wubi installation using the usb drive.

---

### Post by JHawk56 on 2012-12-23
> **gleplae said:**
> Yes I burned the dvd with my laptop, do you think if I burn one using the desktop it will have a better chance of working?Yes.> **gleplae said:**
> Actually I am pretty sure the cd drive on my desktop probably won't burn dvds but can read most types. What is the possibility of using a usb drive to install ubuntu, the last time I tried that it didn't work either. I must have done something wrong since I got the wubi installation using the usb drive.If it can read DVDs, it probably has a DVD logo on it.

You can install via a USB flash drive IF your BIOS allows booting from one and is set to boot from there first, or you call up a boot menu when the first BIOS screen appears and select it there. Instructions for creating a bootable Ubuntu flash stick are here: [http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

---

