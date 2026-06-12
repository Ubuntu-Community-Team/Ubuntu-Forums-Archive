---
title: "Copying files to a SD Card - Permission denied"
date: 2013-03-05
forum: New to Ubuntu
---

### Post by acimi66 on 2013-03-05
First let me say I am VERY new to linux and may well be in over my head.

I am unable to copy the iso OR any of the extracted files to the 32gb SD card. I keep getting _I don't have permission_.

I  made a back up of all the files on the card. Then used Gpart to remove  all the files in both partitions. I could not delete them any other  way.

When I went to add to the file
"basyskom-plasma-active-three-wetab-exopc-tablet-mer-release.iso"

to the SD card It said I don't have permission.

I extracted the files: **isolinux folder** which I successfully put in the "boot" folder on the SD card
BUT the  **LiveOS folder** was not given permission to add to the newly partition folder.

I have have many different ways to access system ROOT on my PC and I have tried to change the permissions on the SD card, nothing has worked. Any help would be greatly appreciated.

[ATTACH=CONFIG]239813[/ATTACH]

---

### Post by Mark_in_Hollywood on 2013-03-05
Because you are (copying) or installing, . . . anyway, you are using files that require a "superuser" permission. So using your keyboard, press and hold the "Alt" key and then tap the "F2" key. When the little window pops up, type:

gksudo nautilus

and press enter or mouse-click "Launch".

A moment later, the file manager (Nautilus) will open and then you can move files into "Boot" or is that spelled "boot". I cannot remember.

BUT more importantly, are you trying to make (build or install) a USB bootable linux? And if I may ask, what are you working on? As you said, you may be in over your head and before any damage gets done, let the Community have a look at it, please.

---

### Post by acimi66 on 2013-03-06
Hey thanks for the response
yes the gksudo nautilus worked
I got the files onto the sd card. but now it won't boot inside the Pengpod 7' tablet. It has android 4.04 and came with a bootable 32gb linux OS
DETAILS:
[TABLE="width: 218"]
[TR]
[TD="class: xl67, width: 132"]Device[/TD]
 [TD="class: xl68, width: 86"]PengPod700[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]Type[/TD]
 [TD="class: xl69"]Tablet[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]CPU[/TD]
 [TD="class: xl69"]A10[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]Android[/TD]
 [TD="class: xl70"]4.0[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]Linux[/TD]
 [TD="class: xl69"]3.0.42[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]Screen[/TD]
 [TD="class: xl69"]7”[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]Resolution[/TD]
 [TD="class: xl69"]800x480[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]Ram[/TD]
 [TD="class: xl69"]1GB[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]Rom[/TD]
 [TD="class: xl69"]8GB[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]SD[/TD]
 [TD="class: xl70"]Micro 32GB[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]USB Host*[/TD]
 [TD="class: xl70"]1[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]USB-OTG[/TD]
 [TD="class: xl70"]1[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]SATA[/TD]
 [TD="class: xl70"]No[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]Wifi[/TD]
 [TD="class: xl69"]B/G/N[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]Ethernet[/TD]
 [TD="class: xl70"]External[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]3G[/TD]
 [TD="class: xl69"]External[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]Bluetooth[/TD]
 [TD="class: xl70"]External[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]HDMI[/TD]
 [TD="class: xl70"]Yes[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]VGA[/TD]
 [TD="class: xl70"]No[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]AV[/TD]
 [TD="class: xl70"]No[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]Camera[/TD]
 [TD="class: xl70"]1.3 Front[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]Head Phone[/TD]
 [TD="class: xl70"]Yes[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]Speaker[/TD]
 [TD="class: xl70"]Yes[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]Buttons[/TD]
 [TD="class: xl70"]1[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]G-Sensor[/TD]
 [TD="class: xl70"]Yes[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]Battery[/TD]
 [TD="class: xl70"]3300[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]Size[/TD]
 [TD="class: xl70"]195x120x10[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]Weight[/TD]
 [TD="class: xl70"]375[/TD]
 [/TR]
 [TR]
 [TD="class: xl67"]Color[/TD]
 [TD="class: xl70"]Black[/TD]
 [/TR]
 [TR]
 [TD="class: xl66"]* Includes OTGport
[/TD]
 [TD="class: xl65"] [/TD]
[/TR]
[/TABLE]

I am trying to install a new OS on this tablet


This is the new file I downloaded from Plasma-active

basyskom-plasma-active-three-archos-gen9-omapfb-tablet-mer-release.tar.bz2

I extracted it and got all the usual looking sys. files which I put on the "root" partition of the SD card

The second I copied the files from the boot folder over to the "boot" partition on the sd card.
System.map-3.0.8
vmlinux-3.0.8
zlmage
initramfs.cpio.lzo

Then I tried re-booting my PP... three times no luck.

I added the old files from the original "boot" partition
boot.scr
script.bin
ulmage

That didn't work either.

I feel I'm close and suggestions?

---

### Post by Mark_in_Hollywood on 2013-03-06
I found this at PengPod

[http://pengpod.com/pengwiki/index.php?title=Automatically_install_Linaro_to_internal_flash](http://pengpod.com/pengwiki/index.php?title=Automatically_install_Linaro_to_internal_flash)

I don't own your device, but from what I read, you have to make some directories if they aren't already on the sd card. Namely:

Also create a /mnt/int directory 'mkdir /mnt/int' on the bootable sd.

to create a sub-directory, you would, in a terminal type:

sudo mkdir /mnt/int

if that doesn't work, then

sudo mkdir /mnt

and then

cd /mnt

sudo mkdir /int

get back to me once this first, small step is completed. Operating systems (in Linux, Android and Unix) are owned by **root**. You can be **root**, but you must use the sudo command to make directories, files, and similar in any part of **root**.  Using the command

sudo

(which stands for superuser do), allows you to be **root**.

You also must put the following files on the sd card:

pengflash
ubootenv.img
pengpod.img
desc.txt
fdisk_commands.cmd

if you don't see the 5 above, we will have a little more work to do.

---

### Post by acimi66 on 2013-03-06
Hey Mark,
Yep, as far as I can tell, all that went well.
The boot partition on the SD card has:
script.bin
ulmage
boot.scr
folder mnt > folder int

And I added those files to the root partition onthe SD card:
pengflash
ubootenv.img
fdisk_commands.cmd
desc.txt

Just to get things straight I only want to install Plasma- active on the SD card and not to over the andriod OS on the internal disk.

Thanks so much for your help

---

### Post by acimi66 on 2013-03-06
UPDATE - So one of the guys at the pengpod forums say that plasma-active OS will not work on this device. 

I guess I was hoping to simply download an image and have it boot onto the tablet. Alittle naive I guess.

Thanks for your help. Thats what I love about the linux community.

---

