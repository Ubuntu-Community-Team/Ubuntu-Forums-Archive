---
title: "HOW TO make a USB Disc with Ubuntu LiveCD and Super Grub Disc in it."
date: 2007-10-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Herman on 2007-10-14
**REVISED** on Wednesday, January 02 2008 
:) Thanks [Tekno_Cowboy]("http://ubuntuforums.org/member.php?u=360355") in post #2 of this thread. :)
[LIST]
[*]     Do you want to try out Ubuntu, Kubuntu, Xubuntu or any other *buntu and install without using a CD?
[*]     Would you like having something that works like a live CD but runs a lot faster?
[*]     Have you ever experienced a partitioning disaster of or an installation failure that could have been caused by a scratched CD or a dirty optical lens in your CD/DVD drive?
[*]     Does your computer support booting a USB disk? (Either from the BIOS or even from a GRUB menu or command line).
[*]     You can also keep it in the USB disk for any emergency you might have later on someday, the Ubuntu Live CD can be used to rescue and repair your Ubuntu operating system and re-install if that's ever necessary. It makes a great rescue disk because it leaves your CD/DVD drive available in case you want to make a file rescue that way, or you can SSH to a networked computer or copy to another USB disk too, whichever will be the easiest.
[*][Super Grub Disk]("http://supergrub.forjamari.linex.org/") is used to boot the Live CD Ubuntu operating system in the USB disk, and it can also be used for emergency booting or fixing the boot of any operating system in your hard drive too if you ever need it.
[/LIST]
This how-to is made of a combination of bits and pieces of several other how-tos on Ubuntu USB making. This how-to is different in that it uses GParted as the partition editor and [Super Grub Disk for USB]("http://supergrub.forjamari.linex.org/?section=download#usb") as the boot loader.
I got information from these other great how-tos, these are all very good,  [Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux"), [LiveUsbPendrivePersistent - Ubuntu Wiki]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent"), [LiveCDPersistence - Community Ubuntu Documentation]("https://help.ubuntu.com/community/LiveCDPersistence"), and PendriveLinux [Ubuntu 7.10 USB persistent Linux installation]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/"), 


**You'll need:**
[LIST=1]
[*]First you will need a computer that is already running Ubuntu  or some other Linux distro.
[*]You will need a USB flash memory stick or other type of USB drive of at least 2.0 GB in capacity or bigger. You might be able to get away with a 1.0 GB drive, but bigger is better a 4.0 GB or larger flash memory drive would be nice. You can also install this way in a real hard disk in an external drive caddy, it doesn't have to be a flash drive.
[*]You'll need a copy of SGD for USB, at the time of typing, the latest is [super_grub_disk_english_usb_0.9673.tar.bz2]("http://forjamari.linex.org/frs/download.php/778/super_grub_disk_english_usb_0.9673.tar.bz2")
[*]You'll also need an .iso file for whichever *buntu you want to install, or to run as a LiveCD (USB) to try it out. Super Grub Disk and Ubuntu Live CD is a good combination for a rescue disk, so you can keep this USB Disk for a rescue disk after Ubuntu is installed in your computer. You can use any Ubuntu Live CD you like.
[/LIST]

