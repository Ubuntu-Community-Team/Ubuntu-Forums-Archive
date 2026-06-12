---
title: "Nothing works.  Please help or I'm buying windows"
date: 2015-01-24
forum: New to Ubuntu
---

### Post by tom_weaver on 2015-01-24
This is the third time in 3 years I've tried Ubuntu.  For the third time I can't get anything to work.  It's extremely frustrating. All I get are roadblocks anytime a solution to anything is proposed. 

Ubuntu runs on a live usb.  When I try to install it the install crashes everytime. 

My hard disk mounts but says I have no permission to read/write to it.  I can't figure out how to change permissions. There was an error when I tried to create an administrator. 

The ubuntu software center opens, then closes very quickly instantly.  

Even though I am using a 32 gb flash disk, the computer seems to think I only have 100 mb of storage space, so I can't download another type of linux. 

I have a mac as my other computer and it won't burn CDs and won't make USB disks, so I was counting on Ubuntu to let me make a new flash booter. I can't because I can't save anything to my hard disk because of permissions. 

In short, this has been tremendously frustrating.  Nothing works and nothing makes any sense.  Unless somebody has any bright ideas, I guess I'll go buy windows because this SUCKS.

---

### Post by oldos2er on 2015-01-24
If you need to use Windows, please do.

Please give us some background information such as your hardware specs, and Ubuntu version.

---

### Post by yancek on 2015-01-24
So you are now just running Ubuntu from a flash drive, not installed.  Is that correct?  You might try reading a tutorial on how to install such as at the link below.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

What hard disk mounts?  What's on it?  If you are using a Live CD on a flash drive, you can gain administrator privileges with the sudo command.  Any changes you make aren't going to be saved on reboot if you are using a Live CD on the flash drive.  You need to explain if you have an actual install or just a Live CD on a flash drive.  How did you get Ubuntu on the flash drive, what software did you use?

It would probably have been easier if you had done some research before you started which you don't seem to have done.  There are numerous tutorials on installing and using Ubuntu.  If you want windows, go ahead. I don't know why you think volunteers here at this forum would care.

---

### Post by tom_weaver on 2015-01-24
First, I'm sorry for getting frustrated.  

My 320 GB disk mounts that had the windows install on it.  I just put a new mobo memory and cpu in. It boots into a USB live of ubuntu and has wireless access.   However, the 320 GB HD, although it mounts, does not let me write to it.  It says I do not have the right permissions.   I was attempting to re-download the USB ubuntu installer because I thought maybe the installer had 2 errors when I ran the check. 

I used Pen Drive's linux installer and it's the 64 bit 4.04.1 LTS

It's a ASRock IIH97-13b Mobo and an intel I3 3.5gz 8 gb ram.

---

### Post by buzzingrobot on 2015-01-24
> **tom_weaver said:**
> 
There was an error when I tried to create an administrator. 

For terminal use, preface a command with 'sudo'.  GUI apps -- relatively few -- that require this kind of privilege escalation will prompt you for it. In both cases, enter the password you created for yourself during the installation.

Bear in mind that, in Unix/Linux, the 'root' user is more or less comparable with the adminstrator in Windows.  In Ubuntu, however, no root user is created, by default.  This is a security measure. Users can temporarily acquire all the privileges they need by using sudo.

> ... I am using a 32 gb flash disk...

Is that the drive you've installed Ubuntu onto?  How is it attached?

---

### Post by buzzingrobot on 2015-01-24
> **tom_weaver said:**
> 

  It boots into a USB live of ubuntu and has wireless access.   However, the 320 GB HD, although it mounts, does not let me write to it..

When you boot the USB stick with the installer, do you see the expected "Try Ubuntu" and "Install Ubuntu" options?  

Are you trying to write to the 320gb drive while in "Try It" mode?  Or, are you launching the installer and it is telling you it cannot write to that drive? Or, are you successfully installing, rebooting into Ubuntu, and then getting the write errors?

---

