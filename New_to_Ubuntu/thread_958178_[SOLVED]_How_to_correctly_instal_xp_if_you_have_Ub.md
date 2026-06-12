---
title: "[SOLVED] How to correctly instal xp if you have Ubuntu and spare partition."
date: 2008-10-25
forum: New to Ubuntu
---

### Post by jon555 on 2008-10-25
How to install xp on my second partition without destroying Ubuntu boot record, GRUUB or what it's called. I don't wana spent 5 hours after tiering to boot Ubuntu.

---

### Post by tuxulin on 2008-10-25
this topic has been answered a thousand times.
>  How to correctly instal xp if you have Ubuntu and spare partition.

use the search button

---

### Post by jon555 on 2008-10-25
Sorry 

I foun an answer from Catllet.

 How to restore Grub from a live Ubuntu cd.
This will restore grub if you already had grub installed but lost it to a windows install or some other occurence that erased/changed your MBR so that grub no longer appears at start up or it returns an error.

(This how to is written for Ubuntu but should work on other systems. The only thing to take note of, when you see "sudo" that will mean to you that the following command should be entered at a root terminal.)

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)

Code:

sudo grub

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)

Finally exit the grub shell
Code:

quit

That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.

Now the explanation.
Sudo grub gets you the grub shell.
Find /boot/grub/stage1 has grub locate the file stage1. What this does is tell us where grub's files are. Only a small part of grub is located on the mbr, the rest of grub is in your boot folder. Grub needs those files to run the setup. So you find the files and then you tell grub where to locate the files it will need for setup.
So root (hd?,?) tells grub it's files are on that partition.
Finally setup (hd0) tells grub to setup on hd0. When you give grub the parameter hd0 with no following value for a partition, grub will use the mbr. hd0 is the grub label for the first drive's mbr.
Quit will exit you from the grub shell.



THIS IS AN EDIT. 5-HT MADE A GOOD POINT AND I AM JUST GOING TO COPY/PASTE IT HERE

Quote:
Just have recommendation to add that may be irrelevant: it might be of benefit to give an explicit warning (though it is mentioned) that this guide will write GRUB to the MBR (just in case someone is using a different boot loader on their MBR and would like to reinstall GRUB to a partition).

If someone wants GRUB on a partition, the 'setup (hd0)' step can be modified to 'setup (hdX,Y)'. Where X is the hard disk, and Y the partition using GRUB's nomenclature of starting from 0 (first partition=0, second=1,...).
THIS IS ANOTHER EDIT. TOSK POSTED A WAY TO MOUNT PROC AND UDEV. THIS WAS NEEDED BECAUSE GRUB WASN'T RECOGNISING THE DRIVE. I THOUGHT IT WAS A VALUABLE COMMENT AND DECIDED TO PUT IT IN THE ORIGINAL POST SO PEOPLE WILL SEE IT AT THE TOP. IT MAY BE MISSED AS JUST A REPLY POST DOWN THE PAGE.
ALL KNOWLEDGE IS WELCOME!

Quote:
Mine was a slightly different story. I couldn't get grub to find the stage1 file or even recognize my drive. So I borrowed some knowledge I picked up while using Gentoo:

You have to mount your root partition using the livecd:
Code:

$
Code:

sudo mkdir /mnt/root

$
Code:

sudo mount -t ext3 /dev/sda6 /mnt/root

Then you have to mount the proc subsystem and udev inside /mnt/root also:
Code:

$
Code:

sudo mount -t proc none /mnt/root/proc

$
Code:

sudo mount -o bind /dev /mnt/root/dev

Doing this allows grub to discover your drives. Next you have to chroot:
Code:

$
Code:

sudo chroot /mnt/root /bin/bash

Now that you're chrooted into your drive as root everything should work.
Code:

#
Code:

sudo grub

I edited in the sudo, just to be safe. When I enter grub and not sudo grub, grub cannot find the file. I do not know if the chroot changes this because I did not try it that way. In the end I figured it was better to err on the side of caution. Tosk I hope you don't mind my editing of your reply.
grub>
Code:

find /boot/grub/stage1

It found mine on (hd0,5)
Code:

grub>
Code:

root (hd0,5)

It successfully scanned the partition and recognized the filesystem-type
Code:

grub>
Code:

setup (hd0)

That was it. It installed and on reboot I was thrown back into Ubuntu.

This might help some people who are having issues so I thought I would post it.

PLEASE NOTE: My Ubuntu was installed to /dev/sda6. This may not be the same for everyone. /dev/sdaX means it's SCSI/SATA/USB/FireWire drive. And it's partition 6 because I have a weird partitioning scheme in place.

--Tosk


**This set of instruction is a combination of 2 guides I saw before. One was a Mepis grub how to but I never found it again. The other is the grub manual. It's section explained the find, root, setup process but never mentioned it could be done from a live session.

This is the grub link [http://www.gnu.org/software/grub/man...-GRUB-natively](http://www.gnu.org/software/grub/man...-GRUB-natively)

Post script;
Just to post as much information as possible, this is an older how to for resoring grub to the mbr. The original post is directions for using the install cd and then there are replies that mention the method I posted here, as well as the chroot method mlind mentioned. If this method fails, you may want to try this [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)
__________________
EDGY GUIDE >Edgy Live CD install > Dapper alternate install cd >Ext2 driver>Aysiu's great ubuntu tutorials>XP to ubuntu transition guide
Last edited by catlett; September 21st, 2006 at 03:46 AM.

---

### Post by jon555 on 2008-11-24
Anyway, I got GRUB CD and now it's so easy task. Just enter, enter, up, enter and you done. Nice and easy.

---

