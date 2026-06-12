---
title: "Newbie concerns about Ubuntu"
date: 2012-10-30
forum: New to Ubuntu
---

### Post by leftbrainedmustdie on 2012-10-30
Hi my laptop died mysteriously so I got a new one w/o an operating system(cheaper).
I decided to install Ubuntu 12.04.1LTS ( cheaper) as my vista DVD failed to boot.
I simply burned this .iso file to a DVD and inserted in the new laptop and followed prompts.  After many tries have managed to connect to the internet.

I would like to add partitions--my laptop has none-- and tried to use partman. I downloaded** • partman-auto-73ubuntu7-i386.udeb ~73Kb**
and using USB drive transferred it to the new laptop and tried to run the file as normal. I am unable to run any executable files on this laptop, including partman.
:guitar:
When I try to run any  ".exe" file I get an error message for example the CD that came with the laptop where I try to execute autorun.exe.  Partman gives similar error message.

I insert the CD and there is only 1 .exe file in the outer folder
autorun.exe
I get the following error message
Archive: /media/1.00.02/autorun.exe
Zip file size: 2844568 bytes, number of entries: 29824
[/media/1.00.02/autorun.exe]:
Zipfile is disk 34294 of a multi-disk archive, and this is not .
the disk on which the central zipfile directory begins (disk
3569)
...................................................................................................................................
VBSETUP. LIB.......>right-clicked--chose Open with software Manager...>error message:
Install software to open files?
Nautilus requires to install software to open files of the following
type:AR
archive is not supported
supported file types 
.......................................................
Can anyone suggest something? I also have a concern that when I delete files the space that was taken up by them is not available for rewriting. I mean overwriting. For example I inserted an almost full external USB drive of  66Mb  and downloaded its contents to desktop and deleted the USB's contents and also emptied recycle bin. The USB drive is still showing as full and I cant add any data to it even though it is empty.  I also want to know if this 66Mb USB drive which is either FAT-formatted or NTFS-formatted is having a problem because these formats wont work in an Ubuntu system



Thanks for the help. I have learnt how to do it thanks to you all. I have reinstalled Ubuntu with partitions. I wonder if its possible to give individual thanks or points

---

### Post by mahdiolfat on 2012-10-30
Hi,

I don't have all the answers for you.

Firstly, .exe files are Windows only and don't work in Ubuntu.
What are you trying to install from the CD?

