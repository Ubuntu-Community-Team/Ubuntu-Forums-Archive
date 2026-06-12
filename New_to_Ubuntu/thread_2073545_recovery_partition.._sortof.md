---
title: "recovery partition.. sortof"
date: 2012-10-19
forum: New to Ubuntu
---

### Post by potolip on 2012-10-19
is it possible to make a recovery partition for ubuntu?

i was thinking in the way one makes a bootable usb-stick but from the HDD

i know in windows its fairley easy. just like making a usb-instalation drive but with another letter in DISKPART

but i dont know if it can be done in ubuntu. i know the drives are callled /dev/s.. and something  like a,b,c, and so on for drives. and numbers for the volumes. but can i do something like that with GPartEd?

im installing ubuntu on a fresh computer with a disc on a borrowed optical drive. the point is not to have any. and strangley i couldnt get a hold of a stick. and since a stick costs more than a drive i wanted to check if i could make a recovery partition for ubuntu in on HDD for future instalations

next month i will be adding a SSD and i would like to re-install it then, either directly from that partition or if i copy it to the ssd. dont matter to me as long as it works.

when i get my SSD i was planing to dualboot with windows. 
  i wanted to have 2 recovery partitions on the SSD one with the ubuntu iso and one with the windows iso.... is this possible at all?  

my MoBo has UEFI if that helps any.

---

### Post by Mark Phelps on 2012-10-20
What you're describing with Windows is not actually a Recovery partition.  OEMs install those in prebuilt Windows PCs and they consist of a compressed Windows image file and the software needed to erase the disk, reformat it, and expand that compressed file onto the disk.  That is very different from simply making a copy of Windows on a spare partition.

If you just want a restorable copy of your Ubuntu setup, you can do the same by using Clonezilla to image the partition(s) onto an external drive. You can then later restore Ubuntu from that image.

---

### Post by potolip on 2012-10-20
> **Mark Phelps said:**
> What you're describing with Windows is not actually a Recovery partition.  OEMs install those in prebuilt Windows PCs and they consist of a compressed Windows image file and the software needed to erase the disk, reformat it, and expand that compressed file onto the disk.  That is very different from simply making a copy of Windows on a spare partition.

If you just want a restorable copy of your Ubuntu setup, you can do the same by using Clonezilla to image the partition(s) onto an external drive. You can then later restore Ubuntu from that image.

your'r right. i dont want a recovery, i want the installation files, the reformat tool and the rest of that software goodness that comes with the liveCD but from  my harddrive.

why?  yes.. i have i new machine and i did'nt equipp it with a optical drive. i dont have a usb stick close to 4gb i got a 1.5 TB external drive with 500-600 gb of Nintendo Wii games on the start of the disc.

so im borrowing a optical drive from my neighbour to install ubuntu and i would want to migrate the installation files to somewhere where they are safe from being formated so i can use them again soon when i buy me a SSD... (and avoid to borrow a optical drive again).

why dont i just buy a usb stick?...

  well... i just spent 1000 USD on a new build and on my next shopping spree i will buy ssd, watercooling and peripherals. and because i have my external drive i dont want to spend money on a stick

how can i do this?

---

### Post by Lisiano on 2012-10-20
I got a interesting idea I am going to test out in a minute, if it works, I'll write about it here. What I'm thinking is using the same installer from the CD to install Ubuntu from within an Installed Ubuntu. Might take a little while to test if it works like I think it will.

---

### Post by oldfred on 2012-10-20
The ad I just saw in the paper was for a USB flash drive for $0.50 per GB. Smaller ones were more but under a $1. It is worth having just to have another way to boot or repair system. You should also have a Windows repair USB.

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

A bit more advanced but you really just need to follow the details:

You can use grub from any device, another hard drive, flash drive, CD or anything your system will boot to boot the install ISO directly. That is not the normal extraction into a flash drive for install.

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

How to make a GRUB_II USB
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb

I have used the above to install grub2 to NTFS, FAT & Linux formated drives and created my own grub.cfg to boot ISO on any device. I also made a Windows repair USB, then installed grub to boot the Windows and added extra Linux ISOs to make a repairUSB for just about anything.

---

### Post by Lisiano on 2012-10-20
Okay, my little test failed.

