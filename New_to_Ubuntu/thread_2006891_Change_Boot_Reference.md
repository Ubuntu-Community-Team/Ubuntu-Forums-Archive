---
title: "Change Boot Reference"
date: 2012-06-19
forum: New to Ubuntu
---

### Post by sarcasticphoenix on 2012-06-19
Hello, I am new to Ubuntu and Linux.
I am trying to install Ubuntu on to a computer.
It came with no operating systems.
It is a RAID hard disk or something. I do not know much about that.
I wanted to go to the usual routine of putting the install disk into the computer, booting off of it, and installing to the Hard Disk... but I ran in to a problem.
The computer boots only from devices with operating systems already installed.
I tried booting from the Ubuntu DVD many times, but failed.
I decided to install Ubuntu to a USB, boot from it, and then install Ubuntu directly to the Hard Drive from there.
So I went on a normal netbook, booted from the DVD, and installed Ubuntu to the USB. I followed the tutorial on the Ubuntu Wiki. It works fine.
The tutorial is at:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
However, this tutorial says:
> You will also need to manually edit the menu.lst file of the new USB installation to change the boot references to /dev/sda, rather than /dev/sdb (or /dev/sdc etc.).
This tutorial must be very old, for GRUB2 does not have the menu.lst it used to have. I do not know how to change the boot references with GRUB2.
Although it says the step is not always necessary, I do not want to fail to boot into Ubuntu (Nor do I want to turn on the very loud computer too many times.) How do I change the boot reference in GRUB2 from sdb to sda?

---

### Post by oldfred on 2012-06-20
Welcome to the forums.

That thread is older. Most installs to a USB stick do not require any editing to boot. But you do have to change BIOS to boot from USB flash drive. Most newer BIOS also have a one time boot key (f12 on my system) to choose what to boot. Your DVD should have worked the same way.

This is the Ubuntu instructions to install.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If you have nVidia video card you also may have to use a boot parameter to get it to boot.
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by sarcasticphoenix on 2012-06-20
Thank you for the help.
I will report back once I test the USB drive once more.

Edit 8:47AM:
I nearly broke the USB where it was installed, so I will try once I make sure that the USB isn't broken.