You need to format your USB in order to really clean it up and use it again.
Follow the instructions in this link:
[http://askubuntu.com/questions/68809/how-to-format-a-usb-or-external-drive](http://askubuntu.com/questions/68809/how-to-format-a-usb-or-external-drive)

Ubuntu 12.04.1 supports both FAT and NTFS filesystems.

-
Mahdi

---

### Post by snowpine on 2012-10-30
Welcome to the forums!

The Ubuntu DVD includes a tool called GParted Partition Manager. I recommend that you boot your Ubuntu DVD and use this provided and supported tool to set up your partitions. Here are a couple of links I think will be helpful:

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
[https://help.ubuntu.com/community/GParted](https://help.ubuntu.com/community/GParted)

To answer your question about the USB drive filling up, this is a limitation of the persistent live system, once you have installed Ubuntu to your hard drive it will not behave like this.

---

### Post by kanikilu on 2012-10-30
You can't run Windows executables (.exe) on Linux, out of the box. Some may work with Windows emulation like Wine, but many don't...

Anyways, where are you at this point? Do you have Ubuntu installed, or just running off the Live DVD? If you are using the Live DVD and want to partition the hard drive, look for a program called "GParted Partition Editor" in the dash. Alternatively, you could partition the drive manually during the Ubuntu install.

// Edit - too slow ;)

---

### Post by deadflowr on 2012-10-30
You can install the program gparted either through a terminal, press ctrl+alt+T:

```
sudo apt-get install gparted
```

or, open the Ubuntu Software Center and search for gparted and install from there.
Be aware that whichever way you install it, you'll be prompted for your password.(Note: passwords typed in the terminal are invisible).

.exe files cannot run in Ubuntu. They are Windows files.

As a side note, your system most likely has two partitions(if set up as a normal install goes), a root partition, and a swap partition.

Here's help with gparted:

[https://help.ubuntu.com/community/GParted]("https://help.ubuntu.com/community/GParted")

---

### Post by LemonLime on 2012-10-30
I'm still learning the quirks of Ubuntu myself, but I might have some suggestions...

When you install Ubuntu fresh from a CD, and you're overwriting any present OS, your drive will likely be formatted and repartitioned. There is partition software included on the disc and it will automatically setup what's needed for Ubuntu to run, but also give you some options to change partition size, add another partition, etc. In the past I've been able to use this program just fine to setup Ubuntu, even incorporating a Windows installation. You should have at least two partitions, one being the main partition formatted for Linux and a second partition being used as a SWAP file.

I might be totally misunderstanding what you're asking/saying, but when you say ".exe" you're referring to an executable file, and that file extension is a Windows unique thing. As far as I know, ".exe" does not exist in Linux unless it's being handled by a windows virtualization. Autorun.exe would be where Windows would look to start up an application running from the disc you've made, and wouldn't run inside Ubuntu. 

Basically, you can make partitions using your already-working Ubuntu disc or you should be able to (easily) find an application that can handle this process using the software center. I hope some of the above made sense.

---

### Post by MoebusNet on 2012-10-30
Allow me to suggest that if this is your first attempt to install Ubuntu, you may wish to perform the installation to your hard drive using all, or as many as possible, of the default settings that Ubuntu offers. This should give you a working Ubuntu setup on your laptop while you learn more about Ubuntu.

If you save your documents to an external drive or back them up to an external drive, it should be fairly easy to reinstall Ubuntu later using a multi-partition setup on your hard drive after you have learned more about Ubuntu and the tools it offers, and recover your saved documents. I think that is what most of us here have done when we were learning, anyway.

---

### Post by leftbrainedmustdie on 2012-10-30
:guitar:I am trying to install drivers from the CD. Its a CD that came with the new laptop, The link you have given goes to askubuntu.com which says they can't find the page I requested, Thanks very much 4 advice

---

### Post by snowpine on 2012-10-30
Normally it is not necessary to install drivers that method in Linux. What is the specific hardware for which you are trying to install the driver?

---

### Post by Mark Phelps on 2012-10-30
> **leftbrainedmustdie said:**
> :guitar:I am trying to install drivers from the CD. Its a CD that came with the new laptop ...

You said the laptop came without an operating system installed, so I don't understand why it came with a CD as well...

But most likely, the CD contains Windows drivers -- which you won't be able to use in Ubuntu.

---

### Post by leftbrainedmustdie on 2012-10-30
I am simply trying to install drivers that came with the new laptop, thinking they were absolutely necessary.  I have succeeded in installing GParted via the Ubuntu Software Center, but it does not have options to resize partitions.

---

### Post by leftbrainedmustdie on 2012-10-30
please can you explain what this code is: 
sudo apt-get install gparted
I know in windows you have to navigate to the .exe file then type the command
at command prompt. How do you do it here? Why is there no option on my GParted to resize partitions,
I did not do any partitioning on my 500GB laptop when installing Ubuntu but
it has partitioned itself putting Ubuntu in a 460GB primary partition  sda1 and has
created one extended partition sda2 with one logical partition sda5. Both are 8Mb each.
I am not able to resize using gparted. Can someone tell me whats wrong thanks very much

---

### Post by leftbrainedmustdie on 2012-10-30
I have got a 500GB laptop with no operating system and installed Ubuntu 12.04.1 on it by burning to a DVD from another computer.  I did not know how to partition it. I have now installed GParted through the software center.  Gparted shows me that ubuntu has done some poor partitioning by itself, putting the Ubuntu into 460GB and making 2 other partitions of 7Mb each  but it does not allow me options to resize and delete partitions. Thats how far I've got,thanks,

---

### Post by pqwoerituytrueiwoq on 2012-10-30
if you installed ubuntu using the default settings on a blank hdd there is no need for gparted, you partitions are just fine as is

you cant resize a mounted partition, you have to unmount it 1st and you cant unmount the file system you booted, you need to resize from a live cd/dvd/usb

---

### Post by snowpine on 2012-10-30
Gparted must be run from Live DVD if you wish to resize the partitions on your hard drive. (You cannot resize a partition while it is in use.)

However I recommend you study your partitioning scheme in detail before you rush into any changes. The following terminal commands will help you to analyze your disk usage (please copy & paste the terminal output back here).

```
df -h
sudo fdisk -l
```

---

### Post by monkeybrain2012 on 2012-10-30
> **leftbrainedmustdie said:**
> please can you explain what this code is: 
sudo apt-get install gparted
I know in windows you have to navigate to the .exe file then type the command
at command prompt. How do you do it here? Why is there no option on my GParted to resize partitions,
I did not do any partitioning on my 500GB laptop when installing Ubuntu but
it has partitioned itself putting Ubuntu in a 460GB primary partition  sda1 and has
created one extended partition sda2 with one logical partition sda5. Both are 8Mb each.
I am not able to resize using gparted. Can someone tell me whats wrong thanks very much


In Ubuntu (and most other Linux distros) you install from the package repositories (kind of like app stores for Apple except everything is free and open,--well Ubuntu does have paid apps but that is a minor point) "sudo apt-get install XXX" is a way to download and install a program from the repositories using the command line.

For easy browsing by categories and one click installation you may want to use a GUI. Ubuntu comes with the Software Center, so you can just go there and look up gparted and install it with a click. I personally prefer synaptic package manager which is a lot faster and allows more options but that is not installed by default so you can install it from the software center or in the terminal type "sudo apt-get install synaptic"

There are other ways to install software like downloading a .deb and right click it (kind of like downloading .exe for Windows), adding ppas and compiling from source, but at the moment you should just stick to the repositories, it is the easiest and safest way to install things.

To use gparted you need to unmount all the partitions first. You should provide a screenshot (use the press key) of your partition layout (just open gparted and take the screen shot) so that we don't screw you up because of misunderstanding.
So you cannot run gparted when you are in the very partition/drive that you want to modify, you should run it from a live usb.

---

### Post by Bashing-om on 2012-10-30
leftbrainedmustdie; Hi ! Welcome to the forum (belatedly ).

Look, this is ubuntu, a variant of linux ...not I repeat not windows/ most evrything will work out-of-the-box...until you get to a point that you know for sure you need to change/install a driver ...don't ! Ubuntu's kernel takes care of it !

As you bought the computer with out an operating system (great !), there is nothing installed... For now I suggest you take an easy path for beginners to get ubuntu up and running. My suggested method:
1. in bios set the 1st boot priority as the cd drive.
2. insert install disk
3. let the system boot up to the menu.
4. choose "Tru ubuntu without installing". Will run slow as compared to running on the hard drive->
5. Play with the system, to insure all does indeed function properly with all your devices.
6. Satisfied ? ...from the desk top choose "install"
7. answer the minimal questions, in the installation screen check install updates during installation, and 3rd party software is enabled. Do the installation the easiest way -let the wizard do the install- eg-> use the entire disk option for installing, insure grub (grand unified bootloader) is going to be installed to the device named sda (as I expect that you desire to boot from the 1st hard disk) --> and you are done !

Do remember the password that you set, this password will be VITAL in administering your system

Detailed installation instructions here:
[http://www.ubuntu.com/download/help/install-ubuntu-desktop](http://www.ubuntu.com/download/help/install-ubuntu-desktop)

stick the disk in, see what happens -> ask questions.
[INDENT]just try'n to help <== BDQ

[/INDENT]

---