What you should do is just go and buy a tiny USB Flash drive. As oldfred said, they are dirt cheap. Just skip a beer and get a Flash drive instead. (Or skip a pizza/cola/root beer/w.e. if you don't drink beer)

---

### Post by potolip on 2012-10-20
thanx  great stuff there...

so lets say i install ubuntu from a disc to my HDD,
then when i get my SSD i format it to, (lets say) fat32.
  setup it up as if it was a grub2 usb.. 
store 2 iso's (1 for ubuntu, 1 for windows)in the (/)system dir. 
  edit the grub menuentry custom file. 
 disconect the HDD. reboot. boot ubuntu from menuentry. 
   install ubuntu. do the same with windows let it format its own space. 
  recover the grub2. 
     and Voilà

is this the theory of it? 

when do i resize the partition? if ever.
does the ubuntu installer format its own space to ext3/4 or do i have to do it before?

can i use a virtual drive to mount the liveCD and restore grub2 after instaling windows?
and will i need to re-edit the menuentry custom file?

---

### Post by sandyd on 2012-10-20
> **potolip said:**
> thanx  great stuff there...

so lets say i install ubuntu from a disc to my HDD,
then when i get my SSD i format it to, (lets say) fat32.
  setup it up as if it was a grub2 usb.. 
store 2 iso's (1 for ubuntu, 1 for windows)in the (/)system dir. 
  edit the grub menuentry custom file. 
 disconect the HDD. reboot. boot ubuntu from menuentry. 
   install ubuntu. do the same with windows let it format its own space. 
  recover the grub2. 
     and Voilà

is this the theory of it? 

when do i resize the partition? if ever.
does the ubuntu installer format its own space to ext3/4 or do i have to do it before?

can i use a virtual drive to mount the liveCD and restore grub2 after instaling windows?
and will i need to re-edit the menuentry custom file?

Hmm.

I don't know if Windows 7 can be boot by using Grub2. There was another OP looking to do that - and they never managed it.


Anyways, you can do something like this -

Partitions:

1: Use for Unetbootin data
2: Use to backup data.

In addition, instead of installing ubuntu with all data on one partition, you can keep /home on a seperate partition so that if you screw up Ubuntu, you can reinstall it without losing data.

You just have to do a custom setup on the reinstall, and select the sperate /home partition as /home.

---

### Post by oldfred on 2012-10-20
You cannot boot the Windows ISO from grub2. 

ISO's have to be configured for loop mounting. But you should be able to Install Ubuntu from one drive to another without issue. I now install from my rotating drive to my SSD that way (really quick). 

The only way I was able to use grub with a Windows repairCD/USB was create the Windows CD and use the CD to install the Windows repair to the USB. I was not able to find any Linux tools that would correctly extract the Windows ISO.  Once I knew the USB booted Windows I just overwrote the Windows boot loader with grub and added a Windows boot entry to grub.cfg. I did have to be careful not to create two /boot or /Boot entries as that can happen. And I then put the Ubuntu & Linux repair ISO in another partition on the flash drive I was using.

---

### Post by potolip on 2012-10-23
Bumping this thread.


been quiet for somedays cuz i ordered a USB stick  still havnt gotten it tho.. i live out in the middle of the baltic sea,

is there a way to simply switch between grub2 and windogs boot manager.

---

### Post by oldfred on 2012-10-23
It is easy if you have Ubuntu current liveCD and a good Internet connection. Not sure about from the middle of the Baltic sea.

Also most Linux repair disks also make it easy as they can reinstall a Windows like boot loader.

[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)


Whenever I upgrade I make sure I have several repair tools like Boot-Repair, Ubuntu liveCD, Knoppix, Supergrub, etc. I used to go thru a lot of live CDs with each upgrade as I was also upgrading my repair toolbox. Now I just have them on a bootable USB which then is easy to update.

---

### Post by potolip on 2012-10-23
still havnt a usb stick but i guess i will have to wait then ...

so theres nothing i can do in uefi that allows me to change MBR to direct the boot towards either of those loaders?

btw...
the internet is fine we have a nice thick cable in the bottom of the sea togeter with russias biggest gas pipe connecting us to EU..

---

### Post by oldfred on 2012-10-23
UEFI boot does not use MBR, and MBR boot does not use efi partition. So how have you installed?
Both Windows & Ubuntu need to be in either BIOS/MBR or UEFI/gpt modes to work together.
Ubuntu's 64 bit version offers both UEFI or BIOS modes to boot liveCD or USB and then installs in that mode. I think Windows works the same way.

Boot-Repair will convert an Ubuntu install in BIOS mode to UEFI mode if that is the issue and Ubuntu is installed to gpt drive.

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by potolip on 2012-10-23
i have installed both os now without discs but my goal was to have the installation isos on the hardrive and i have that just finding it a bit awkward booting the iso's 

no troubles at all with with the dual boot

in some days i will get my usb stick and probaly all my issues will be solved



thanx for the help

---