### Post by tom_weaver on 2015-01-24
So when I run CFdisk it says "fatal error: cannot open disk drive press any key to exit cfdisk"   DF is showing 100% of space used.  parted says I am not a superuser and Error: no device found.  

So then I checked devices and it has my 320 GB hard drive, my cd rom drive, my 31 gb thumb drive and then Other devices it has a 984 mb loop device and a 2.2 gb loop device, both called casper-rw.  The system will not let me mount anything because it says  Error creating mount point /media/buntu/casper-rw no space left on device.  

I think this is probably an issue with hard drive space and/or my hard drive not mounting correctly? What do I need to understand about partitions, mounting, etc. before I can install ubuntu?  Is there something I should read about this?  Do I need to understand loop devices first before installation is possible?

Is my USB stick set up wrong somehow?  Does it not have enough space maybe?

The installer keeps crashing and I have not been able to go past the screen where it shows the map of the world in the background.    I was trying to write to the 320 device in "try it mode"   I figured the installer might have been having problems because of  hard drive mounting issues.

I have not been able to install and am running live. The installer keeps crashing at the same point with the map of the world behind it.    I don't know why.  Should I check logs or something to find out? Is my USB stick a bad copy maybe/

I should add the reason why I was trying to mount my HDD in live is because I wanted to download a new copy of ubuntu (or mint) thinking that maybe my USB stick was bad.  Then I was going to create a New USB stick from within ubuntu.  I have a mac and mac's don't let you create bootable USB sticks.  Also my CD burner does not appear to be working.    My new computer is a DIY and the only operating system I have for it is ubuntu live USB disk.  I'm kinda stuck because I can't make another with the equipment I have. But because I can't mount a drive, I don't have a way to download a new copy of ubuntu in order to make a new USB stick... It's kinda an ugly circle I've gotten myself into here.

Maybe what I should be worried about is getting the installer to work somehow?  Is there a way with more power options with the USB stick I have?   The GUI isntaller does not appear to be working ...

---

### Post by buzzingrobot on 2015-01-24
It's possible the image was burned to the stick incorrectly. If so, the only recourse is to try again with new newly downloaded image.

Just to be sure, you are using a 14.10 install image?  I ask because the 15.04 development image exhibited a bug recently that sometimes similarly crashed its installer.

You don't really need to know anything about mounting, etc., to get Ubuntu installed. You do need to ensure there's space on the target drive for Ubuntu's partitions.

---

### Post by tom_weaver on 2015-01-24
Yeah it's a 14.10 image...   The problem is I took apart my windows machine to use its case and power supply and don't have a way to burn another disk since ubuntu live is not cooperating on that front.   If I could just get it to mount my 320 GB drive I could download ubuntu and make a new flash disk....

---

### Post by tom_weaver on 2015-01-24
To clarify I don't have a windows license for this new mobo

---

### Post by buzzingrobot on 2015-01-24
If you have another USB stick, and another available USB port, try downloading another image while in live mode.  The filesystem the live mode uses is maintained in RAM.  Open a terminal and move to the folder where you saved the image (probably Downloads). 

Attach the second USB stick.  In the terminal, execute "lsblk" and/or "mount" to see if you can determine which device has been assigned to that USB stick.

 (I have two internal drives in my system, and an attached USB external drive.  They are /dev/sda, /dev/sdb, and /dev/sdc, respectively.  An attached stick is /dev/sdd. If you have a single internal drive, it should be /dev/sda.  If no other USB device is attached, the USB stick with the install image should be /dev/sdb and the second stick should be /dev/sdc.  But, be sure to check!)

So, assuming your second stick is /dev/sdc, you can burn the image to it by executing this command in the terminal: ```
sudo dd if=the-name-of-the-image.iso of=/dev/sdc bs=4M && sync
``` E.g.,  "sudo dd if=ubuntu14.10-amd64.iso of=/dev/sdc bs=4M && sync". You should not be prompted for a password.

This usually takes from a few minutes to several minutes to complete. Be very careful here because the dd command simply transfers bytes from "here" to "there", period.  If you accidentally pointed it the 320gb drive, it will happily write the image there.