**NOTE 1:** The Ubuntu **'Alternate CD'**, *is supposed to work* if you add 'vesa vga=771' as kernel parameters, but when I tried it, the Gutsy Gibbon Alternate CD starts but fails 'mounting the CD-ROM', so I couldn't install from it. - refer: [page 3, post #23, #24, #25]("http://ubuntuforums.org/showthread.php?t=575406&page=3").
[B]
NOTE 2: Hardy Heron users:[/B] MQMike discoverd that Hardy Heron LTS wouldn't boot work in persistent mode. Please see [page 7, posts #66-69]("http://ubuntuforums.org/showthread.php?t=575406&page=7") for MQMike's special work-around that enables Hardy Heron to boot with persistence. Thanks MQMike, adrian15, meierfra and others for your hard work on that. (Starts on [Page 5, post #49]("http://ubuntuforums.org/showthread.php?t=575406&page=5").)[B]

Okay, let's get started.

Formatting your USB disk[/B]
[LIST=1]
[*]Unmount your USB disk and open GParted in Ubuntu.
[*]Delete any other partitions that were there before, (back up your data somewhere first, of course!)
[*] Make the first partition with an ext2 file system, at least 745 MiB in size. Better make it 750 MiB to be sure.
[*]Make the second partition ext3 taking up all the rest of the available space in the USB disk.
[/LIST]
**We need to label the file systems** with commands similar to the following ones
```
e2label /dev/sdb1 ubuntu710
```Where: your first partition in your USB disk is called /dev/sdb1 
If you're not sure, open GParted again and check. 
If it's something else then change your command to suit your own computer.
```
e2label /dev/sdb2 casper-rw
```Where: your second partition in your USB disk is called /dev/sdb2 
If you're not sure, open GParted again and check. 
If it's something else then change your command to suit your own computer.

**Eject and unplug your USB disk.**



**Mount your .iso file using these commands,**
```
sudo mkdir /media/ubuntu_iso
``````
sudo mount ubuntu-7.10-desktop-i386.iso -o loop /media/ubuntu_iso
```**Plug in your USB disk again**, so it will be mounted automatically in /media.
Icons should appear on your desktop.

**Note:** the name of your USB disk's partitions should now appear on your desktop as: ubuntu710 and casper-rw.

** If the ubuntu710 file system doesn't get automatically  mounted,** it may need to be mounted manually,
```
sudo mkdir /media/ubuntu710
``````
sudo mount -t ext2 /dev/sdb1 /media/ubuntu710
```Where: your first partition in your USB disk is called /dev/sdb1 
If you're not sure, open GParted again and check. 
If it's something else then change your command to suit your own computer.

**Copy the files from the .iso file to the USB disk,**
```
sudo cp -rfv /media/ubuntu_iso/* /media/ubuntu_iso/.disk /media/ubuntu710
```[B]
Super Grub Disk
[/B]```
wget http://forjamari.linex.org/frs/download.php/778/super_grub_disk_english_usb_0.9673.tar.bz2
``````
tar jxvf super_grub_disk_english_usb_0.9673.tar.bz2
```** Copy Super Grub Disk's /boot** into your USB disk's ubuntu710 partition.
```
sudo cp -rv boot /media/ubuntu710/
```**Install Super Grub Disk's IPL** to MBR in your USB disk, do something like this, but your disc and partition numbers might be different, replace with the right numbers to suit your system,
Get a GRUB shell,
```
sudo grub
``` Now. Don't copy and paste the 'grub>' part in the next few code boxes, that's the prompt, I'm just including it to indicate we're in a GRUB shell right now. Also, don't copy the outputs, just the commands. Or even better, type your own commands for this part, and remember to use your 'tab key', it's very useful in a GRUB shell.

Test to remind you which hard disks and partitions in your computer contain GRUB files,
```
grub> find /boot/grub/menu.lst 
(hd0,1) 
(hd1,0)
```Test with GRUB's 'geometry' command to find out if (hd1) is really your USB disk.
Here is an example of how to use GRUB's geometry command to verify that (hd1) is your USB disk.
```
 grub> geometry (hd1)
drive 0x81: C/H/S = 250/255/63, The number of sectors = 4030464, /dev/sdb
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
```Tell Grub which partition it's supposed to be working in, (this depends on the output from the preceding commands, and may vary between computers, please watch it and alter the command to suit your own particular machine.```
grub> root (hd1,0)
```Set the boot flag, GParted can do that too but we didn't tell it to, never mind, we''ll do it with GRUB now,
```
grub> makeactive
```Install GRUB to the partition's first sector (optional).
This also depends on the output from the earlier 'find' and 'geometry' commands, so you can be most certain that you are definitely installing GRUB to the correct partition.
```
grub> setup (hd1,0)
```Install GRUB to MBR in the USB drive, (this also depends on the output from the 'find' and 'geometry' commands)
```
grub> setup (hd1)
```Close the GRUB shell
```
grub> quit
```[B]Open your USB disk's /boot/grub/menu.lst
[/B]```
gksudo gedit /media/ubuntu710/boot/grub/menu.lst

```**Copy this entire menu.lst** from this web page (below), and go to your own  USB disk's menu.lst and go 'Edit'-->'Select All'-->'Delete'-->'Edit'-->'Paste'-->'Save', and close the file.
```
# You can edit this file to add your own distribution
# You can choose default to 0 to select first entry
# which it is usually the entry for the default distro
#
#Thank you adrian15!
#
# You can also set timeout to something as 10
#
# This is the shortcut to call Super Grub Disk (commented)
#title Super Grub Disk
## The two commands: setgrubdevice and usbshift are needed
## so that SGD works well.
usbshift

#configfile $(grub_device)/boot/sgd/menu.lst
#
# Just after default and timeout statements you have to put
# setgrubdevice so that grub device is correctly set.

default 0
#timeout 2
setgrubdevice # This is compulsory
# The two commands: setgrubdevice and usbshift are needed
# so that SGD works well.
usbshift
#gfxmenu /boot/grub/message
foreground ffffff
background 0c00ff
color white/brown yellow/cyan

title       Ubuntu Gutsy Gibbon in Persistent Mode
kernel   $(grub_device)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper persistent quiet splash --
initrd    $(grub_device)/casper/initrd.gz

title       Super Grub Disk
configfile $(grub_device)/boot/sgd/menu.lst

title      Ubuntu Gutsy Gibbon in Live CD Mode
kernel   $(grub_device)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
initrd   $(grub_device)/casper/initrd.gz 

title       Start Ubuntu in Safe Graphics Mode
kernel   $(grub_device)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper xforcevesa quiet splash --
initrd    $(grub_device)/casper/initrd.gz 

title        Install with Driver Update CD
kernel    $(grub_device)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper debian-installer/driver-update=true quiet splash --
initrd     $(grub_device)/casper/initrd.gz 

title        OEM Ubuntu Gutsy Gibbon Install (for manufacturers)
kernel    $(grub_device)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper oem-config/enable=true quiet splash --
initrd     $(grub_device)/casper/initrd.gz 

title        Check CD for Defects
kernel    $(grub_device)/casper/vmlinuz boot=casper integrity-check quiet splash --
initrd      $(grub_device)/casper/initrd.gz 

title        Memory Test
kernel    $(grub_device)/install/mt86plus  - 

title       Boot the First Hard Disk
root       (hd0)
chainloader +1

title       Boot the Second Hard Disk
root      (hd1)
chainloader +1
```Now you can exit from your terminal and close any windows you have open and reboot with the USB drive.  

**Booting the SGD USB disk**

With some computers you might be able to Boot your USB Disk for your BIOS, here's how I do that, [How I boot from my BIOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#How_I_boot_from_my_BIOS_with_my_F12_key")
Yours might be different but you might be able to do something like that.

Another way boot it would be from [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") (effective even in some computers that can't boot the USB directly from the BIOS).
If you're going to be booting USB devices again, you should make a permanent chainloader type of boot entry for that in your menu.lst. That makes booting the USB easier.

Here's an example of how to boot Super Grub Disk in your USB disk from your own hard disk installed GRUB's CLI (Command Line Interface) or some other GRUB, such as a GRUB floppy disk, a GRUB CD.
```
grub> root (    # <tab>
Possible discs are: fd0 hd0 hd1
``````
grub> root (hd1)
``````
grub> chainloader +1
``````
grub> boot
```**Enjoy!**

Regards, Herman

---

### Post by Tekno_Cowboy on 2007-12-22
This seems to work well. I wanted persistence, So I made the following changes:

1. The label of partition 2 needs to be

```
e2label /dev/sd[COLOR="Red"]X[/COLOR]2 casper-rw
```

where [COLOR="Red"]X[/COLOR] is the letter of the drive you are working with. BE CAREFUL NOT TO USE THE WRONG LETTER OR YOU MIGHT LOSE DATA!

2. I added the text in [COLOR="Red"]red[/COLOR]
```

# You can edit this file to add your own distribution
# You can choose default to 0 to select first entry
# which it is usually the entry for the default distro
#
#
# You can also set timeout to something as 10
#
# This is the shortcut to call Super Grub Disk (commented)
#title Super Grub Disk
## The two commands: setgrubdevice and usbshift are needed
## so that SGD works well.
#usbshift
#configfile $(grub_device)/boot/sgd/menu.lst
#
# Just after default and timeout statements you have to put
# setgrubdevice so that grub device is correctly set.




default 0
# timeout 2
setgrubdevice # This is compulsory
#gfxmenu /boot/grub/message
foreground ffffff
background 0c00ff
color white/brown yellow/cyan

title Ubuntu Gutsy Gibbon Live CD
kernel $(grub_device)/casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw [COLOR="Red"]splash persistent[/COLOR]
initrd $(grub_device)/casper/initrd.gz

title Super Grub Disk
# The two commands: setgrubdevice and usbshift are needed
# so that SGD works well.
usbshift
configfile $(grub_device)/boot/sgd/menu.lst

title Inicio normal / Normal Boot 
kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
initrd $(grub_device)/initramfs

title Soporte de accesibilidad / Accesibility Support -->
configfile $(grub_device)/boot/grub/menu2.lst

title Normal boot. Kernel is aware of Boot device
kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash boot_device=$(grub_device)
initrd $(grub_device)/initramfs

title Normal boot. Selecting kernel and initrd files depending on grub_device
kernel $(grub_device)/vmlinuz_$(grub_device_string) lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
initrd $(grub_device)/initramfs_$(grub_device_string)

title Selecthd test
configfile $(grub_device)/boot/grub/choose/selecthd.lst

title findp test
configfile $(grub_device)/boot/grub/choose/selectpart.lst
title set SGD variables and boot SGD

configfile $(grub_device)/boot/sgd/menu.lst
```

you don't really need the "splash", but I like it =)


If someone knows how to get this to boot like a live cd too (not just boot live cd, the whole menu), that would be great. I'd like to don a trait from Sabayon Linux and add specialized boots, like for internet browsing, gaming, and multimedia.

Otherwise, this is the only method I have tried that has actually worked for me, and you get the added bonus of Super Grub Disk, a handy utility if there every was one. You could probably modify this a little to include other utilities, like some kind of system rescue cd, that can be selected at boot. If anyone knows the best way to do this, please post it.

---

### Post by Herman on 2007-12-27
>  If someone knows how to get this to boot like a live cd too (not just boot live cd, the whole menu), that would be great. I'd like to don a trait from Sabayon Linux and add specialized boots, like for internet browsing, gaming, and multimedia.

Otherwise, this is the only method I have tried that has actually worked for me, and you get the added bonus of Super Grub Disk, a handy utility if there every was one. You could probably modify this a little to include other utilities, like some kind of system rescue cd, that can be selected at boot. If anyone knows the best way to do this, please post it.        October 14th, 2007 03:33 PM:) Okay then. let's try using the [Syslinux]("http://syslinux.zytor.com/") boot loader now. Here is the [Syslinux documentation page]("http://syslinux.zytor.com/faq.php") in case anyone wants to study up on that and add more boot options or something.
This how-to was made by combining ideas I found in the Ubuntu Wiki's[LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent"), with some ideas and a command or two I adapted from this great site, Pendrive.com's [USB Ubuntu 7.10 Gutsy Gibbon install]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/"). I mixed in a lot of my own ways of doing things with what I learned from those two sites and came up with something different. I'm starting with Super Grub Disk again, but it's in its own independant file system this time. This how-to uses GParted Partition Editor for making the partitions. It's divided into three stages and you can boot the USB after each stage to make sure that part of the how-to has been completed okay. I explained what to do and why as well, in a lot of places, so it might help other people to understand what's going on. That's to make it easier to follow as well as more educational.

** Super Grub Disk for USB + Ubuntu Gutsy Live CD with Persistence**

> You will need:
A computer running an up to date Ubuntu Gutsy Gibbon with GParted Partition Editor installed in it. (sudo apt-get install gparted).
A Ubuntu Gutsy Gibbon .iso file or a Ubuntu Gutsy Gibbon CD 
A USB flash disk, at least 2.0 GB would be big enough. Even a 1.0 GB one should work.
A working internet connection for downloading some small files.The basic plan is this:[LIST=1]
[*]We will make an ext2 partition in the USB disk and install Super Grub Disk for USB in it.
[*]We will install Super Grub Disks's GRUB to MBR and to the Super Grub Disk partition as well.
[*]Then we'll shrink the partition as small as we can.
[*]We'll make another partition named 'ubuntu7.10', formatted FAT32 for the Ubuntu Gutsy Gibbon Live CD and copy the Live CD into it.
[*]We will install Syslinux to it.
[*]We'll shrink that as small as we can.
[*]Another partition will be made, ext3, called 'casper-rw', taking up the rest of the hard disk.[/LIST]PART 1 Super Grub Disk for USB
The reason for choosing an ext2 rather than an ext3 file system is just to save room in the USB disk. An ext2 file system is basically the same as an ext3 file system, but the ext3 file system is better for most general purposes because it features journalling. We don't need journalling for what we're going to use this file system for, 'the static files of a boot loader'. We aren't going to be writing to it once it's made. We're installing in a USB device, which is quite small and cramped, so we want to save space. The ext2 file system, without the extra overhead of the journalling feature, is what would be best for our purpose.
Filesystem overhead in an empty ext3 filesystem takes up 149 MiB, but for ext2  only about 86 MiB is taken up by the file system's metadata blocks.

1,1 We begin by using GParted to delete whatever file systems were already in the USB disk, (make sure you save any data out of it first though!), and we create a partition with an ext2 file system in it, using the whole disk.
So plug in your USB flash memory disk to your computer running Ubuntu Gutsy Gibbon and if it automatically mounts, unmount it, (by right-clicking the icon and clicking 'unmount volume', and open GParted Partition Editor. Delete what's there and make your new partition with the ext2 file system in it.
While you are using GParted, take note of your hard disks and partitions designations for your own particular computer. Write them down on a piece of paper and draw yourself a sketch if necessary so you'll be sure you know which hard disk is which and what file system is called /dev/hda1 and which is /dev/sda2 and so on.  You may need to replace '/dev/**s**da**x**' throughout this how-to, with the file systems designations that suit your own unique computer.
Close GParted.

1.2 Open a terminal and make a label for the new file system,
```
e2label /dev/sdb1 SGD
``` Where: '/dev/sdb1 is your new ext2 file system in your USB flash memory stick, if yours is /dev/(something else), then please replace it with the appropriate device designation throughout this entire how-to.   
1.3 We can either go on the internet and download a copy of the latest [Super Grub Disk for USB]("http://sgd.benjamin-butschko.de/?section=download#usb"), or use wget to get it for us. 
You can do it your way, but here I'll show you the wget comand for it in case anyone wants to do it the easiest way, (just copy and paste),
```
wget http://sgd.benjamin-butschko.de/download/binaries/sgd/usb/sgd_0.9588_for_usb.tar.gz
```1.4 Now we're going to extract it,
```
tar xvzf sgd_0.9588_for_usb.tar.gz
```Another way to do the same thing in GUI is to just right-click on the file and click 'extract here', but we're using terminal commands, it's good practice.

1.5 Your USB disk is probably still unmounted since we just made and labelled the new file system in it. To mount it again, just unplug is and plug it back in again. Most USB devices will be automatically re-mounted.
If it doesn't, you might need to mount it  yourself, see  [File Systems and Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm").
 
Copy the /boot directory and all of it's contents into the new Super Grub for USB disk.
```
sudo cp -R sgd_0.9588_for_usb/boot /media/SGD
```1.6 Edit the Super Grub Disk's /boot/grub/menu.lst file,
```
sudo gedit /media/SGD/boot/grub/menu.lst 
```BEFORE:
```
# You can edit this file to add your own distribution
# You can choose default to 0 to select first entry
# which it is usually the entry for the default distro
#
#
# You can also set timeout to something as 10
#
# This is the shortcut to call Super Grub Disk (commented)
#title Super Grub Disk
## The two commands: setgrubdevice and usbshift are needed
## so that SGD works well.
#usbshift
#configfile $(grub_device)/boot/sgd/menu.lst
#
# Just after default and timeout statements you have to put
# setgrubdevice so that grub device is correctly set.




default 2
timeout 2
setgrubdevice # This is compulsory
#gfxmenu /boot/grub/message
foreground ffffff
background 0c00ff
color white/brown yellow/cyan


title Inicio normal / Normal Boot 
kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
initrd $(grub_device)/initramfs

title Soporte de accesibilidad / Accesibility Support -->
configfile $(grub_device)/boot/grub/menu2.lst

title Super Grub Disk
# The two commands: setgrubdevice and usbshift are needed
# so that SGD works well.
usbshift
configfile $(grub_device)/boot/sgd/menu.lst

title Normal boot. Kernel is aware of Boot device
kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash boot_device=$(grub_device)
initrd $(grub_device)/initramfs

title Normal boot. Selecting kernel and initrd files depending on grub_device
kernel $(grub_device)/vmlinuz_$(grub_device_string) lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
initrd $(grub_device)/initramfs_$(grub_device_string)

title Selecthd test
configfile $(grub_device)/boot/grub/choose/selecthd.lst

title findp test
configfile $(grub_device)/boot/grub/choose/selectpart.lst
title set SGD variables and boot SGD

configfile $(grub_device)/boot/sgd/menu.lst
```AFTER:
```
# You can edit this file to add your own distribution
# You can choose default to 0 to select first entry
# which it is usually the entry for the default distro
#
#
# You can also set timeout to something as 10
#
# This is the shortcut to call Super Grub Disk (commented)
#title Super Grub Disk
## The two commands: setgrubdevice and usbshift are needed
## so that SGD works well.
#usbshift
#configfile $(grub_device)/boot/sgd/menu.lst
#
# Just after default and timeout statements you have to put
# setgrubdevice so that grub device is correctly set.




default [COLOR=Red]**0**[/COLOR]
[COLOR=Red]** #**[/COLOR] timeout 2
[COLOR=Red][B] # The two commands: setgrubdevice and usbshift are needed
# so that SGD works well.
usbshift[/B][/COLOR]
setgrubdevice # This is compulsory
#gfxmenu /boot/grub/message
foreground ffffff
background 0c00ff
color white/brown yellow/cyan

[COLOR=Red][B] title Ubuntu Gutsy Gibbon Live CD
root (hd1,1)
chainloader +1[/B][/COLOR]

[COLOR=Red][B] title Super Grub Disk
configfile $(grub_device)/boot/sgd/menu.lst[/B][/COLOR]

title Inicio normal / Normal Boot 
kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
initrd $(grub_device)/initramfs

title Soporte de accesibilidad / Accesibility Support -->
configfile $(grub_device)/boot/grub/menu2.lst

title Normal boot. Kernel is aware of Boot device
kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash boot_device=$(grub_device)
initrd $(grub_device)/initramfs

title Normal boot. Selecting kernel and initrd files depending on grub_device
kernel $(grub_device)/vmlinuz_$(grub_device_string) lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
initrd $(grub_device)/initramfs_$(grub_device_string)

title Selecthd test
configfile $(grub_device)/boot/grub/choose/selecthd.lst

title findp test
configfile $(grub_device)/boot/grub/choose/selectpart.lst
title set SGD variables and boot SGD

configfile $(grub_device)/boot/sgd/menu.lst
```You can see what I changed highlighted in red.
I first I set the operating system entry to be booted by default from 2 to 0, so the first entry will be booted automatically, which is going to be Ubuntu7.10
Then I disabled the timer by 'commenting out' that line with a 'hash' mark.
I typed in an entry to boot the second partition by chainloadingit by the boot sector. Later, we'll install syslinux in partition 2's boot sector.
I cut the entire Super Grub Disk entry from fourth and moved it up to second place and pasted it there.

If you're in a hurry, just copy mine from this web page and then go to your own Super Grub Disk's /boot/grub/menu.lst, click 'Edit'-->'Select All'-->'Delete', and the 'Edit'-->'Paste', to replace what was there before with the new copy. Don't forget to click 'Save' before you close the file now.

1.7 The next thing we need to do is install Super Grub Disk's GRUB to MBR in the USB disk, and in the SGD partition as well just to make sure.
```
sudo grub
```This opens a GRUB shell

We're going to make use of GRUB's 'tab completion' feature, to help us install GRUB to the right locations.
So I type 'root (hd ...and press my tab key.
```
grub> root (hd 
```I press tab to see what's here. NOTE: If you're copying and pasting these commands, you don't copy the 'grub>' part for these next few commands, that's just to show you we have a GRUB shell, actually, these next few commands are better off being done manually, because we're going to be using GRUB interactively to make sure we install GRUB to the right boot sector and MBR.

Grub replies,
```
grub> root (hd
Possible disks are: hd0 hd1
```There are two disks here, how will I know which hard disk is my USB disk and which one is my internal hard disk?
I know that the USB disk only has one partition in it, but my internal hard disk has several partitions in it.

I'll try a test by typing '(hd1, ' ...and pressing my tab key to see what GRUB can see in (hd0)
```
grub> root (hd0, 
Possible partitions are:
Partition num: 0, Filesystem type is fat, partition type 0x16
Partition num: 1, Filesystem type is fat, partition type 0xc
Partition num: 2, Filesystem type is ext2fs, partition type 0x83
Partition num: 4, Filesystem type is unknown, partition type 0x82
Partition num: 5, Filesystem type is ext2fs, partition type 0x16
Partition num: 6, Filesystem type is ext2fs, partition type 0x16
```Nope, I don't want to install Super Grub Disk's GRUB to MBR in (hd0). I'm sure now that (hd0) is my internal hard disk.

```
grub> root (hd1, 


```I'll try backspacing and type a '1' there to replace the '0', and press 'tab' again.
```
grub> root (hd1,0)

```This time it auto completes. It doesn't give me a list of partitions because there's no choice, there's only one partition I can select. Now I'm really certain I know what I'm doing! 
(The famous last words --only joking!)
```
grub> setup (hd1,0)
```That installs Super Grub Disk's GRUB to the first partition (boot sector) of the USB disk (hd1).
```
grub> setup (hd1)
```This installs Super Grub Disk's GRUB to the MBR of (hd1), the USb disk. We don't really need GRUB in both places, it's just overkill. It won't hurt anything though.
```
grub> quit
```Yay! We're finished setting up the Super Grub Disk Partition! Now we have Super Grub Disk for USB installed, and if we want, we can try it out and boot operating systems in any computer with it already.

1.8
One more thing we can do anytime is open GParted again, unmount the SGD partition and shrink it (resize to a smaller size), as small as it will go. We don't need any spare room in the file system at all, we aren't going to be adding any more files in it. Even if we do need to edit the /boot/grub/menu.lst again, it will only be a few lines of typing, that won't make any difference. Shrink it to as small as GParted can shrink it.
Mine shrank right down to 86.26 MiB, so obviously Super Grub Disk doesn't take up much room at all. 
Now maybe you can see the sense in using ext2 instead of ext3, wouldn't it seem silly to use double the amount of disk space for a fancier file system when Super Grub Disk itself takes up so little room? And we're probably not going to make any more changes to teh file system anyway, so what's the use of having a journalling file system in this instance?

===================END OF PART ONE===========================

---

### Post by Herman on 2007-12-27
===================BEGIN PART TWO============================

2.0 
Using GParted, we need to make a new partition taking up the free space in the USB flash drive. 
Make it formatted with a fat32 file system, because later on we're going to use the syslinux boot loader, and the syslinux boot loader will only work in a FAT32 file system.
Close GParted and if the file system had been automatically mounted, unmount it again. (by right-clicking the icon fo rit and clicking 'Unmount Volume'.

Open a terminal again and reformat the partition with a new fat32 file system again and name it 'ubuntu710' with this command,  (just to give the file system a volume label),
```
mkdosfs -n ubuntu710 /dev/sdb2
```Where: sdb2 is the second partition in your USB drive.
CAUTION: If you use this command again in the future, always remember only to use it on an empty file system one that has all the files backed up first, because this command is not safe like it's ext2 counterpart, this one re-formats the file system, so you will lose any data in it.
CAUTION: Make sure you aim this at the right partition, don't mis-type the command and wipe out a partition in the wrong hard drive!!!
This mkdosfs command is the dangerous one, the e2label command we used earlier is actually quite safe and harmless.

Unplug the USB flash drive and plug it in again so the new file system will be mounted, ready to copy some files into.

2.1
I presume you have your ubuntu-7.10-desktop-i386.iso file  in your /home/username directory and not inside some other directory. If you have it  somewhere else, you should either move it to your /home/username directory or be prepared to type your own file path into the commands I'm going to use or your commands won't work.

We are going to mount our .iso files so we can copy the files from the .iso files directly to the USB disk's ubuntu710 partition. An easier way to do things would be to copy them off a CD that's already made, but that would be too simple, you don't need me to show you how to do that. If you can mount an .iso file, it's a pretty good shortcut sometimes, because obviously, you don't need to go to the work of burning the .iso to a CD every time. 
Here's the command to make a mount point,
```
sudo mkdir /media/ubuntu_iso
```Here's the command to mount the .iso
```
sudo mount -o loop -t iso9660 ubuntu-7.10-desktop-i386.iso /media/ubuntu_iso
```Your USB partition should be mounted automatically already as /media/ubuntu710, because that's the name we gave the file system.
2.2
We'll copy the files from the mounted .iso file into the ubuntu710 partition in the USB disk,
```
cd /media/ubuntu_iso
``````
sudo cp -rf casper disctree dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines ubuntu.ico casper/vmlinuz casper/initrd.gz /media/ubuntu710/
```Expect this to take a few minutes. Your USB flash disk's light will be winking and blinking for a little while.
Ignore any error messages about 'cannot create symbolic link'.```
cd
```2.3
Now we need to install the boot loader called syslinux in the boot sector of the USB drive. 

Just before we do, we'll run apt-get update so our operating system will be aware of the most up to date packages,```
sudo apt-get update
```Now we'll use apt to install the program for syslinux. This program is called mtools and when it's installed we can type 'man mtools' for more information about what it can do.```
sudo apt-get install syslinux mtools
``````
syslinux -sf /dev/sdb2
``` That installed syslinux to the boot sector of the Ubuntu partition.
2.4 We need to rename the isolinux file 'syslinux' instead.
```
sudo cp /media/ubuntu710/isolinux.cfg /media/ubuntu710/syslinux.cfg
```Now try rebooting and boot Super Grub for USB, and try booting into Ubuntu this time, it should boot up okay now. You won't have persistence, but it should work as if it was a live CD, only faster.

===================END OF PART TWO===========================

---

### Post by Herman on 2007-12-27
===================BEGIN PART THREE============================

Now for the persistence part of things....
Boot up your regular hard disk installed Ubuntu operating system again, and with your USB flash drive plugged in, carry out the following steps.
3.0
```
gksudo gedit /media/ubuntu710/syslinux.cfg
```We're supposed to use 'gksudo' in Ubuntu (Gnome), instead of plain 'sudo' for opening graphical programs like gedit, use 'ksudo' if your running KDE. I learned that from this article by aysiu, [Graphical sudo]("http://www.psychocats.net/ubuntu/graphicalsudo").

_Editing syslinux.cfg_
We need to change the file paths by deleting all 11 instances of words '/casper,  5 occurrences of the word '/cdrom , and one instance of the word '/install from the syslinuc.cfg file.

:idea:  I will tell you a neat trick you can use with the 'less' command to help you find the words you need to delete for sure. Switch to another workspace and open another terminal up. Type this command,
```
 less /media/ubuntu710/syslinux.cfg
```Enter the command 'less /media/ubuntu710/syslinux.cfg', and when the file is open in your terminal window, without closing the window, type ' //casper', and press 'Enter'. Press your 'page up' key too, to go to the top of the file.
You should see all the instances of the word '/casper' highlighted for you!  :)
 Do the same with '//cdrom', you might need to hit your 'page up' key. Also do '//install', (use your 'page up' key once more if you can't see the whole page properly.
Unfortunately, I haven't discovered yet how to do any editing with the 'less' command yet. (I'm only joking, but wouldn't it be neat if we could? If anyone knows how to do something like that please let me know, I'll bet there is a program that can do that). :)
We can edit the file with gedit, back in the other workspace, and we have to open and close 'less' to see the changes.
BEFORE:
```
DEFAULT [COLOR=Red]**/casper**[/COLOR]/vmlinuz
GFXBOOT bootlogo
GFXBOOT-BACKGROUND 0xB6875A
APPEND  file=[COLOR=Red]**/cdrom**[/COLOR]/preseed/ubuntu.seed boot=casper initrd=[COLOR=Red]**/casper**[/COLOR]/initrd.gz quiet splash --
LABEL live
  menu label ^Start or install Ubuntu
  kernel [COLOR=Red]**/casper**[/COLOR]/vmlinuz
  append  file=[COLOR=Red]**/cdrom**[/COLOR]/preseed/ubuntu.seed boot=casper initrd=[COLOR=Red]**/casper**[/COLOR]/initrd.gz quiet splash --
LABEL xforcevesa
  menu label Start Ubuntu in safe ^graphics mode
  kernel [COLOR=Red]**/casper**[/COLOR]/vmlinuz
  append  file=[COLOR=Red]**/cdrom**[/COLOR]/preseed/ubuntu.seed boot=casper xforcevesa initrd=[COLOR=Red]**/casper**[/COLOR]/initrd.gz quiet splash --
LABEL driverupdates
  menu label Install with driver ^update CD
  kernel [COLOR=Red]**/casper**[/COLOR]/vmlinuz
  append  file=[COLOR=Red]**/cdrom**[/COLOR]/preseed/ubuntu.seed boot=casper debian-installer/driver-update=true initrd=[COLOR=Red]**/casper**[/COLOR]/initrd.gz quiet splash --
LABEL oem
  menu label ^OEM install (for manufacturers)
  kernel[COLOR=Red]** /casper**[/COLOR]/vmlinuz
  append  file=[COLOR=Red]**/cdrom**[/COLOR]/preseed/ubuntu.seed boot=casper oem-config/enable=true initrd=[COLOR=Red]**/casper**[/COLOR]/initrd.gz quiet splash --
LABEL check
  menu label ^Check CD for defects
  kernel [COLOR=Red]**/casper**[/COLOR]/vmlinuz
  append  boot=casper integrity-check initrd=[COLOR=Red]**/casper**[/COLOR]/initrd.gz quiet splash --
LABEL memtest
  menu label ^Memory test
  kernel [COLOR=Red]**/install**[/COLOR]/mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt
```We need to add a new boot entry titled "Start Ubuntu in USB Persistent Mode" or something like that, with the right commands in the other lines to make it boot in persistent mode.
AFTER:
```
DEFAULT /vmlinuz
GFXBOOT bootlogo
GFXBOOT-BACKGROUND 0xB6875A
APPEND  file=/preseed/ubuntu.seed boot=casper initrd=/initrd.gz quiet splash --
[COLOR=Sienna][B]LABEL persistent
  menu label ^Start My Ubuntu USB in Persistent Mode!
  kernel /vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper persistent initrd=/initrd.gz quiet splash --[/B][/COLOR]
LABEL live
  menu label ^Start or install Ubuntu
  kernel /vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper initrd=/initrd.gz quiet splash --
LABEL xforcevesa
  menu label Start Ubuntu in safe ^graphics mode
  kernel /vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper xforcevesa initrd=/initrd.gz quiet splash --
LABEL driverupdates
  menu label Install with driver ^update CD
  kernel /vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper debian-installer/driver-update=true initrd=/initrd.gz quiet splash --
LABEL oem
  menu label ^OEM install (for manufacturers)
  kernel /vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper oem-config/enable=true initrd=/initrd.gz quiet splash --
LABEL check
  menu label ^Check CD for defects
  kernel /vmlinuz
  append  boot=casper integrity-check initrd=/initrd.gz quiet splash --
LABEL memtest
  menu label ^Memory test
  kernel /mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt  
```If you're lazy or in a hurry, just copy all the text from my finished one here, and go to yours and go 'Edit'-->'Select All'-->'Edit'-->'Delete'-->'Edit'-->'Paste'-->'Save'. And close the file.

Now that's finished, unmount the volume and shrink that partition as small as you can with GParted.
We're not going to be adding any more files to this partition.
Even if we end up needing to edit a file, the difference will be negligible.
Mine ended up to be only 699 MiB.

Make another new partition taking up the rest of the hard disk. This time we'll be writing to it, so we'll make it an ext3 file system.
Name this file system 'casper-rw'.
```
e2label /dev/sdb3 casper-rw
```NOTE: It isn't a command with the -rw option, so don't type it that way. There is no whitespace (gap) between the r and the - (dash), it's all one word.
I started with a 4.0 GB (3.84 GiB) flash memory stick and I have 3.07 GiB in the casper-rw partition.
The Super Grub Disk and the Ubuntu Live CD partitions are only taking up 784.40 MiB of the Flash Memory.

Now reboot and boot Super Grub Disk for USB and from there into Ubuntu in the flash memory stick and make some obvious changes.
Then reboot again to test whether it's persistent. It should be persistent from now on. :)

You can update your system with apt-get update and apt-get upgrade if you have enough spare room in your USB drive. 
I installed [Partimage]("http://www.partimage.org/Main_Page"), [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"), [Smartmontools]("http://smartmontools.sourceforge.net/") and [ssh]("http://www.openssh.com/") in mine already using apt-get.
There are plenty more great applications available for Ubuntu and they're all easy to install.
I think I can do everything I will ever need to do with my USB stick with Ubuntu.


============================THE FINISH LINE====================================

---

### Post by Tekno_Cowboy on 2008-01-04
I really like the way you changed the first part, using Super Grub Disk. It's much quicker than the syslinux method, and works (in effect) the same as the syslinux/isolinux that the cd uses, and has less issues when used with some setups with certain hard disk setups than the syslinux solution. 

I think extlinux might be a better solution for the second part, though I havn't had the time to find the documentation on it to see if I'm right or not. If you find out, please share :)

:)Thanks For This Great How-To:)
It was very educational.

---

### Post by gary4gar on 2008-01-04
Thanks a Ton!
i was looking for something like this, but is there any way by which do not alter the partions, and still boot from USB, as making a ext partion on flash drive, will ruin its main purpose sharing of data because most PC can't read ext partions by default

---

### Post by Herman on 2008-01-05
Tekno_Cowboy,
Thanks, I'm happy if you like it and thanks for telling me about extlinux too, I'm looking into it. :)

gary4gar
:confused: What kind of operating system are you using? All my USB memory sticks are ext3 and all my computers read them just fine. 
Well, if you want you can use the memory stick to install Ubuntu in all those computers you find that don't have it and then you will be able to use your ext3 memory stick in any computer! :guitar:

Don't do that really, I'm only joking. :)

---

### Post by Herman on 2008-01-05
gary4gar,
Actually, it doesn't really matter, because when you boot Ubuntu in the USB in any computer, you can use Ubuntu to mount the file systems inside the computer and read and write data in or out of the USB to any file system you like.
Gutsy Gibbon has NTFS read and write support.
Ubuntu is the master operating system and other operating systems are under your control when you are using Ubuntu.

Regards, Herman :)

---

### Post by Tekno_Cowboy on 2008-01-05
> **gary4gar said:**
> Thanks a Ton!
i was looking for something like this, but is there any way by which do not alter the partions, and still boot from USB, as making a ext partion on flash drive, will ruin its main purpose sharing of data because most PC can't read ext partions by default

I believe you are talking about using the extra space on a Windows PC, or to transfer files between a Linux PC and a Windows PC. Windows does not play well with ext filesystems, and tends to mount only the 1st partition on the drive. To make it work, you can simply put a FAT32 or FAT 16 filesystem at the beginning of the drive, and partion the rest out for your Linux USB. On a 4GB Survivor, I made a 2.5 GB FAT32 partition at the beginning, an ext2 partition for my live cd files in the middle, and a casper-rw partition with all the remaining space at the end. Windows sees the FAT partition, and so does Linux. Hope this answers your question.

---

### Post by Tekno_Cowboy on 2008-01-05
Kubuntu and Ubuntu work fine with the first method, but I can't seem to get Xubuntu to be persistent. If you come across why this is, please let me know.

Thank You

Edit: Solved-I was using a 7.04 CD, which is known to have problems with persistence. I sure feel sheepish.

---

### Post by Tekno_Cowboy on 2008-01-07
I think my post got moved or deleted, because I can't seem to find it. I was hoping to get some help with a probem with the persistent part with the first method. I can boot to persistent mode and change things once. When I try to boot up again, I get an error saying something about .ICEauthority after the KDE splash, and it goes to the login screen. I can still boot to a non-persistent boot using the same drive, and if I delete all the files on the casper-rw partition I can boot again, but of course all of my changes are gone. I've set this up on a few drives, and for some reason, only some of them seem to be doing this, and I can't figure out why. Any help would be greatly appreciated.

Edit: problem solved, somehow the permissions get changed in the /home directory, and no longer allow you to use them. Either changing these permissions, or setting up a new user on the first boot should quickly fix this. Many thanks go to davbslim.

---

### Post by MQMike on 2008-01-09
I have a question about “persistence,” in the context of making a bootable LIVE K/Ubuntu USB flash drive.

If we make the stick persistent, an example of what we want would be to store various * static * data/configurations.  Example:  The background image on the Desktop (set once and for all);  the selection of icons on the kicker panel; configuration/preference settings for the resident web browser, the word processor OOo Writer, and so on.  These items are set once and for all and do not change—they are only “read.”

An example of what, I would think, we do NOT want would be for the LIVE K/Ubuntu (on flash drive) to be constantly writing to the flash drive such things as variable files, tmp files (both /tmp and /var/tmp), swap, and such things.  There is the issue of “wearing out” the stick with re-write cycles.

In fact, one of the references raises the question (“Outstanding Questions”):
“Every single disk write goes to the USB stick, which GNOME loves to do all the time.”
[https://help.ubuntu.com/community/LiveCDPersistence#head-4be8ad9301322add5fa96636940e31f46cae5951](https://help.ubuntu.com/community/LiveCDPersistence#head-4be8ad9301322add5fa96636940e31f46cae5951)

We know that Puppy Linux (on LIVE USB flash drive) is specially designed to “optimize” this performance criterion (eliminate disk writes to the USB flash drive), whereas, I’ve read that Knoppix on a USB stick is a bad idea for this reason (“wear-out" performance).

Do we know where the current “persistent” fix stands with respect to the wear-out criterion on USB flash drives?  Is this an issue?  

==> What *exactly* gets written to the persistent LIVE stick?

---

### Post by Herman on 2008-01-09
:) Hi MQMike, 
You are asking some very good questions there and all I can really say is, "I'm not sure".

The original how-to was written mainly to provide a way that people can install Ubuntu to hard disk in another computer if the other computer doesn't have a working CD-ROM drive.
Ubuntu in a USB flash memory stick works a lot quicker than when it's running from a Live CD too, so it's great for demo purposes.

I would certainly imagine even if it did wear out, if the SGD + Ubuntu flash memory stick was used for installing Ubuntu in people's computers, it would have performed enough hard disk installations to have well paid for the cost of a new memory stick.

The 'Persistence' idea is a secondary but also nice, feature. With Super Grub Disc in it, and your choice of software that's installable from the Ubuntu repositories, it can also double as an emergency disk. 
I have Partimage, TestDisk, Smartmontools and a few other things like that in mine.
I'm not planning on using mine for all day, every day use, I think that's what (internal) hard disks are good for. 
My own SGD + Ubuntu flash memory stick will be here most of the time sitting on the shelf or in a drawer, ready for when the phone rings and one of my freinds has a computer emergency of some kind and and they need me to come over and sort it out for them. It's a lot easier to carry than my laptop.

My brother's wife had her laptop stolen from her a while back when she was travelling. She had it with her other luggage  when she visited some people she used to know a long time ago who she thought were still her friends.
After a cup of tea or coffee when she was ready to leave, her laptop was gone. The people in the house claimed she didn't have a laptop with her whe she arrived, she must have forgotten it at the airport or left it in the taxi or something. Whatever happened to it, we'll never know, she never saw her new laptop again
This story illustrates another reason why someone might want Ubuntu in a memory stick. I imagine it would probably last at least long enough for a journey of some kind, instead of taking a laptop. In that example, the price of replacing the laptop would have paid for lots of new memory sticks. That's another example of the memory stick being for short term use, not as a permanent all day every day operating system.

Tekno_Cowboy and I discussed this very same issue, (if a flash memory disk will last very long when used that way),  briefly, through private messages separate from but related to this thread. Tekno_Cowboy says there can be a difference in the quality of USB flash memory too.

I would hate to be blamed for anyone losing any data due to a failure of a flash memory stick. I really don't know how long these things last or even if it's true that they can wear out. The only way to find out might be to start a poll and ask people who have had persistent Linux flash memory installations how old theirs is and how much they use it and if they've ever had one fail and so on.

Another point is, hard disks can fail too, and the best thing to do is make sure we have our data backed up on separate media at all times.

MQMike, do you have any ideas where to search for any information about the durability of flash memory under this kind of use?

Regards, Herman  :)

EDIT: Here's one I found already, Wikipedia link:  [3 Limitations]("http://en.wikipedia.org/wiki/Flash_memory#Limitations")
 


---

### Post by MQMike on 2008-01-10
Hi Herman  :)

My thoughts are about the same as what you've expressed here on this subject.  It seems that very little is known about it in a practical sense.  On the other hand, we do not see the forums full of people screaming that “My USB stick burned out on me!”

I view these things as rescue/emergency/convenience devices when loaded with OSs.   I've got a 512 MB with SGD, my own GRUB/menu.lst, GParted, Puppy, and data, and one 2 GB with both K/ & Ubuntu LIVE on it (using GRUB, chainloading to Syslinux).  Motivated by a how-to by IntutuiveNipple, I did my version (*without persistence*) at Build a LIVE Kubuntu Flash Drive, How-To
[http://kubuntuforums.net/forums/index.php?topic=3089474.new#new](http://kubuntuforums.net/forums/index.php?topic=3089474.new#new)
(where I referenced the one by I-N, too; I did MEPIS there and it was a bit different--uses all GRUB, no Syslinux).

I've been studying persistence and you've got really good references on it here, Herman.  Your how-to is very nicely done, and I think I can use it to make trivial modifications to include persistence in mine.

In doing Puppy, I came across these two references (9-15-07):
UFD life cycle:
[http://www.getusb.info/what-is-the-life-cycle-of-a-usb-flash-drive](http://www.getusb.info/what-is-the-life-cycle-of-a-usb-flash-drive)

[http://puppylinux.org/wikka/FlashDetail](http://puppylinux.org/wikka/FlashDetail)
(Puppy:   Special solutions to minimize UFD re-write cycles.  Puppy is supposed to be one of the best for minimizing wear-out write cycles.  It runs 100% in RAM after loading--see the link for more.)

Another interesting question is how to load an updated version of K/Ubuntu on the stick?  That is, when you download a K/Ubuntu iso, then install it to hard drive, as we all know, it takes 100-150MB of updates to bring it up current.  But the iso we copy to the stick doesn't have these updates, so the LIVE version is running without any updates.  I have loaded Kubuntu on a 4 GB stick as a full installation (not LIVE) just like doing it on a hard drive, but then, what's the point of that?  It would be interesting to test how long it would run without wearing out the stick.

If I run across any better “definitive” references, I'll pass them along.  What we need is to use K/Ubuntu LIVE persistent on a stick full time and see how long it will go under continuous use!
You know, another “persistent”-like solution, an obvious one, is to use a regular LIVE K/Ubuntu on a stick and save your data/configuration to a second stick or to a second partition on the same stick.  That would work for things like personal data, Thunderbird email (just copy off the whole profile folder then import it as needed), Firefox bookmarks, and such.

Thanks again for your excellent How-To!  :)

---

### Post by Herman on 2008-01-10
> Another interesting question is how to load an updated version of K/Ubuntu on the stick? That is, when you download a K/Ubuntu iso, then install it to hard drive, as we all know, it takes 100-150MB of updates to bring it up current. But the iso we copy to the stick doesn't have these updates, so the LIVE version is running without any updates. I edited the /etc/apt/sources.list file and ran apt-get update and then added the software I wanted. Just like a regular hard disk install. The ubuntu710 (Live CD) partition never changes, but the updates go to the casper-rw partition instead.
Interestingly, I tried copying all the directories out of the casper-rw partition and booting the memory stick again and it re-generates the files, but you have to re-do all your settings and any updates. Then if you overwrite those files with your original ones, it makes it back to the way you had it the first time. 

An interesting thing I noticed was when repeating the installation to test and try to perfect the how-to, when I  created the partitions in the same place again in the blank disc, my old file system would pop back up, alreadt named 'casper-rw'. I don't know why.

>  Thanks again for your excellent How-To!Sure! No problems there, MQMike, actually, I was looking at your how-to in Kubuntu Forums about installing GRUB USB stick. adrian15 likes the way you do it with the device command, he doesn't approve of my geometry command method. It works for me. I'm looking into it.
 
Regards, Herman :)

---

### Post by MQMike on 2008-01-10
I have noticed this "geometry" issue popping up now and then, here and there!

Actually, the tip you gave at your web site about using geometry to find out what is where on the drives, that tip is one of the best tools I know of.  If you combine geometry with root-setup-quit, and toss in configfile, you can rescue just about 80% of booting problems (at least temporarily, enough to get booted into an OS to make permanent repairs).

Thanks for the info on doing the updates, too.  When you say that you "edited the fstab file,"  what are you referring to?  (It's early here and maybe my brain isn't yet in gear.  :)  )

Thanks again.

---

### Post by Herman on 2008-01-10
> When you say that you "edited the fstab file,"  what are you referring to?Sorry, my bad, I meant to type "/etc/apt/sources.list" file. I have corrected my post amd I will do 20 pushups. 
Regards, Herman :)

---

### Post by MQMike on 2008-01-10
About flash drive re-write/wear-out . . .

Well, I've just begun to look at this (using Kubuntu LIVE persistent), and  it sure seems that the casper-rw partition is quite actively being written to!
.trash, cdrom, etc, home, lib, media, tmp, usr, var, root, sbin.

It is tracking the usual logs, recent docs, cookies, etc. -- user activity.
You can look at it in your regular K/Ubuntu OS.
With just a few settings, bookmarks, Firefox download, etc., I've already got 147 MB on the casper-rw partition.
I imported bookmarks to the stick's Firefox from another flash drive, which worked well, and saved data to a second flash drive from the Kubuntu Live persistent flash drive.
Everything seems to work very well, but as I say, it looks like the casper-rw partition is quite active.

---

### Post by iispyderii on 2008-01-12
hi,

i am having a little problem on my pendrivelinux. i have searched the forums and done some researching but im not quite sure what to do.

i did everything perscribed in the pendrivelinux.com thing and when i go to boot the linux in a dell windows xp... it says 'operating system missing'? but then i go to run the same USB drive on my desktop with Ubuntu 7.10 installed already (with GRUB). it boots right up and i can start live. so what do i need to do so i can put this USB drive into any windows computer so that it'll boot right up and load.

herman, 

i was reading the long posts back and forth with you and tech09 and the problems he had. but that kind of just confused me a little bit. it sayed that he just got it right one time he went through the pendrivelinux.com. 

so do i need to install the super grub thing to my usb drive and instructed in this first post of the thread? 
and if im installing the ubuntu pendrive and grub.
i had some trouble mounting the iso (where do i put it to mount it first?) and i had trouble with the grub installation on the usb.

please lend a helping hand!

iispyderii

---

### Post by MQMike on 2008-01-12
iispyderii,
I am new to this thread and so will let Herman return for some of your questions.  However, the very first things to check are:
1  Did you set your Dell to "Boot from USB" and include the USB stick in the list of drives recognized by your Dell BIOS?  You have to enter your DELL BIOS to do all this--see your motherboard instructions.
2   Make sure you set the boot flag on your USB stick partition where your Ubuntu is installed.  You can do that with GParted Live CD, highlight that partition, click the tab at the top Partition, Manage Flags, boot--click in the box.

---

### Post by Herman on 2008-01-12
Hello iispyderii,

I agree with the two point MQMike just made, those were the first two things I thought of too. My bet's on the boot flag, it does say in Pendrivelinux to set one, but ti would be easy to overlook and skip a step.
>  so do i need to install the super grub thing to my usb drive and instructed in this first post of the thread? 
You don't have to, Super Grub Disk is extremely useful, but it's not compulsory to have Super Grub Disk just to boot a USB. If you want I can help you install Super Grub disk to your Pendrivelinux USB Ubuntu.
>  and if im installing the ubuntu pendrive and grub.
i had some trouble mounting the iso (where do i put it to mount it first?) and i had trouble with the grub installation on the usb.You probably need to make your own mount point, the usual place to make a mount point in Ubuntu is in our /media directory, but you can make it anywhere. Here is a link that explains all about mounting stuff, [File Systems and Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm"), I hope that page is easy to understand, if it isn't please complain to me and I'll try to fix it.
Then, just copy the /boot directory of Super Grub Disk for USB into your ubuntu710 partition.
Finally, you'll probably want to install Super Grub Disk's GRUB to the USB disk's MBR. That's easy, the main thing is to make sure it does go to your USB's MBR and not to just any MBR in your computer.
There are two ways to do that.

FIRST WAY
One way is when you USB drive is unplugged, to open up a terminal and type 'mount',
```
mount
```Then, after you plug your USB in again, if it automatically mounts for you, type the 'mount' command again.
```
mount
```Compare the output from the first mount command with that from the second mount command. 
You should see if the USB is called something like '/dev/sda', or '/dev/sdc', or whatever by Linux.
Only trouble is, in my computer the ubuntu710 partition never is able to be automatically mounted for some reason. If it doesn't automount, just use 'sudo fdisk -lu' to see what your USB looks like in Linux notation (/dev/(something))
```
sudo fdisk -lu
```Now, you get a GRUB shell, by typing 'sudo grub' in Ubuntu.
```
sudo grub
```You use GRUB's device command, to force GRUB to register your USB drive as a drive number in GRUB notation, like (hd(drive number). [Quick Guide to GRUB's Numbering System]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System")
```
device (hd2) /dev/sdc
```Type 'root' (hd3)
```
root (hd2)
```Type 'setup' (hd(drive number)
```
setup (hd2)
```Type 'quit'
```
quit
```SECOND WAY
The other way is faster and simpler for me, since the only computer I have working at the moment that can boot a USB will never automatically mount the ubuntu710 partition.
Get a GRUB shell.
```
sudo grub 
```Test to remind you which hard disks and partitions in your computer contain GRUB files,
```
grub> find /boot/grub/stage1
```You should get some feedback like: (hd0,1) (hd1,0) , but you're still not sure which is the USB and which is in your hard disk. Probably (hd1) is the USB.
Test with GRUB's 'geometry' command to find out if (hd1) is really your USB disk.
```
 grub> geometry (hd1)
```You should get some feedback similar to the following,
drive 0x81: C/H/S = 250/255/63, The number of sectors = 4030464, /dev/sdb
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83 
That indicates that we guessed correctly, (hd1) is the USB.

Tell Grub which partition it's supposed to be working in, (this depends on the output from the preceding commands, and may vary between computers, please watch it and alter the command to suit your own particular machine.```
grub> root (hd1,0) 
```Install GRUB to MBR in the USB drive,```
grub> setup (hd1) 
```Close the GRUB shell
```
grub> quit
```I think that way is the best, or at least it seems that way to me, but not everyone's computer is the same, so use whichever way works best for you.

Regards, Herman  :)

---

### Post by ibbers on 2008-01-13
Thanks for the fantastic how-to, first of all!

Using the instructions i've gotten gutsy live running on my cruzer stick...

however, i need some advice on the particular version i'm trying to get working on my stick.

I have a fit-pc at home, and after an update that broke it (compounded by me not reading up on the 'break' first before trying to fix it), i've been trying to reinstall *buntu on it.  Xubuntu goes on fine, but i'd rather ubuntu.

Because of its hardware, I can only use the altenative install cd when installing  (xubuntu live doesn't work, and ubuntu live definitely doesn't).  Installing from a USB CD drive appears to be very flaky, so i'm hoping the USB-disk installation you've detailed (using the Alternate ISO instead) should do the trick.

So my question are (and please excuse my ignorance!):

* How do I go about editing the kernel (as you've mentioned below - "add 'vesa vga=771' as kernel parameters")?  Where/how?

* I assume I'll need to edit the grub menu as well, once i've got the kernel thing fixed - where/how would i do that?

Once again, excuse my ignorance - if i can overcome these two hurdles i can get my fit-pc back up and running. :D

thank you in advance mate!

Ibbers


[Snipped for quoting]:

[*]You'll need a copy of SGD for USB, at the time of typing, the latest is [super_grub_disk_english_usb_0.9673.tar.bz2]("http://forjamari.linex.org/frs/download.php/778/super_grub_disk_english_usb_0.9673.tar.bz2")
[*]You'll also need an .iso file for whichever *buntu you want to install, or to run as a LiveCD (USB) to try it out. Super Grub Disk and Ubuntu Live CD is a good combination for a rescue disk, so you can keep this USB Disk for a rescue disk after Ubuntu is installed in your computer. You can use any Ubuntu Live CD you like. the Ubuntu 'Alternate CD', is supposed to work if you add 'vesa vga=771' as kernel parameters.[/LIST]**Formatting your USB disk**[LIST=1]

---

### Post by Herman on 2008-01-14
```
title       Ubuntu Gutsy Gibbon in Persistent Mode
kernel   $(grub_device)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper **[COLOR=Sienna]vesa vga=771[/COLOR]** quiet splash --
initrd    $(grub_device)/casper/initrd.gz
``` Something like that probably. 
I haven't tried the 'Alternate CD in a Live USB myself at all, I have only read that it's supposed to be possible if we add 'vesa vga=771' to the kernel options in the GRUB menu.

I would think we wouldn't care about persistence when using the Alternate CD, so I removed that in the above boot entry, but you can still keep that option if you want.

If you have around 257 MB or RAM, but the 'Desktop' LiveCD won't run, (it's extremely slow or freeezes from lack of RAM), often you can use a [GParted -- LiveCD]("http://gparted.sourceforge.net/")
 and make a swap area on your hard disk for the Live CD to use when it doesn't have enough RAM. That makes a big difference to it, and often you'll find the Live CD will be able to perform the install after that, without any problems at all.
I'll have a try at making the USB disk from the Alternate CD myself, at the same time, and see what problems I run into, and if I run into any problems I'll try to solve them for you. I can't guarantee when I'll have that finished though, as I get interupted a lot, and I'm not even certain this will work for sure. You can try too if you like and we can post back here when we have some progress. It's up to you.

---

### Post by Herman on 2008-01-14
Okay, first the good news...
 I have the USB made with the 'Alternate' CD in it and I have the menu.lst right, as far as I know, because it's booting.  :)

Now the bad news...
It boots and I can start the first few screens of the install, then it says 'Your installation CD-ROM couldn't be mounted, this probably means your installation CD is not in the drive.", and the next screen is a red screen with a similar message to confirm that. I don't know how to get around this. The failing step is "Detect and Mount a CD-ROM.". :(
```
Here's the menu.lst for it, for what it's worth,
# You can edit this file to add your own distribution
# You can choose default to 0 to select first entry
# which it is usually the entry for the default distro
#
#Thank you adrian15!
#
# You can also set timeout to something as 10
#
# This is the shortcut to call Super Grub Disk (commented)
#title Super Grub Disk
## The two commands: setgrubdevice and usbshift are needed
## so that SGD works well.
usbshift

#configfile $(grub_device)/boot/sgd/menu.lst
#
# Just after default and timeout statements you have to put
# setgrubdevice so that grub device is correctly set.

default 0
#timeout 2
setgrubdevice # This is compulsory
# The two commands: setgrubdevice and usbshift are needed
# so that SGD works well.
usbshift
#gfxmenu /boot/grub/message
foreground ffffff
background 0c00ff
color white/brown yellow/cyan

title       Ubuntu Gutsy Gibbon Alternate Install in Text Mode
kernel   $(grub_device)/install/vmlinuz file=/cdrom/preseed/ubuntu.seed vesa vga=771 quiet --
initrd    $(grub_device)/install/initrd.gz

title       Super Grub Disk
configfile $(grub_device)/boot/sgd/menu.lst

title      Ubuntu Gutsy Gibbon Alternate Install in Expert Mode
kernel   $(grub_device)/install/vmlinuz file=/cdrom/preseed/ubuntu.seed priority=low vesa vga=771 quiet --
initrd   $(grub_device)/install/initrd.gz 

title      Ubuntu Gutsy Gibbon Alternate OEM install (for manufacturers)
kernel   $(grub_device)/install/vmlinuz MENU=/bin/cdrom-checker-menu vesa vga=771 quiet --
initrd    $(grub_device)/install/initrd.gz 

title      Ubuntu Gutsy Gibbon Alternate Install a command-line system
kernel   $(grub_device)/install/vmlinuz file=/cdrom/preseed/cli.seed vesa vga=771 quiet --
initrd    $(grub_device)/install/initrd.gz 

title        Rescue a broken system
kernel    $(grub_device)/install/vmlinuz rescue/enable=true vesa vga=771 quiet --
initrd     $(grub_device)/install/initrd.gz 

title        Memory Test
kernel    $(grub_device)/install/mt86plus  - 

title       Boot the First Hard Disk
root       (hd0)
chainloader +1

title       Boot the Second Hard Disk
root      (hd1)
chainloader +1
```
Now what? :confused:

Regards, Herman :)

---

### Post by ibbers on 2008-01-15
> **Herman said:**
> Okay, first the good news...
 I have the USB made with the 'Alternate' CD in it and I have the menu.lst right, as far as I know, because it's booting.  :)

Now the bad news...
It boots and I can start the first few screens of the install, then it says 'Your installation CD-ROM couldn't be mounted, this probably means your installation CD is not in the drive.", and the next screen is a red screen with a similar message to confirm that. I don't know how to get around this. The failing step is "Detect and Mount a CD-ROM.". :( 


Now what? lol....

*sigh*.... somedays the universe just doesn't like me, does it?

Well, I may have found a workaround.... plugging my USB CD-ROM drive into a usb hub on my mini-pc (a "fit-pc"), and putting the gutsy alternate CD in there allowed me to get so far up to the install base systems stage...

so basically the instal prog is running from the USB, but drawing the installation files from the USB-CDROM drive....

the failing step of "Detect and Mount a CD-ROM" was what drew me to a usb stick solution in the first place, ironically... I hadn't been able to get a instal working from my USB CD-ROM (since fit-pc's don't have CD-ROM drives, and only 2 usb ports) as it kept failing to find itself when it went to load installer components.

Well, fingers crossed this workaround of sorts worked, i'll let you know....

lol... *sigh*.... ;)

Ib

---

### Post by Herman on 2008-01-15
:)  Cool!  you're a genius!

---

### Post by MQMike on 2008-01-15
What a relief to see there's some room here for admitting questions  :)

Good news:  My experiments putting Kubuntu 7.10 on a UFD (USB flash drive), Live-persistent, are so far successful, using these and other methods.

Other news:

Remember, I'm speaking from ignorance now.  The main boot entry is:

title       Ubuntu Gutsy Gibbon in Persistent Mode
kernel   $(grub_device)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper persistent quiet splash --
initrd    $(grub_device)/casper/initrd.gz

Using this, I was getting weird “can not access or mount /media/cdrom” messages when I tried to work on/with the UFD loaded with the Live Kubuntu—even though there was no cdrom in sight.  The 2 partitions on the UFD were not mounted as /media/cdrom!  They were something like /media/sdcx/etc.  I don't understand the part that says  file=/cdrom/preseed/ubuntu.seed, and I wonder if it had something to do with this behavior.  Sorry I can't be more precise.  It occurred in the midst of some problematic testing and I did not try to reproduce it.  So, then I went with a suggestion from both Tekno_Cowbo (see his post above) and KOLO (at Kubuntu), and I tried this method:

title  Kubuntu 7.10 LIVE Persistent
root (hd0,0)
kernel /casper/vmlinuz  boot=casper  ramdisk_size=1048576  root=/dev/ram  rw quiet splash persistent
initrd /casper/initrd.gz

And since then, it has gone well (so far).

However, * it did not work with casper-rw formatted as ext2 *.  It did work that way once or twice, but then data corruption from failure to unmount (upon shutdown) caused it to fail (in many ways, including losing my X display and some persistent settings) on subsequent re-boots.

KOLO told me to use ext3 for casper-rw, and that worked perfectly ever since (perhaps because of the journalling/checking).  And I am not worried about UFD wear-out from ext3 writes.  KOLO's has run 2 years with moderate use.  Besides, how many UFD's do you hear about biting the dust?  If mine does wear out, it will have been a very productive $17 experiment (2 GB Kingston, on sale).  As always, you should back up anything important (to a second UFD or to internal/external HDD).

Then, I found this well-known Gutsy bug on unmounting these pups.  It might be useful to anybody trying to fine tune, workaround, or troubleshoot:

[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/125702](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/125702)
(I posted as mikeXYZ)

That's my two cents worth, FWIW.  All in all, I'm very happy with the stick now (even though the correct time does not stick...)
:)

---

### Post by adrian15 on 2008-01-16
> **MQMike said:**
> I have noticed this "geometry" issue popping up now and then, here and there!

Actually, the tip you gave at your web site about using geometry to find out what is where on the drives, that tip is one of the best tools I know of.  If you combine geometry with root-setup-quit, and toss in configfile, you can rescue just about 80% of booting problems (at least temporarily, enough to get booted into an OS to make permanent repairs).

Thanks for the info on doing the updates, too.  When you say that you "edited the fstab file,"  what are you referring to?  (It's early here and maybe my brain isn't yet in gear.  :)  )

Thanks again.

It's interesting how do I hate the geometry command and how other users insist in using it!

I think it's better to mount your pretended drive with the mount command, you identify the correct device for the drive you want to work into and then you can run the device command inside the grub shell.

If you are not using grub inside  linux environment, i.e., booting from SGD directly you can still use Boot & Tools -> Show partitions to identify hd0, hd1, hd2 with your actual hard disk with its partition layout.

Should I finish adopting the geometry command :) ?

adrian15

---

### Post by adrian15 on 2008-01-16
> **MQMike said:**
> I have a question about “persistence,” in the context of making a bootable LIVE K/Ubuntu USB flash drive.

If we make the stick persistent, an example of what we want would be to store various * static * data/configurations.  Example:  The background image on the Desktop (set once and for all);  the selection of icons on the kicker panel; configuration/preference settings for the resident web browser, the word processor OOo Writer, and so on.  These items are set once and for all and do not change—they are only “read.”

An example of what, I would think, we do NOT want would be for the LIVE K/Ubuntu (on flash drive) to be constantly writing to the flash drive such things as variable files, tmp files (both /tmp and /var/tmp), swap, and such things.  There is the issue of “wearing out” the stick with re-write cycles.

In fact, one of the references raises the question (“Outstanding Questions”):
“Every single disk write goes to the USB stick, which GNOME loves to do all the time.”
[https://help.ubuntu.com/community/LiveCDPersistence#head-4be8ad9301322add5fa96636940e31f46cae5951](https://help.ubuntu.com/community/LiveCDPersistence#head-4be8ad9301322add5fa96636940e31f46cae5951)

We know that Puppy Linux (on LIVE USB flash drive) is specially designed to “optimize” this performance criterion (eliminate disk writes to the USB flash drive), whereas, I’ve read that Knoppix on a USB stick is a bad idea for this reason (“wear-out" performance).

Do we know where the current “persistent” fix stands with respect to the wear-out criterion on USB flash drives?  Is this an issue?  

==> What *exactly* gets written to the persistent LIVE stick?

Can  anyone copy-paste the puppy linux /etc/fstab and the ubuntu /etc/fstab so that I can advise you how to edit ubuntu fstab to avoid so many unneeded read and write ?

adrian15

---

### Post by MQMike on 2008-01-16
Hi adrian15   :)

Live flash drive Puppy /etc/fstab:

none          /proc        proc     defaults               0 0
none          /sys         sysfs    defaults               0 0
none          /dev/pts     devpts   gid=2,mode=620         0 0
/dev/fd0      /mnt/floppy  auto     noauto,rw              0 0


Live flash drive (persistent) Kubuntu 7.10 /etc/fstab:

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb2 swap swap defaults 0 0

(I have a swap file on hard drive sdb2)

That's exactly what came up. 
 (Took me awhile as I am not yet very familiar with working in Puppy.  For one thing, you work as root and so should not use sudo at the terminal--can't stat suoders file and so on.)

--Mike

---

### Post by adrian15 on 2008-01-17
> **MQMike said:**
> 
Live flash drive Puppy /etc/fstab:

none          /proc        proc     defaults               0 0
none          /sys         sysfs    defaults               0 0
none          /dev/pts     devpts   gid=2,mode=620         0 0
/dev/fd0      /mnt/floppy  auto     noauto,rw              0 0


That's going to be difficult. It seems that loading the system in ram is done in a former step. What I find strange is that there is not a / line. Haven't you left any line to copy-paste ?

adrian15

---

### Post by MQMike on 2008-01-17
That's all there is for Puppy's fstab--the 4 lines (I checked a few times as I was using Puppy).  It is strange.

---

### Post by adrian15 on 2008-01-17
> **MQMike said:**
> That's all there is for Puppy's fstab--the 4 lines (I checked a few times as I was using Puppy).  It is strange.

Do you have a direct download link to one of this puppy linux persistent installations so that I check it? I suppose our question is answered in the initrd file and its way of putting sytem into RAM.

However you should be able to use tmpfs or ramfs to mount /var or /tmp into ram.

Try with this line in fstab for example:

```

/var       /var     ramfs     bind     0        0

```

and tell us if it evens work because I fear some problems with the bind option because ramfs is supposed not to have any option.

Or maybe the tmpfs is a best bet:

```

tmpfs	/dev/shm	tmpfs	defaults	0 0
/dev/shm        /var      tmpfs   defaults        0 0

```

These are some thoughts and I have not checked them. Maybe an script like the one explained [here]("http://nomadic.sourceforge.net/production/misc/redhat-6.x-readonly.html") in **Edit /etc/rc.d/rc.sysinit ** is what we need.


adrian15

---

### Post by MQMike on 2008-01-17
Here's all I have on it.  When you install Puppy to Live CD and run it, there's an option on it to install Puppy to flash drive using the Puppy Universal Installer.

Puppy Home:     [http://puppylinux.net/index.html](http://puppylinux.net/index.html)
Flash-Puppy page:     [http://puppylinux.net/flash-puppy.htm](http://puppylinux.net/flash-puppy.htm)
Download page (including MD5 sums):     [http://puppylinux.net/download/downpage.htm](http://puppylinux.net/download/downpage.htm)

***   Puppy:   Special solutions to minimize UFD re-write cycles.
[http://puppylinux.org/wikka/FlashDetail](http://puppylinux.org/wikka/FlashDetail)

---

### Post by Herman on 2008-01-28
Originally posted by Adrian15:
>  Should I finish adopting the geometry command :) ? I think everyone should do things the best way they can that works for them and they like. If there are more than one way to do things, there will always be some people who will go one way and some people who will go the other. It seems to depend on the hardware mainly. :)

Originally posted by mqmike:
>  title       Ubuntu Gutsy Gibbon in Persistent Mode
kernel   $(grub_device)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper persistent quiet splash --
initrd    $(grub_device)/casper/initrd.gz

Using this, I was getting weird &#8220;can not access or mount /media/cdrom&#8221; messages when I tried to work on/with the UFD loaded with the Live Kubuntu&#8212;even though there was no cdrom in sight. The 2 partitions on the UFD were not mounted as /media/cdrom! They were something like /media/sdcx/etc. I don't understand the part that says file=/cdrom/preseed/ubuntu.seed, and I wonder if it had something to do with this behavior. Sorry I can't be more precise. It occurred in the midst of some problematic testing and I did not try to reproduce it. So, then I went with a suggestion from both Tekno_Cowbo (see his post above) and KOLO (at Kubuntu), and I tried this method:

title  Kubuntu 7.10 LIVE Persistent
root (hd0,0)
kernel /casper/vmlinuz  boot=casper  ramdisk_size=1048576  root=/dev/ram  rw quiet splash persistent
initrd /casper/initrd.gz

And since then, it has gone well (so far).
 I don't know why that could be. Mine works fine. Thanks for the info, it might help someone. 

Originally posted by MQMike: > However, * it did not work with casper-rw formatted as ext2 *. It did work that way once or twice, but then data corruption from failure to unmount (upon shutdown) caused it to fail (in many ways, including losing my X display and some persistent settings) on subsequent re-boots.

KOLO told me to use ext3 for casper-rw, and that worked perfectly ever since (perhaps because of the journalling/checking). And I am not worried about UFD wear-out from ext3 writes. KOLO's has run 2 years with moderate use. Besides, how many UFD's do you hear about biting the dust? If mine does wear out, it will have been a very productive $17 experiment (2 GB Kingston, on sale). As always, you should back up anything important (to a second UFD or to internal/external HDD). The Ubuntu710 partition is one with the liveCD files in it. I don't imagine that would ever be written to at all. To illustrate, here is the Ubuntu Community Docs '[LiveCDPersistence]("https://help.ubuntu.com/community/LiveCDPersistence")', where they only use the USB stick for the casper-rw half of the job and they still use the actual Live CD for the Live CD part. The only reason for making the Ubuntu710 partition ext2 rather than ext3 is to save a little bit of space, but that can be ext3 too if people want.
Interestingly, they are using a FAT16 file system for casper-rw.  I like the ext3 file system for the casper-rw partition, but every time mine unmounts, I do see some file system errors in the casper-rw file system. They seem to disappear on rebooting, I guess the file system check at boot up fixes the file system again. Sometimes I give it a better file system check with GParted too. Mine's still working fine so far. I wonder how well reiserfs would work.

My news is I have been working on my website's [SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm") Page. The page is designed so someone new to Ubuntu will be able to (I hope) see in the simplest possible way how to set up a secure home network in a protected LAN. It's a challenge to try to explain something like networking in a simple way so anyone should be able to understand it. It gets progressively a little more complex as people get further down the page.
Near the bottom of the page is how to install [seahorse]("http://www.gnome.org/projects/seahorse/") for file encryption as well as RSA keys for SSH networking, and a little about port forwarding and ideas for dealing with dynamic IP addresses.
That means if people can figure all that out, they can travel with their 4.0 GB USB stick and still have access to all of the files in their home PC's as long as they can get an internet connection.
Plus there's the added privacy of file encryption in case they lose the USB stick somehow.

Regards, Herman  :)

---

### Post by MQMike on 2008-01-28
Hi Herman and everyone,

Thanks for the reply and the other info.
I just cloned (made an exact copy of)  the Live persistent Kubuntu flash drive which is handy; in case anyone would want to do the same:
The source or “input file” (if) is the Kubuntu 7.10 live persistent flash drive (2 GB San Disk);
The target or “output file” (of) is a blank flash drive, formatted FAT32 (2 GB Kingston);
Then, plug both in your PC and see how they come up in K/Ubuntu:
the Kubuntu flash drive came up as sdc, and the blank flash drive came up as sdd.
Then, at a terminal, issue this single command:
dd if=/dev/sdc of=/dev/sdd bs=4096 conv=notrunc,noerror
Output:
492671+1 records in
492671+1 records out
2017984000 bytes (2.0 GB) copied, 425.104 seconds, 4.7 MB/s

Worked perfectly (I tested the new sdd clone – all my persistent settings were there and worked.). The dd copied everything--GRUB, MBR, the two SanDisk partitions, and the ext3 formatted filesystems.

(If you want to clean out a used flash drive, you can write zeros to it and make it like new:
dd if=/dev/zero of=/dev/sdd conv=notrunc
(where the flash drive is seen as sdd in your K/Ubuntu--CAUTION: make sure you use the correct sdx here!!!). Then use GParted to partition it (like FAT32) with a new Disk Label. Then do the cloning as above.

---

### Post by itrade on 2008-01-29
Hello there Herman

I am having an awful time with the Pendrivelinux.com instructions and I happend to see your post.

I followed the instructions to  the letter, it did not work I did notice some irregularities I got extra error before the  "cannot create symbolic link". Also the first time the U710fix.zip would not unzip

I redid the entire  install from scratch This time everything worked I got the unzip etc but when I booted the USB I got the Ubuntu screen with the bar going back and forth a  a new entry with the persistent option. After that I get a BUSY BOXX with a prompt command initash something like that.

Any ways  If I boot up Livecd whjen i install the pendrive  two usb directories mount themselves automatically the casper- rw and the ubuntu710.

What can I do to remedy the situation and make it bootable without the LIVECD.

---

### Post by Herman on 2008-01-29
Hello itrade,
These how-tos for making the Live CD into a USB memory stick can be a challenge even for someone with some experience with Linux. It's important to take your time and read all the instructions well. It took me a few times to get the idea of it myself. The Pendrive site was the first site I was able to have a successful outcome with.
A busybox error, in my experience, is usually associated with some problem in finding the initrd.img file, so check your boot entry for the correct path to an initrd.img file, or check that your initrd.img file is in the correct location in your file system. 
If you are following the Pendrive how-to, they are using syslinux to boot with, so the kernel and initrd.img are copied out into the root of the file system. Maybe you will need to check that has worked if you are using the Pendrive how-to.

Are you using this how-to now or are you still trying to master the Pendrive how-to?
I don't mind helping you no matter which one you are doing.

Regards, Herman :)

---

### Post by shaggy999 on 2008-02-02
Can anybody help me? I'm trying to do this exactly as stated but I'm not getting to far. I have a SanDisk Cruzer 4 GB memory stick. Here is my partition setup:

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f10c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          25      200781   83  Linux
/dev/sda2              26        9729    77947380   83  Linux

Disk /dev/sdb: 4103 MB, 4103938560 bytes
255 heads, 63 sectors/track, 498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b3ef1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          11       88326   83  Linux
/dev/sdb2              12         498     3911827+   b  W95 FAT32

```

I go through the first two steps and install syslinux and all that and when I reboot and boot off my usb key I get super grub. Great! But when I select to boot the LiveCD off the second partition I get an error something along the lines of this:

```
Can't boot (hd(1,1). Unknown Partition type 0x83, incompatible execution type
```

Anybody have any ideas?

---

### Post by shaggy999 on 2008-02-02
Ok, I got past that point. Apparantly for some obscure reason when I boot off my usb key hd0 and hd1 switch places!! It thought that hd(1,1) was my usb key's second partition, which it was actually the hard drive's second partition! And it makes sense that it couldn't understand THAT partition, because it's an encrypted partition w/ lvm on top and 3 volumes on top of that.

So what I did was changed the menu.lst to boot hd(0,1) instead of hd(1,1). But that kind of scares me because now I'm worried I'll get confused at some point and trash my hd's mbr or worse.

---

### Post by Herman on 2008-02-02
Hello shaggy999,
You are doing that second how to eh?  The three part one that uses syslinux, obviously.

I forget why but when I checked up to see what you are talking about I realized  I had the 'usbshift' command for Super Grub DIsk's menu.lst after the Ubuntu boot entry instead of before it.
Sorry about that. 
I have now moved it up and pasted it further up, and that should make Super Grub Disk get the device order right from now on for anyone else who might happen to follow that second how-to.

The 'usbshift' command was in the Super Grub Disk's menu entry, so your Super Grub Disk will work fine, it won;t matter if you leave yours like that. You can change it if you want, but then you'll have to change your (hd1,1) back to (hd0,1) again too.
Thanks for bringing that matter to my attention, it might save someone else from having that problem.

Trash your hard disk's Master Boot Record or worse? By accidentally installing GRUB to it?

Grub is an upgrade for most MBRs. I suppose anything that's not planned can be inconvenient though.
I don't think GRUB will really hurt anyone's MBR, unless maybe if you have a RAID setup, then you probably need to know what you're doing to install GRUB in that case. 
I didn't think anyone would be able to follow one of these how-tos without already having a Ubuntu installation though, so you would already have GRUB installed to MBR anyway wouldn't you? Unless your talking about using it in a different computer maybe.

Well, once again, thanks and sorry for any inconvenience that caused.

Regards, Herman :)

---

### Post by shaggy999 on 2008-02-02
Thanks for the info. I suspected something was off in that config file, but I couldn't be too sure since I don't know a whole lot about grub. :)

What I meant about grub messing up my mbr is that I have the craziest partition setup I've ever had in my life. I have a 200 MB boot partition and then the rest is a cryptload partition on an 80 gig drive. On top of that I have an LVM partition over the top, and then inside the LVM I have root, /home, and a swap partition setup. That's the craziest I've ever seen with a partition. It's my first time setting up this encrypted partition, so if I somehow hose the mbr or /boot partition then I really lose everything! My next step is to back up the mbr and /boot partition in case I do something retarded.

Anyway, my concern is that I would intend to do something to the usbkey and instead overwrite the hard drive's mbr and lose my delicately configured system that I just set up yesterday.

---

### Post by shaggy999 on 2008-02-02
By the way, the persistent mode is pure genius! I wanted a setup like this for Windows for the longest time! It also reminds me of a time when I worked at a library and we used Symantec Ghost to image many generations of machines with dozens of different network card configs. I kept trying to make the "ultimate" ghost boot cd that had all the drivers, but I kept running into problems with the ram filesystem and when things would load, etc....

Windows... bah. Ghost... bah.... Open source is awesome!

---

### Post by Herman on 2008-02-02
Yes, the usbshift command is a special one unique to Super Grub Disk by adrian15. with regular GNU-GRUB we often have to play around between (hd0) and (hd1) and experiment or run a few tests or whatever to get it right, but with Super Grub Disk we're not supposed to have to do that, the usbshift should handle it automatically. 


If you want to make a backup of your MBR I normally use the method here in this link, [MBR backup and restore]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd"). For just the bootloader part of the MBR, just the first 446 bytes is all you need to back up. I don't know much about LVM. Maybe in that case, since yours is specail, you might want to back up the entire 512 bytes, I imagine you yourself would know best.

Regards, Herman :)

---

### Post by Tekno_Cowboy on 2008-02-12
If you want to reduce the ammount of writes and still have programs up to date and whatnot, you can install to your regular system, get just the config you want, and then use remastersys to turn it into a live cd, which you can boot via the tutorial at the beggining of this thread. Another thing you can do, to give yourself cross-platform freespace on a bigger drive, is to put a FAT partition at the beggining of the drive, then your iso partition, then your casper-rw partition. I've done this with a 4GB survivor(about $40 US) and it works great, since I need to use windows at work.

---

### Post by Herman on 2008-02-12
[Remastersys]("http://www.remastersys.klikit.org/")

[Creating Your Own Custom Ubuntu 7.10 Or Linux Mint 4.0 Live-CD With Remastersys]("http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys")

Hey WOW Tekno_Cowboy, thanks for letting me know about Remastersys! That's SUPER COOL! :cool:

Regards,Herman  :)

---

### Post by MQMike on 2008-02-13
Here's a recent discussion about this “new” remastering interest (with some good comments, tips, and links):
[http://kubuntuforums.net/forums/index.php?topic=3089356.0](http://kubuntuforums.net/forums/index.php?topic=3089356.0)

I've had some problems with the CD but was told (in that thread) to try it with a FRESH install of the OS (which I haven't had time to do yet).


About rewrite cycles to the flash drive, possibly risking flash drive wear-out, as I said above, one user told me he has run 2 years with his persistent flash drive and no problems.  Another experienced, long-time PC consultant said recently:
“Mike, you'll lose the flash device before you wear it out, so play away.   That knowledge came directly from a senior Intel Flash memory engineer during a dinner, at my expense, at Gruet's Steakhouse. The info is reliable...we hadn't ordered the second bottle of wine at that point.”


If there is something absolutely critical about your persistent flash drive, simply use that one-line dd statement I gave (above somewhere) to clone it now and then.  (If you understand dd enough, I think you could clone the flash drive to a file on a hard drive, then restore the file to the flash drive if necessary.  I've been doing similar by using dd to write my Kubuntu root partition as a backup file in my /home directory on a separate partition, and that works fine as I've tested it.)

---

### Post by MQMike on 2008-04-28
Anyone try this with 8.04 (&#8220;normal&#8221; version, not remix) yet, using  Tekno_Cowboy's menu.lst:

title Kubuntu 7.10 LIVE Persistent
root (hd0,0)
kernel /casper/vmlinuz boot=casper ramdisk_size=1048576 root=/dev/ram rw quiet splash persistent
initrd /casper/initrd.gz

I just began to look at this, the flash drive boots OK, the Kubuntu screen shows up as loading, then it drops to a BusyBox prompt
(initramfs)

I just started working on this today, but thought I'd post to see if anyone got their 8.04 persistent live flash drive going.

---

### Post by meierfra. on 2008-04-28
MQMike:  I have the exact same problem. I have no idea how to fix it, but I do know that it's looking for files on the CD drive. And if the  Live CD is in the CD drive while trying to boot from the USB drive, the Live CD gets booted instead.

---

### Post by MQMike on 2008-04-28
Thanks for your feedback,meierfra.

I just re-did the project from scratch, checking every step, and still got the same result.  It is not a problem booting, as it does boot.  And as you said, it tries to do its thing and load.  Hmmm.  Have to work on this.  You'd think (or, that is, I expected) 8.04 to be even better behaved for flash drive, but no-go yet.  7.10 went in so problem-free.  And so it goes.
Thanks again.

Maybe someone else has looked at this for us, too.

---

### Post by shaggy999 on 2008-04-28
I started working on this but stopped just short of working on the persistent part because I was short of time. I plan to work on this later this week or this weekend.

---

### Post by adrian15 on 2008-04-29
> **MQMike said:**
> Anyone try this with 8.04 (“normal” version, not remix) yet, using  Tekno_Cowboy's menu.lst:

title Kubuntu 7.10 LIVE Persistent
root (hd0,0)
kernel /casper/vmlinuz boot=casper ramdisk_size=1048576 root=/dev/ram rw quiet splash persistent
initrd /casper/initrd.gz

I just began to look at this, the flash drive boots OK, the Kubuntu screen shows up as loading, then it drops to a BusyBox prompt
(initramfs)

I just started working on this today, but thought I'd post to see if anyone got their 8.04 persistent live flash drive going.

Shouldn't you use a new menu.lst based on the new 8.04 menu.lst?

You can copy-paste the new 8.04 menu.lst if you want some advice from me.

adrian15

---

### Post by MQMike on 2008-04-29
adrian15, Thanks and Yes, that was my next inquiry, to see what if any boot options are different.
Here's the new menu.lst for the regular Kubuntu 8.04:

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=my_UUID ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=my_UUID ro single
initrd		/boot/initrd.img-2.6.24-16-generic

There's not much there!  
This is the boot entry on the flash drive:

title Kubuntu 8.04 LIVE Persistent
root (hd0,0)
kernel /casper/vmlinuz boot=casper ramdisk_size=1048576 root=/dev/ram rw quiet splash persistent
initrd /casper/initrd.gz

(It worked for 7.10)

I checked in the new casper folder, and vmlinuz and initrd.gz are there.

Kubuntu DOES boot from the flash drive and goes to the blue Kubuntu screen where the horizontal progress bar oscillates back and forth, but then, abruptly, it drops to BusyBox
(intramfs)

The  post by meierfra above seems relevant.

---

### Post by adrian15 on 2008-04-29
> **MQMike said:**
> adrian15, Thanks and Yes, that was my next inquiry, to see what if any boot options are different.
Here's the new menu.lst for the regular Kubuntu 8.04:

Let's see.
> **MQMike said:**
> 
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=my_UUID ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=my_UUID ro single
initrd		/boot/initrd.img-2.6.24-16-generic

There's not much there!  

No, there isn't.
> **MQMike said:**
> 
This is the boot entry on the flash drive:

title Kubuntu 8.04 LIVE Persistent
root (hd0,0)
kernel /casper/vmlinuz boot=casper ramdisk_size=1048576 root=/dev/ram rw quiet splash persistent
initrd /casper/initrd.gz

(It worked for 7.10)

I see. I think I need the cdrom's isolinux.cfg content file then.
> **MQMike said:**
> 
I checked in the new casper folder, and vmlinuz and initrd.gz are there.

Kubuntu DOES boot from the flash drive and goes to the blue Kubuntu screen where the horizontal progress bar oscillates back and forth, but then, abruptly, it drops to BusyBox
(intramfs)

The  post by meierfra above seems relevant.

[Removing quiet and splash as explained here](http://www.supergrubdisk.org/wiki/Linux_Kernel_Boot_Parametres_Howto#Tips) can be useful to determine the problem.

adrian15

---

### Post by MQMike on 2008-04-29
Here's the isolinux config file.  And I'll check the link you gave (after I return from an appointment).

DEFAULT /casper/vmlinuz
GFXBOOT bootlogo
APPEND  file=/cdrom/preseed/kubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
LABEL live
  menu label ^Try Kubuntu without any change to your computer
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/kubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
LABEL live-install
  menu label ^Install Kubuntu
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/kubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash --
LABEL check
  menu label ^Check CD for defects
  kernel /casper/vmlinuz
  append  boot=casper integrity-check initrd=/casper/initrd.gz quiet splash --
LABEL memtest
  menu label Test ^memory
  kernel /install/mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt

---

### Post by MQMike on 2008-04-29
I have time to post this, then will return later.  I modified the menu.lst on the flash drive by omitting quiet splash from the kernel line, rebooted, and these are the last few lines prior to it stopping:

Registering unionfs 1.4
unionfs debugging not enabled
loop: module loaded
squashfs: version 3.3
EXT3-fs: Unrecognized mount option “mode=755” or missing value
BusyBox v1.1.3 Built-in shell (ash)
(initramfs)_

That looks like a promising clue (it's almost in plain language!  :)  ), but I'm out of time and am posting it for others to see/use.

---

### Post by MQMike on 2008-04-29
A few more details -- Actually, the endgame is this (scrolling messages):

EXT3-fs: mounted filesystem with ordered data mode
kjournal starting: commit interval 5 seconds
...
and those two lines repeat many times
...
then comes this:

Registering unionfs 1.4
unionfs debugging not enabled
loop: module loaded
squashfs: version 3.3
EXT3-fs: Unrecognized mount option &#8220;mode=755&#8221; or missing value
BusyBox v1.1.3 Built-in shell (ash)
(initramfs)_
and it stops here.

I typed dmesg and got:
EXT3-fs: Unrecognized mount option &#8220;mode=75&#8221; or missing value
BusyBox v1.1.3 Built-in shell (ash)
(initramfs)_

>> Note that it says &#8220;mode=75&#8221;  which differs from the first stop message above &#8220;mode=755.&#8221;

Not being a programmer/dev, or insider-kernel guy, I'm trying to think what might be visible to the user that can be tweaked.  If this were a Desktop K/Ubuntu with a mode mounting message, for example, one might begin with the fstab.  But here, I'm not yet sure where to begin; but still working on it as time permits.

My two partitions on the flash drive are root Ext3 and casper-rw Ext3.
I did not have good persistent experience with Ext2 (as noted in the bug report cited above for 7.10).



EDIT
I just ran the working 7.10 Live persistent flash drive.
It also has the repeating block of two lines:
EXT3-fs: mounted filesystem with ordered data mode
kjournal starting: commit interval 5 seconds

So, the difference is just in the endgame:
EXT3-fs: Unrecognized mount option &#8220;mode=755&#8221; or missing value
BusyBox v1.1.3 Built-in shell (ash)
(initramfs)_
and it stops here.
(and those other "Mode=75" messages I reported above.

---

### Post by adrian15 on 2008-04-30
> **MQMike said:**
> 
EDIT
I just ran the working 7.10 Live persistent flash drive.
It also has the repeating block of two lines:
EXT3-fs: mounted filesystem with ordered data mode
kjournal starting: commit interval 5 seconds

So, the difference is just in the endgame:
EXT3-fs: Unrecognized mount option “mode=755” or missing value
BusyBox v1.1.3 Built-in shell (ash)
(initramfs)_
and it stops here.
(and those other "Mode=75" messages I reported above.

Copy paste here both usb's ubuntu 7.10 fstab and ubuntu 8.04 fstab and we will see what's wrong I suppose.

adrian15

---

### Post by MQMike on 2008-04-30
That's not very revealing.  In both cases (live 7.10 and live 8.04), the fstab is the same:

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb5 swap swap defaults 0 0


It almost seems that the error has something to do with permissions.
I have to investigate what this Mode=  stuff is about.

---

### Post by Mike V on 2008-05-02
Hi, what if I install Ubuntu to a hard drive and then copy everything to a USB, what do I need to fix in order to boot from the USB? I want to have a very small working system without gnome but I don't want DSL.

---

### Post by shaggy999 on 2008-05-02
Installing the OS to a USB key isn't a problem. In fact, you should be able to just install the OS straight onto the USB key with no issues. But be aware that the USB key install will then be tied to the setup of the computer. Meaning your installation will probably only be good on the computer it was installed on. That's what's cool about the LiveCD + Persistency, you get the customized features of a personal install plus the flexibility of a generic system that autodetects stuff as it boots up.

---

### Post by Herman on 2008-05-02
:) Yes -exactly- I agree with shaggy99, the hardware detection and automatic configuring of drivers and settings in the LiveCD is one of the main reasons for wanting to install any version of Ubuntu in this manner.

Otherwise, if you only want Ubuntu for one specific PC, just install in the USB disk in the normal way, it's a lot easier. You can probably get away with running it in similar computers even, but if you try it in a computer that's too much different you will likely need to reconfigure the hardware. The old way to reconfigure the Xserver drivers and settings was to run 'sudo dpkg-reconfigure xserver-xorg', [Xserver Page]("http://users.bigpond.net.au/hermanzone/p7.html").

I have read in the [Hardy Heron Release Notes]("http://www.ubuntu.com/getubuntu/releasenotes/804"), that one of the new innovations that Hardy Heron introduces in Ubuntu is the new X windows Recovery feature.
> A new X windows recovery feature is available. If     you are unable to boot after attempting changes, you can reboot, choose     the restore option in the boot menu, and then select the 'xfix Try to     fix X server' option on the Recovery Menu. This should restore your X     windows configuration to a usable condition and allow you to boot     normally.      I have not yet had time to try out a USB disk install myself to test things out and see what happens, and more importantly, how Hardy Heron will perform if it is plugged into different computers, and how well this new X window recovery feature works or even what it does exactly. I hope to get time some time to try that out this weekend, I hope.

Other than portability, good reasons for wanting the Live CD in a USB disk are for having an alternative method for running the Ubuntu installation in a computer without a CD-ROM drive, and having a great rescue system, and being able to show Ubuntu off (demonstrate Ubuntu running at full speed) to people who haven't seen Ubuntu before, and for the novelty of having an operating system running in such a nifty small (in physical size) device.
Having Super Grub Disk there to boot it is cool too, at least I think so.

If this installation method turns out to be obsolete, we can still install Super Grub DIsk for USB and then install Ubuntu in the USB disk in the regular way instead of in this complicated way and it will probably work as well or even better.

Thanks to everyone who is working on this too, by the way, I really appreciate the help, I have been reading the posts here and keeping up with the news but haven't had anything useful to contribute yet. :)

Regards, Herman :)

> I want to have a very small working system without gnome but I don't want DSL.If you really want to save disk space you might like to try out a minimal install and install your own Desktop. The IcwWM Desktop is quite nice, or XFCE. Here's a link about a minimal install, but you don't have to dual boot or install in low memory mode, and you should be able to use Hardy instead of Gutsy,  [Windows98SE+Ubuntu Gutsy Gibbon]("http://users.bigpond.net.au/hermanzone/p2.htm")
I prefer the full Gnome install myself. 
A regular Ubuntu install used to take only 1.8 GB of hard disk space, I used to dual boot Ubuntu Warty Warthog 4.10 with Windows 98SE on a 6.0 GB hard disk drive, and that seemed like all the hard disk space I would ever need! (LOL), I suppose I didn't know of anything better back then. :)
Now, we have USB flash sticks even bigger than that! How times have changed!

---

### Post by Mike V on 2008-05-03
oh, I thought that I could boot from ubuntu usb and as I will only have ubuntu-standard there wont be any problem if the computer have changed a little or too much, thnx for pointing that out

I will try to do your method with xubuntu 8.04 and see what happens, or maybe linuxmint, I suppose that since is based on ubuntu it will do fine too, or I'm wrong?

---

### Post by Herman on 2008-05-03
Yes, I think Linux Mint is based on Ubuntu too.
I'm having a hard time just getting Hardy to install and boot in a USB flash memory stick even as a regular install myself at the moment though. Maybe I'm just having a run of bad luck. I have days like this every now and then, when absolutely nothing goes according to plan. Maybe it's just me. Actually I was having a good day up until now. (LOL). Let me know how you get along. :)

---

### Post by MQMike on 2008-05-03
I'm still working on putting Kubuntu 8.04 "regular" (not the remix)on live persistent flash drive (as noted above in my posts).
Here's a progress report in case someone smarter/faster than me wants to jump in but encounters the "mode=755" problem:

I'm using the menu.lst of Teckno_Cowboy.

The problem I reported above looks like it can be solved by editing scripts/casper (in the extracted initrd.gz from the CD ROM) as explained here in detail (and the links he provides to pendrivelinux on methods):
[http://t-skariah.blogspot.com/2008/04/ubuntu-804-hardy-heron-on-usb.html](http://t-skariah.blogspot.com/2008/04/ubuntu-804-hardy-heron-on-usb.html)

I am not using his method for installing to USB, but only his tip on editing that file to take out mode=755.

I'll see if that works.  I've been busy remodeling two bathrooms in my house and can't get time to stay on this, but it looks like I'll be able to this weekend.

Since meierfra has encountered this same error (mode=755), I suspect others might also, so this may be one hurdle.  Be nice if a Linux dev-person could explain the what's & why's behind the 755 mounting option for the rw persistence, but it may do fine simply by removing it from the flash drive files.

---

### Post by MQMike on 2008-05-03
That seems to have worked (for me).
I'm still testing, but the straight persistent mode seems to be working well (so far).  Installed to a 2 GB USB Kingston flash drive.
I'll test some more and write something up, but for now, basically, here's what I did (following those links I gave above):

Get your K/Ubuntu download, check it, burn it, test it live.

From the iso CD, access /casper/initrd.gz.
Un-zip it.
Locate the file scripts/casper (among the files of the unzipped initrd.gz).
Edit the line having to do with the mounting option mode=755
to delete just the following string:
mode=755
(leave everything else in that line untouched).
File > Save and File > Quit
Zip it with the new changes you just made to the /scripts/casper file.
Re-boot to test it.

That's the idea.  I made a  directory on my Desktop to work in in K 8.04 (Desktop/work_here)) and did all the work inside it.  You can mess with the logistics at CLI or GUI, and use the gzip commands structured in the links I gave (skariah, and the link to pendrivelinus that he gave in one of his steps).
I had difficulty getting Konsole to do some things (like open the file using kate or kwrite as root, even using kdesu and sudo su) and so had to sort of work back and forth between GUI and CLI (e.g., in GUI, right-click on the file scripts/casper did not offer the option Edit as Root, so I opened Konqueror as root and got it that way).  Seems something in my desktop 8.04 is buggy, but I've seen lots of posts having to do with sudo problems in 8.04.  Who knows!  What I know is that it worked (by hook or by crook).

Still testing it, as I say, but it sure seems to all be there; and for certain, what I've said in this post was sufficient to get it fully booted up into a live session, and changes made so far seem to be persistent.  I'm working it in right now, using Firefox 3 installed through Add/Remove programs | Internet.

---

### Post by MQMike on 2008-05-03
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/219192](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/219192)

Ah, that explains it.
(Thx KOLO)

---

### Post by MQMike on 2008-05-05
BTW,
If you use Ubuntu (not for Kubuntu), there's a patched initrd.gz you can copy into /casper. 
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/219192/?loggingout=1](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/219192/?loggingout=1)
See the post by FlipsideTech 2008-04-29.

If you are using Kubuntu (EDIT: or Ubuntu--it works for either), you can see my manual method in Reply #18 of the following:
[http://kubuntuforums.net/forums/index.php?topic=3089474.msg129956#new](http://kubuntuforums.net/forums/index.php?topic=3089474.msg129956#new)

We hope this will be fixed soon and my posts here will be history. :)
Thanks to Herman for providing this thread where we can mess with K/Ubuntu on live persistent flash drive this way.

---

### Post by Herman on 2008-05-05
:) Thanks for all your hard work, MQMike.
I added a note for Hardy Heron users close to the top of the first how-to referring them to here so they will see your advice.
Thanks adrian15 and meierfra too.

---

### Post by Herman on 2008-05-05
I tried out installing in a flash memory stick just using the standard install method.

I had no problem installing in a USB flash memory stick just in the normal way we would install in any hard drive, but I had a devil of a time trying to get the Gnome Desktop to come up after logging in. I have one made with the IceWM desktop though. That works okay. I don't know what I'm doing wrong. I'm using cheap flash memory sticks, I (two got two for the price of one). Takes over twice as long as normal for the installation should have told me something to begin with. Installing three or four times and messing around with the desktop wasted all the time I had.
I will try again with a decent quality USB flash memory next time I get the time.

---

### Post by Herman on 2008-05-10
This weekend I have tried again to install Ubuntu Hardy Heron in a USB flash memory stick that I know does work well and even this one gave me an empty tan screen after login, (no Gnome Desktop).
This time I installed the Xubuntu Desktop and that works beautifully in Hardy Heron.

Then I found out there is a bug in Hardy Heron that seems to affect Gnome especially in USB devices, refer to these two links, [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/221850](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/221850) and [https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434)
So it is necessary to use the 'ctrl'+'alt'+'del' keyboard combinationa dn login to a virtual terminal and type 'sudo rm /tmp/X0-lock', and 'startx', and then open 'System'-->'Administration'-->'login window', open the security tab, and enable automatic login for the administrative user.

Now I have both of my USB installations fixed, and they are able to boot Ubuntu as they should.

Hardy Heron uses the latest [Xorg 7.3]("http://www.ubuntu.com/getubuntu/releasenotes/804overview#head-34da8c8d2432823a293ea6a0639fe8b9a24c0f77")  Xwindow system from [X.Org Foundation]("http://www.x.org/wiki/").
The new Xserver in Hardy Heron really does seem to be great!
I have tried it in a variety of computers and it can boot and configure itself just as well as a live CD in the computers I have tried it out in so far.

---

### Post by a1234 on 2008-05-10
> **Herman said:**
> 
Now I have both of my USB installations fixed, and they are able to boot Ubuntu as they should.



Great! Can't wait for your update for Heron. I used your Gibbon method for heron with some mod. No go!

Regards

---

### Post by Herman on 2008-05-10
Yeah, but with these amazing advances in the Xserver and the way it can set itself up for different video cards and monitors now, we can just install Ubuntu the ordinary way in a USB device if we want Ubuntu in a flash memory device. It's a simpler way to install and gives a better operating system.

I installed my USB Hardy in my [Acer Aspire 3003 WLMi]("http://www.acerdirect.co.uk/Acer_Aspire_3003WLMi_5150-LX.A5505.340/version.asp") laptop and Hardy was working fine in that.

Then shut it down and booted the USB key in my LEC desktop machine model PM266A, with an ASUS P4V533-MX main board, Intel Celeron 2.60 GHz CPU, and 487.3 MB of RAM with a [Diamond Digital DV171J]("http://www.myshopping.com.au/SP--171847_Mitsubishi_DV171J_DV171JB_17_TFT_Monitor")  LCD monitor.

After that I tried it out in my [Acer Aspire T310 Desktop]("http://www.pcauthority.com.au/Review/18221,acer-aspire-t310.aspx") with an [ATI 9200]("http://ati.amd.com/products/radeon9200/radeon9200/specs.html") video card and an 17" CRT monitor and it worked fine.
Then I shut down and plugged in my [Acer AL2016W]("http://www.myshopping.com.au/SP--148326_Acer_AL2016W_20_LCD_Monitor") LCD monitor and booted again with that one.

Hardy Heron USB (regular install) was able to pass all the tests I could give it and automatically configure itself and run with an excellent display in all my computers that can boot a USB.

If you just want to be able to install Ubuntu from a USB, you don't really need the 'persistence' feature. It would be quicker to follow one of these how-tos from Ubuntu Community Docs, [Installation without a CD]("https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd").
Not so many people will really feel the need to bother going through all of these complicated steps to get a USB they can use for installing Ubuntu.

I'm not sure if this how-to will be worth updating to Hardy Heron, it might be redundant.

---

### Post by a1234 on 2008-05-11
Do you know of similar guide for liveusb booting from a mac?

---

### Post by Herman on 2008-05-11
No, I believe macs are quite a bit different. I have no idea, but when I get time I'll take a look around and see if I find anything. :)

---

### Post by a1234 on 2008-05-11
> **Herman said:**
> No, I believe macs are quite a bit different. I have no idea, but when I get time I'll take a look around and see if I find anything. :)

Thanks Herman. People like you make ubuntu community proud and keep me hanging on!

---

### Post by a1234 on 2008-05-20
> **Herman said:**
> No, I believe macs are quite a bit different. I have no idea, but when I get time I'll take a look around and see if I find anything. :)
 Herman

Lookee here! 

[http://www.ryancloke.com/ubuntu-804-hardy-heron-live-usb-how-to/](http://www.ryancloke.com/ubuntu-804-hardy-heron-live-usb-how-to/)

I used his method to install Heron on one of my partition in my macbook pro. I have a persistence on my mac! My <username> is "ubuntu":)
Still can't get it to work on a usb. Any suggestion?

---

### Post by MQMike on 2009-02-23
@ Herman:
"I'm not sure if this how-to will be worth updating to Hardy Heron, it might be redundant."

With 8.04, there is the bug fix I mentioned somewhere in this thread, but I wonder if there may be more problems than that ...

Mine is for Kubuntu 8.04 (and the newer 8.04.2 announced 2-21-09--new download), and uses a GRUB menu and menu.lst like that of Techno-Cowboy in his first post of this thread.

I've tried for two weeks on and off, starting from scratch with super-clean flash drives, lately using the new 8.04.2 .  All sorts of problems.  E.g., Adept crashing, not installing packages.

But main issue is with this:

kio-media Kdialog
Will not save configuration
file “/home/ubuntu/.kde/share/config/kdeglobals” not writable.  (and other related messages, cannot write to kwinrc, konquerorrc, kickerrc, and a whole list)

I checked it and owner:group is ubuntu, BUT no one has any permissions: ---  ---  ---, not even ubuntu.  I tried changing ownership/permissions in all possible permutations (using fresh flash drives), no luck, some changes made things even worse (cannot log in, cannot start the desktop, etc.).

I wonder if anyone else has encountered such either with Ubuntu or with Kubuntu.  Basically, I have been unable to get a fully functioning live persistent 8.04/8.04.2 flash drive as yet.

I had no issues with 7.10.  I briefly tried 8.10 and it seemed to go ok but I didn't extensively see how it held up.

Question right now is about 8.04.

Thanks.

---

### Post by Herman on 2009-02-23
:D Hi MQMike!

I have a 'persistent' style installation of Ubuntu 8.10, 'Intrepid Ibex', I made it to try  out the new automatic method for making a persistent installation in a USB that Intrepid Ibex features. [http://www.ubuntu.com/news/ubuntu-8.10-desktop](http://www.ubuntu.com/news/ubuntu-8.10-desktop).

I hadn't used it very much until a few days ago when someone brought me a Windows computer which was, (like all Windows computers), badly infected with all kinds of viruses and malware.
I decided I would install AVG in my Ubuntu flash memory stick with the help of this excellent how-to, [HOWTO: Install AVG free anti-virus]("http://ubuntuforums.org/showthread.php?t=136064&highlight=avg") by artificial intelligence to scan the Windows computer to find out what viruses were there. 
I found it impossible to get AVG to update, it complained I didn't have permission to do that, and a virus scanner is no good if it can't get any updates. I ran out of time and never did solve the problem.
We re-installed Windows anyway in the problem computer and installed Ubuntu Hardy Heron as well, so the owner can avoid getting more viruses in the future by avoiding using Windows except for when he needs to use MYOB accounting software for his business. 
It would have been nice to know what was wrong with it before re-installing though. I like to be able to show people evidence of why a computer part needs to be replaced, or how I know it's infected with viruses, even when their own antivirus doesn't detect anything.
I am fairly certain the free AVG virus scanner would have worked perfectly without a hitch if I was using a regular installation instead of a 'persistent' type of USB install.

I will re-install the USB according to this how-to,  [How to install ubuntu on USB drive and carry entire computing system in pocket?]("http://ubuntuforums.org/showthread.php?t=789528") so I'll have a normal type of installation, and with the ReiserFS with journaling turned off, (for a little extra speed), ready for next time I need to work on someone's computer.

The advantages of the 'persistent' type of USB install are that we can use it for installing Ubuntu and  they reduce wear on the flash memory, if you believe that could be a problem.

Regards, Herman :D

---

### Post by MQMike on 2009-02-23
Good to hear from you Herman! :)

Thanks for your input.  Seems you've gone to a regular installation (on the flash drive) instead of live-persistent.  That makes sense to me, and I've done several distros that way, too.

Only thing is--as you noted in your link--it may take quite some time for a regular install to boot up fully, and I've noticed the same thing, sometimes with blinking "-" in upper left corner for some minutes and then POP! -- up comes some recognizable graphics.

Of course, as we all know, Puppy is notable for its fast, crisp click-and-get live USB performance (and has improved steadily this past couple releases), but usually not so with the heavier distros.

Again, good to hear from you, and thanks for the thoughts.

--Mike

---

### Post by Herman on 2009-02-25
I have tried Ubuntu out using a variety of mid-range USB flash memory devices and I found a big difference in the behaviours of the flash memory between brands. Generally though, in my computers at least, Ubuntu runs about the same from a USB flash memory as it does in a hard disk.

I found out that it is important to use Reiserfs, not ext3. The fact that Reiserfs is ten to fifteen times faster than ext3 for small files (and operating systems contain a lot of small files), seems to make a big difference when installing and running an OS in flash memory, even more than bench testing software suggests. Results vary between brands and models of flash devices. Using reiserfs makes up for the slower disc writes to the flash memory. 
I'm looking forward to ext4, when that comes out I'm hoping it will be even better than Reiserfs.

It is true that Ubuntu seems to take longer to boot for the first time when it is moved to a computer with different hardware, I guess the Xserver is probably resetting itself.

Another time I experienced slow booting, with a flashing cursor in the upper left-hand corner has been after it has been running my laptop, and the laptop has run out of batteries for one reason or another, so it has had an improper shutdown. 
Sometimes after that nothing happens even after repeated attempts to boot or mount the flash, and it would make most people think that the flash memory is worn out or dead and probably throw it away.
However, I have found that it pays not to give up and if repeated attempts are made to get GParted to detect it, or just if it's allowed enough time, I'm not really sure, eventually it rights itself and 'comes good' again. This has happened to me a few times. My guess it that what has happened was that the fake file system in the flash memory that controls the wear levelling might have been getting out of order and then repairing itself. None of my flash memory sticks have worn out yet, and I have an EeePC that runs 24/7 too.

If your flash memory takes longer to boot Ubuntu it might be that you have a better quality flash memory than I have and there's more going on in the background, (maybe it has fancier wear levelling strategy built into the flash disc's firmware?

When USB3 hits the market next year some time, maybe around the same time as GRUB2 and ext4 comes out, then USB flash memory drives might start to overtake hard drives in performance and we may see external USB SSD's becoming a popular item, (I'm only guessing).

Regards, Herman :)

---

### Post by MQMike on 2009-02-27
Thanks for sharing your experinece with use of live-persistent UFDs versus "full, regular" installs, Herman.

No question that a regular, full(HDD-type)install of the OS to a flash drive seems to work normally.  The sacrifice is portability:  a regular, full install may not work on another PC, but only on the PC on which it was built.  As for updates, I haven't tried it on a regular, full HD install (to UFD), but it should work normally, I would think.

As for the ability to update the live-persistent flash drive (update the packages and/or kernel) --  Lots of issues there.  I'll post the following as informational for people interested/stuck on this aspect ...

Interesting exchange of experience/discussion here:

Bug Report:
MASTER update-initramfs is disabled since running on a live CD but it is running from a flash drive.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/292159](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/292159)


--Mike

---

### Post by Andreiz on 2009-04-25
thanks for this wonderfull tutorial, just what i needed :P

---

