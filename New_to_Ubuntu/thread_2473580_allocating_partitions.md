---
title: "allocating partitions"
date: 2022-04-07
forum: New to Ubuntu
---

### Post by yc2 on 2022-04-07
Hi,

I have an old 16.04 running dual boot. I wish to keep dualboot and home partition and only install 20.04. I dont understand how to allocate partitions

sda4 should be swap, like before, format
sda5 should be system, like before, format
sda6 home, like before, keep data

I am not sure where to put boot loader (I probably use GRUB, but not sure)

[http://imgur.com/a/geTwSck](http://imgur.com/a/geTwSck)

Grateful for assistance

---

### Post by oldfred on 2022-04-07
You should be able to use your live installer and add Boot-Repair via ppa. 
This report documents your system. I periodically run it, so my backups include the report.

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)            
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by yc2 on 2022-04-07
Thank you. I got a bit further. I believe this is correct partitions. But where should bootloader be?

[http://imgur.com/a/6fzSkd2]("http://imgur.com/a/6fzSkd2")

---

### Post by yc2 on 2022-04-07
Thanks for your assistance. I got stuck a little on other issues and will come back later with Bootinfo summary
Cheers

---

### Post by grahammechanical on 2022-04-07
A lot will depend on what sda1 (FAT32) is. Do you have a UEFI motherboard? Is sd1 a EFI boot partition? If it is then Grub should installed into sda1. Both Windows and Ubuntu (Grub) boot files can reside in a EFI boot partition. Where are the Grub boot files for 16.04? Are they in sda1?

Regards

---

### Post by yc2 on 2022-04-07
> **grahammechanical said:**
> A lot will depend on what sda1 (FAT32) is. Do you have a UEFI motherboard? Is sd1 a EFI boot partition? If it is then Grub should installed into sda1. Both Windows and Ubuntu (Grub) boot files can reside in a EFI boot partition. Where are the Grub boot files for 16.04? Are they in sda1?

Regards

Thank you. it was a while ago I set this up. This is how I boot it now

[http://imgur.com/a/QoqUJdT](http://imgur.com/a/QoqUJdT)

ought to be sda1?

lets see if I can download a repair usb and only run the bootinfo

Your assistance appreciated

Cheers

Edit:
maybe not sda1? If I start choose sda1 alternative from the screen it goes straight into windows

---

### Post by yc2 on 2022-04-07
The Boot Repair ISO I put on a USB will not boot. I don't know why.
Same Rufus that produced the Live CD that booted!

The one I boot from is the first:

[http://imgur.com/a/fhqhEOr]("http://imgur.com/a/fhqhEOr")


Gparted:
[http://imgur.com/a/1S329ml](http://imgur.com/a/1S329ml)

Installed boot info into old system on disc, but I dont know how to run the program
> sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt update

sudo apt install -y boot-info && boot-info

---

### Post by oldfred on 2022-04-07
Typically better to just use the Ubuntu live installer and use the ppa to add Boot-Repair to it. 
The Boot-Repair ISO is not updated as frequently, but is based on Lubuntu so works with older systems.

What model HP?
What video card/chip?

If install is UEFI which it looks like, you must boot live installer in UEFI boot mode.
Some tools to create live installer make it UEFI/gpt only or BIOS/MBR only. Others make it as either, but then you have to choose the UEFI: boot entry for the flash drive, not the flash drive entry which is just a BIOS boot.

You always install grub to a drive like sda, never to a partition.
But with UEFI, the installer always finds the ESP - efi system partition on the first drive and installs the boot files into that ESP. Any choices shown in install screens only work with BIOS installs.

---

### Post by yc2 on 2022-04-07
> **oldfred said:**
> Typically better to just use the Ubuntu live installer and use the ppa to add Boot-Repair to it. 
The Boot-Repair ISO is not updated as frequently, but is based on Lubuntu so works with older systems.

What model HP?
What video card/chip?

If install is UEFI which it looks like, you must boot live installer in UEFI boot mode.
Some tools to create live installer make it UEFI/gpt only or BIOS/MBR only. Others make it as either, but then you have to choose the UEFI: boot entry for the flash drive, not the flash drive entry which is just a BIOS boot.

You always install grub to a drive like sda, never to a partition.
But with UEFI, the installer always finds the ESP - efi system partition on the first drive and installs the boot files into that ESP. Any choices shown in install screens only work with BIOS installs.

Thank you. I come back tomorrow with what info I can gather.
Cheers

(like you say, the boot-info doesnt come up when I "search my computer" even though it installed OK. I will try live CD)

---

### Post by yancek on 2022-04-07
Select the option to Create BootInfo Summary and do not try to make any repairs.  You should get a link when it finishes and you should post it here and members will be able to view the output and make suggestions.

Which release of Ubuntu are you trying to install?  I would not install 22.04 yet as it has not reached final release point so is still in the testing stage.

What is the current status?  Are you able to boot windows?  Have you installed the new Ubuntu release over your 16.04?

One of your images shows an Ubuntu entry in your BIOS firmware.  What happens when you select to boot it?

You should get a pop up window asking if you want to create a boot info summary.  Click that.  If that doesn't work or you don't see it, just open a terminal and type:  boot-repair

---

### Post by yc2 on 2022-04-07
I run dual boot 16.04, will install 20.04 and keep the home partition.
boot-info will install on disc 16.04 but will not find command when I type boot-info or boot-repair
use HP pavillion x360

here is some of the requested info

> xxx@x360:~$ lspci
00:00.0 Host bridge: Intel Corporation Device 2280 (rev 35)
00:02.0 VGA compatible controller: Intel Corporation Device 22b1 (rev 35)
00:0b.0 Signal processing controller: Intel Corporation Device 22dc (rev 35)
00:13.0 SATA controller: Intel Corporation Device 22a3 (rev 35)
00:14.0 USB controller: Intel Corporation Device 22b5 (rev 35)
00:1a.0 Encryption controller: Intel Corporation Device 2298 (rev 35)
00:1b.0 Audio device: Intel Corporation Device 2284 (rev 35)
00:1c.0 PCI bridge: Intel Corporation Device 22c8 (rev 35)
00:1c.2 PCI bridge: Intel Corporation Device 22cc (rev 35)
00:1c.3 PCI bridge: Intel Corporation Device 22ce (rev 35)
00:1f.0 ISA bridge: Intel Corporation Device 229c (rev 35)
00:1f.3 SMBus: Intel Corporation Device 2292 (rev 35)
02:00.0 Network controller: Intel Corporation Wireless 3165 (rev 81)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
xxx@x360:~$ 
xxx@x360:~$ efibootmgr
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000,3000,0001,2001,2002,2004
Boot0000* ubuntu
Boot0001* Windows Boot Manager
Boot2001* EFI USB Device
Boot3000* Internal Hard Disk or Solid State Disk


I will try to install boot-info on live cd or install 20.04 boot on disc and not partition
Ill come back about it

---

### Post by TheFu on 2022-04-07
Before you do too much, please, please, please, backup any data you can't afford to lose and have both a 20.04 boot/installer and a Windows boot/installer available.  

While it is possible to do an install over an existing install, just 1 error that isn't clearly recognized at the time will cause a really bad day.  That's why everything you don't want to lose should be backed up first.  Be certain you know how to put it back, should something bad happen too. Have a plan, before you need it.

---

### Post by ActionParsnip on 2022-04-08
I also suggest running a final full backup of your data before embarking on this. This will protect your data from catastrophe

---

### Post by yc2 on 2022-04-08
> **TheFu said:**
> Before you do too much, please, please, please, backup any data you can't afford to lose and have both a 20.04 boot/installer and a Windows boot/installer available.  

While it is possible to do an install over an existing install, just 1 error that isn't clearly recognized at the time will cause a really bad day.  That's why everything you don't want to lose should be backed up first.  Be certain you know how to put it back, should something bad happen too. Have a plan, before you need it.

> **ActionParsnip said:**
> I also suggest running a final full backup of your data before embarking on this. This will protect your data from catastrophe.
Data will be backed up. In the old days sometimes some people said "as long as you don't format the wrong partition we can revive your system". But I am not sure it is correct.

---

### Post by yc2 on 2022-04-08
boot-info that worked from the live USB (but not from the hard disk):
[https://paste.ubuntu.com/p/JpCVKfg8yh/]("https://paste.ubuntu.com/p/JpCVKfg8yh/")

Impressive info roundup. Please help me interpret.

The first question is: What should I choose for "device for boot loader installation" in the "allocate partitions" part, during install, please?

(or will I be given an alternative to completely skip boot loader installation in the following steps, and just use the old one?)

[https://imgur.com/a/geTwSck](https://imgur.com/a/geTwSck)

Thanks a lot, I appreciate all help here.


Edit: sda8 is a recovery partition for Windows. Can it ever be used to recover a blank Windows system after repartitioning?

Just out of curiosity: "Suspend" works (really fine and quickly) from the Live USB. I didnt expect that. I thought the RAM were busy with other stuff?

---

### Post by QIII on 2022-04-08
> **yc2 said:**
> But I am not sure it is correct.

What matters is what sorts of mistakes we humans can make and how quickly a machine can execute the mistake before we can even react to try to stop it.

---

### Post by yc2 on 2022-04-08
> **oldfred said:**
> Typically better to just use the Ubuntu live installer and use the ppa to add Boot-Repair to it. 
The Boot-Repair ISO is not updated as frequently, but is based on Lubuntu so works with older systems.

What model HP?
What video card/chip?

If install is UEFI which it looks like, you must boot live installer in UEFI boot mode.
Some tools to create live installer make it UEFI/gpt only or BIOS/MBR only. Others make it as either, but then you have to choose the UEFI: boot entry for the flash drive, not the flash drive entry which is just a BIOS boot.

[B]You always install grub to a drive like sda, never to a partition.
But with UEFI, the installer always finds the ESP - efi system partition on the first drive and installs the boot files into that ESP. Any choices shown in install screens only work with BIOS installs.[/B]
I am still reading up a little but I will probably set the boot device to sda during install. It will likely be overridden. If it asks to rewrite anything related to boot, I will negate it.
Thanks, Cheers.

Just as a reply to an earlier question: The Ubuntu entry in my Grub starts the 16.04 system I will overwrite (it works fine but doesnt update properly).

---

### Post by oldfred on 2022-04-08
As long as you boot installer in UEFI mode, it will auto install grub2's boot files into the ESP.
If using Something Else the options on where to install boot loader do not matter. It uses the ESP. 
Since only one drive, it will  not matter.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

You need to use the Something Else install option to be able to choose which partitions are which. Know which is which as I have created new partitions and installed to wrong one.

But HP does not recognize efibootmgr which grub uses to reset boot order.
You must have used UEFI settings menu to change boot order before, so that may just stay the same?

---

### Post by TheFu on 2022-04-08
> **yc2 said:**
> Data will be backed up. In the old days sometimes some people said "as long as you don't format the wrong partition we can revive your system". But I am not sure it is correct.

It is, but ... we all make mistakes. Picking the wrong partitions is very common when doing work like this by everyone - beginners and experts.

Avoiding a really bad day isn't too hard.


> **yc2 said:**
> Just as a reply to an earlier question: The Ubuntu entry in my Grub starts the 16.04 system I will overwrite (it works fine but doesnt update properly). 
That's because support for 16.04 ended. There aren't any patches unless you have ESM support. [https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)  I think ESM is great for specific commercial needs, but a bad idea for individuals who are just lazy.

---

### Post by yc2 on 2022-04-09
> **TheFu said:**
> It is, but ... we all make mistakes. Picking the wrong partitions is very common when doing work like this by everyone - beginners and experts.

Avoiding a really bad day isn't too hard.

That's because support for 16.04 ended. There aren't any patches unless you have ESM support. [https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)  I think ESM is great for specific commercial needs, but a bad idea for individuals who are just lazy.
I see, maybe good to have a fresh start sometimes?

> **oldfred said:**
> As long as you boot installer in UEFI mode, it will auto install grub2's boot files into the ESP.
If using Something Else the options on where to install boot loader do not matter. It uses the ESP. 
Since only one drive, it will  not matter.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

You need to use the Something Else install option to be able to choose which partitions are which. Know which is which as I have created new partitions and installed to wrong one.

But HP does not recognize efibootmgr which grub uses to reset boot order.
You must have used UEFI settings menu to change boot order before, so that may just stay the same?
I probably must have changed the UEFI settings to put Ubuntu first. It was a while ago and I don't remember. I just remember GRUB setup file. Looks good now after installation and works fine:

[http://imgur.com/a/4iIqz4b]("http://imgur.com/a/4iIqz4b")

I try to double check all: filesystem (NTFS for windows), partition number/order and size, making partitions different sizes. I just do this seldom so I try to be extra careful. Those who do it every day might become too confident ;)  But anyone can fail anytime.

Installation went smooth. It seems Ubuntu is continuously making things easier. 

I was careless and accepted the given username during install and now have a new username and home directory. (Maybe I wouldn't have dared use the old user name either, considering a risk the old home directory would have been destroyed?) The old data are now accessible in a home directory bearing the name of my old user name. So it works fine. But maybe I could later move the data to the new home directory without any problems in ownership. The old user does not exist, which I didn't think of during install. Maybe I could also create a new user with the old name now? 

```
useradd -d /home/olduser olduser
sudo usermod -aG sudo olduser
```

But what you should probably do is just simply to use your old user name during install. It will connect to your old home directory without erasing it. I forgot that.

I also have an ASUS TUF that came with Win 10 and seems to have upgraded itself to 11. When time permits I will create partitions and install dual boot. It seems the Ubuntu installer will take care of UEFI without any problems so I can hopefully make an install without any additional fixing.

Thanks a lot everyone. This support is really very valuable. Also good to get access to Ubuntu Linux. The computer just does what it is told and doesn't delay your work by unknown simultaneous acitivty, saves computer power, no commercial overhead, updates only when you ask, powerful and simple-to-run programs easy to find and install, situations often resolved more easily by using terminal and searching the Internet for commands if needed, new install simple, data and system are kept apart on home partition. Windows partition easily accessible, f.ex. playing videos on Windows partition, just clicking them.

---

### Post by TheFu on 2022-04-09
On the file system, it isn't the username or groupname that matter. It is the userid and groupid.  If those match between the old and new HOME directories, just move the old one over to be under your new username, then go into it and mv all the files/directories up 1 level (to the parent).

If we have:
/home/new
/home/old

Then running these commands will do it.
```
mv     /home/old      ~/
mv    ~/old/*     ~/
mv ~/old/.[a-Z0-9A-Z] ~/

```
Be happy.

BTW, changing a username from old --> new isn't THAT hard either.  Or from new ---> old which is a tiny bit harder, but really just accounting, not very complex. 4 files for the later change.

> updates only when you ask
sadly, that isn't true. Snap packages update whenever they like. I think the default is to check for updates daily and to keep 3 versions of the snap package on the system - bloat.

---

### Post by yc2 on 2022-04-09
> **TheFu said:**
> On the file system, it isn't the username or groupname that matter. It is the userid and groupid.  If those match between the old and new HOME directories, just move the old one over to be under your new username, then go into it and mv all the files/directories up 1 level (to the parent).

If we have:
/home/new
/home/old

Then running these commands will do it.
```
mv     /home/old      ~/
mv    ~/old/*     ~/
mv ~/old/.[a-Z0-9A-Z] ~/

```
Be happy.

BTW, changing a username from old --> new isn't THAT hard either.  Or from new ---> old which is a tiny bit harder, but really just accounting, not very complex. 4 files for the later change.


sadly, that isn't true. Snap packages update whenever they like. I think the default is to check for updates daily and to keep 3 versions of the snap package on the system - bloat.
[ Just forget this post please. ]

---

### Post by yc2 on 2022-04-09
> **TheFu said:**
> On the file system, it isn't the username or groupname that matter. It is the userid and groupid.  If those match between the old and new HOME directories, just move the old one over to be under your new username, then go into it and mv all the files/directories up 1 level (to the parent).

If we have:
/home/new
/home/old

Then running these commands will do it.
```
mv     /home/old      ~/
mv    ~/old/*     ~/
mv ~/old/.[a-Z0-9A-Z] ~/

```
Be happy.

BTW, changing a username from old --> new isn't THAT hard either.  Or from new ---> old which is a tiny bit harder, but really just accounting, not very complex. 4 files for the later change.


sadly, that isn't true. Snap packages update whenever they like. I think the default is to check for updates daily and to keep 3 versions of the snap package on the system - bloat.
That was simple. I am just a little rusty :oops:
Like you say the userid/groupid are the same. The old files already came up under my new username/groupname in "ls -l"
I left them like this for the time being
```
sudo mv     /home/old      ~/
```

Linux is the best of worlds, if you just know the basics.

Thank you all. Thread solved. I'll probably be back  :D

---