When it completes, don't unattach the stick.  Power down the machine. Remove the other USB stick so the new stick, with the new image, is the only one attached.  Then, power up and, fingers crossed, you should boot into the new image and try a new install.

---

### Post by tom_weaver on 2015-01-24
Thanks I appreciate it but I can't download anotehr copy of the image because I don't have enough hard drive space.  I only have 900 mb of space and that's it.  Even though my pen drive is 31 gb it won't mount and I can't access it.

---

### Post by Cope57 on 2015-01-24
There are over two hundred versions of Linux out there, and if Ubuntu is giving you issues, feel free to check out more distributions at distrowatch.com.  If you are still having to much problems with Linux adapting to the hard drive, feel free to reinstall Windows.

Call up Microsoft, and tell them you upgraded your motherboard, and now Windows does not work.
They will most likely give you a new product key for the changes in your PC.
I upgraded my wife's motherboard, video card, cpu, and ram, and she was able to get a new product key.  I still can not get her to switch over to Linux, but I have opened her eyes to open source software.

---

### Post by buzzingrobot on 2015-01-24
> **tom_weaver said:**
> Thanks I appreciate it but I can't download anotehr copy of the image because I don't have enough hard drive space.  I only have 900 mb of space and that's it.  Even though my pen drive is 31 gb it won't mount and I can't access it.

You won't be downloading to either physical drive.  You'll be downloading to the filesystem created, in RAM, when you run in live mode. 

I've used this approach when I've managed to work myself into similar spots.

---

### Post by mc4man on 2015-01-24
> **tom_weaver said:**
> Thanks I appreciate it but I can't download anotehr copy of the image because I don't have enough hard drive space.  I only have 900 mb of space and that's it.  Even though my pen drive is 31 gb it won't mount and I can't access it.

If you do have 8GB ram then there is more than enough free ram to download a new image - ck  in live session with
```
free -m
```
I would not bother with 14.10, it's a buggy & shortlived 'release'
Use the amd64 image from here, just go there in Firefox & download - 

[http://cdimage.ubuntu.com/trusty/daily-live/current/](http://cdimage.ubuntu.com/trusty/daily-live/current/)

---

### Post by SeijiSensei on 2015-01-25
I still can't tell if you're trying to install Linux on the hard drive, or just run it from the USB key?  If the former, it's very likely that the entire 320 GB hard drive is devoted to Windows leaving you no free space to install Linux.  There are methods to repartition the drive, but I'll leave you in the capable hands of others here who know more about this than I.

---

### Post by Quarkrad on 2015-01-25
There are other methods to do this, but if you want to install on your hard disk, you can create the new partitions for Ubuntu first.  To do it this way (for win 7) go:
Start
Control Panel
System and Security
Administrative Tools
Computer Management
Disk Management

for other versions of Windows just get to Disk Management via Contol Panel.  Have a look at your C partition and see how much space you have on it.  Post back and tell us how much of C drive you are using and how much free space it has.   (Normally the majority of free space left (on a Windows machine)  is on the C drive/partition).  We can then decide what new partitons to create and whether to do this first via Windows or during the Ubuntu install. DONOT attempt to create any new partitons via Disk Management before backing up any of your data first.

---

### Post by flaymond on 2015-01-25
Firstly, can you view the partition on the USB? If yes, please tell...how many partition it had, and how much for a partition (if more than one)

Second, try Ubuntu 14.04.1(stable release) instead of 14.10 (14.10 is an experimental release, so yes. It's buggy)

---

### Post by GrouchyGaijin on 2015-01-25
Silly question but are you sure your Mac can't burn a CD/DVD?  Did I miss something in the description of the other computer you described as a Mac?

---

### Post by bapoumba on 2015-01-25
> **GrouchyGaijin said:**
> Silly question but are you sure your Mac can't burn a CD/DVD?  Did I miss something in the description of the other computer you described as a Mac?
If there is no cd drive (MBAir for ex) :)
Make a bootable usb drive from MacOSX (stop before installing on the Mac ;)):
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)

---