This might be off-topic, but is there a way I can get my computer to realize that the Ubuntu install disk is what it is supposed to boot from? I remember having to launch the DVD after logging in to Windows to boot into the Ubuntu installer, but Windows is not installed on my computer.
Here is a link:
[http://www.ebay.com/itm/140696037376?ssPageName=STRK:MEWNX:IT&_trksid=p3984.m1439.l2649#ht_965wt_1272](http://www.ebay.com/itm/140696037376?ssPageName=STRK:MEWNX:IT&_trksid=p3984.m1439.l2649#ht_965wt_1272)
Maybe it is a BIOS problem.

---

### Post by jmfal on 2012-06-20
You will have to enter bios/setup and change boot order/priority  to your dvd/cd drive

---

### Post by sarcasticphoenix on 2012-06-20
Yep, done the boot order.
However, even if I set to boot from DVD, it will spam "No OS"
It must be the crappy BIOS.
I plugged in the Ubuntu flash drive...
Boots to grub
Says there is an error when I try to boot...
What do I do?
EDIT:
Oh great, when I rebooted to get the Error Message again to write it down, the comp spammed to me (again) no operating systems found. Great.
Please tell me ANY way I can just smash Ubuntu onto the Hard Drive.
EDIT:
The server boots, must be because the USB is half broken.
The GRUB menu is all corrupted. All I see are purple and black horizontal bars. Will NOMODESET help?

EDIT:
Grub is fine.
Server boots.
Only one problem now.
I try to boot to Ubuntu:
error: hd0 read error
error: no such device: a9945... I could not write it down because it exits quickly.
I try again:
error: no such partition.
What?

---

### Post by oldfred on 2012-06-20
That is a RAID server, not a desktop. You always should have a working liveCD to make repairs but to install to a server you need RAID and maybe LVM drivers which are not on the Desktop install and liveCDs.

The alternative or text based install or the server install has the RAID drivers to let you install to a RAID system.

[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)
There is also a link to the server install in above page. Not sure if your system is 32bit or 64bit, so be sure you have the correct version.

---

### Post by sarcasticphoenix on 2012-06-20
Thank you for the help.
I followed the directions to install Ubuntu.
I should have made a separate partition for GRUB2, for I tried to install GRUB2 when prompted, but I couldn't install. I even tried sticking a USB drive in and installing GRUB2 on to there.
I ended up having to skip that step, but other than that, I followed all directions.
I now have another problem.
I try to boot from the Hard Drive after installation, but all I see is a black screen with a blinking cursor. I can press keys such as Alt, Ctrl, Del, etc. but whenever I press any other key, such as letters, it sends a beep through the speakers.
Also, I tried to install GRUB2 afterwards with the Ubuntu DVD, but now I once again get the "No operating systems found" spam.
Is there anything I can do? Should I re-burn the install disk?

---

### Post by drs305 on 2012-06-20
Did you follow *oldfred's* advice about installing from the Alternate CD? If you are using RAID or LVM the Alternate CD/DVD is the one to use. I don't know if you can install with a normal CD and just install GRUB from the Alternate CD.

---

### Post by oldfred on 2012-06-20
I do not know RAID as it is not common for desktops, but I think you have to install grub2's boot loader to the RAID drive root not the normal sda MBR.

To use liveCD with RAID each time you boot liveCD you will have to add the RAID drivers.
Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm

I think Boot-Repair also works.
Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by sarcasticphoenix on 2012-06-20
I am downloading the Boot Repair Disk and the Text Install now.
The server is always stuck on the black screen with a blinking cursor.
I have looked at many tutorials online which all say to use a live CD or DVD.
However, the server seems to ignore all bootable disks now, hence I tried to boot off of the same Server ISO DVD again, and I got the No OS spam every time.
If the Boot Repair and the Text Only do not work, is my server bricked?

EDIT

Neither worked.
I am pretty sure I am
BRICKED

Can I take the hard drive out and plug it in to another computer? And install from there?

---

### Post by oldfred on 2012-06-20
Have you tried a full power down or cold boot. Sometimes BIOS seems to get locked up.
You should get BIOS boot screen and it should show options on how to set boot order. BIOS should also tell you it can see hard drives. If BIOS does not see a drive, then it will never be bootable.

Did you correctly install to CD? You do not copy it, but have to use the instructions/software to extract as that also creates a bootable CD or USB flash drive.

As last resort you can remove drives, but since it is RAID you have to remove both?

---

### Post by sarcasticphoenix on 2012-06-20
Yes, I have turned the server on and off many times while trying to get the server to work.
I only have booted from devices shown in bios boot order menu.
Yes. I burned the DVD correctly using ImgBurn.
For the last resort, i do not know what the RAID disk looks like or where it is stored within the server. Only if I could change the drive from the RAID disk to a normal Hard Disk without having to disassemble the server entirely... I do have a couple of spare hard disks after replacing HDDs with SDDs, but the server itself is SO old that I have not found a guide to tweaking it on the internet yet.
Any tips? Any ways I could possibly fix the server? I've tried reburning the Ubuntu server iso on to a USB (I do not want to burn 10 of the same iso files) and booting from it, no luck. I am stuck with Ubuntu installed but with no GRUB, the screen is black with only a flashing cursor thing that won't let me type, and I cannot boot into the installer. I heard the black screen with cursor is common on nVidia devices (or however it is spelled), I have seen the way to fix it somewhere (I can look in browser history), but the DVD won't boot, so I am stuck.

---

### Post by oldfred on 2012-06-20
If it is that old it may not boot from USB flash.

Often a server like that is totally designed as a server and the RAID is hard ware not software, but every brand/design can be different. You may only be able to use RAID drives of a certain type and only with the same RAID hardware. It is not like the almost standard desktop computer. Or it could just be the computer and is designed to hook up to another chassis that has many RAID hard drives.

This does not look like something an absolute beginner should start with. Some in the server sub-forum may know more, but expect you to be knowledgeable of what RAID is at least.

Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
parted (3.0) completely removes filesystem creation and modification support, except for filesystem probing to determine what's in a partition.

---

### Post by sarcasticphoenix on 2012-06-21
I am used to installing operating systems to computers and such, for I have done it one too many times while trying to fix a netbook. I can usually solve almost any problem by common sense, but the "bricked" server is different. I just cannot understand why Ubuntu will not boot. The setup did tell me that I could boot without GRUB2 by entering commands, but it will not let me. The server was made somewhere around 2006.

EDIT:
I know basically what RAID is. Only if I could remove it and put in a normal hard drive... but that will leave a large gap within the server.
The RAID disks must be the four numbered boxes shown in this image. There is nothing else that could be the RAID disk inside the server, it is the only thing that looks like it could hold 2TB.
[IMG]http://img805.imageshack.us/img805/8258/raidj.jpg[/IMG]
Also, should I ask the question over at the Server forums?

---

### Post by oldfred on 2012-06-21
If it is hardware based RAID I do not know if you can even remove it. If software you can remove the RAID meta data and in effect convert to what looks like 4 hard drives.

From a liveCD you have to add in the RAID software.

The Boot-Info report may not show much as nothing is installed, but try running it and post link.
Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

Everytime you boot liveCD install this:
sudo apt-get install mdadm

Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=1777458](http://ubuntuforums.org/showthread.php?t=1777458)
[http://ubuntuforums.org/showthread.php?t=1338445&page=5](http://ubuntuforums.org/showthread.php?t=1338445&page=5)
Software RAID w/mdadm driver
[https://help.ubuntu.com/11.10/serverguide/C/advanced-installation.html](https://help.ubuntu.com/11.10/serverguide/C/advanced-installation.html)

Only if you totally want to break the RAID and it is software RAID.
Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
probably for all 4 drives???
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by sarcasticphoenix on 2012-06-21
I do know that there are 4 500GB Seagate Hard Drives.
There is a option during boot to change and configure RAID (I think it was by nVidia.) I once deleted the RAID setup, but it just showed me the same setup screen, obviously the server wants me to have a RAID disk.
However, I did find that I can change the RAID type, such as striped, mirrored, or mirrored stripe. Since I ran out of time, I changed it back to RAID5, but I will experiment with that later. Also. When setting up the RAID, it gives me the option to erase the MBR. Could be useful, but I kept the MBR as is.
Also, I tested other bootable disks to see if they worked (to see if the install disk not working was an Ubuntu problem.) I tried LinuxMint, Debian, and even Windows Server 2012 RC, but all failed. The server must hate booting installers.
As usual, Ubuntu still won't boot, and I cannot load a Live CD to fix GRUB2. I did find that I can literally remove hard drives by sliding the boxes out shown in the image earlier.
Tomorrow, I will test the various things to fix everything.

---

### Post by jmfal on 2012-06-21
Are you trying to turn this server into a desktop or an ubuntu server?

---

### Post by sarcasticphoenix on 2012-06-21
I am trying to turn it into a server.
If there is any remaining RAM while hosting the server, I might browse the web or something if I am too lazy to turn my laptop on.
I bought this server because my laptop isn't good enough for a server.

EDIT:
Bootable stuff works again, yay.
One of the USB ports were broken.

---

