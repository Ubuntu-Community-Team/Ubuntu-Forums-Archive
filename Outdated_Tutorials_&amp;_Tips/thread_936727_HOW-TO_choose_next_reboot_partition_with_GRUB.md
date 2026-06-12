---
title: "HOW-TO choose next reboot partition with GRUB"
date: 2008-10-03
forum: Outdated Tutorials &amp; Tips
---

### Post by plh on 2008-10-03
Hi grub users,
I've been looking for a way to choose next boot partition before shutting down, in order to avoid being stuck to my PC during reboot process.

I found something interesting [here]("http://ubuntuforums.org/showpost.php?p=1786749&postcount=9") (many thanks to knn), tried it and it worked for me.

Nevertheless, it lacked some handy tool to automate the process, so I wrote a script to do that. Basically, what you need is the following:

1- Edit your /boot/grub/menu.lst
 a) set the "default" entry value to "saved" (it's near the beginning of the file)
 b) add the word "savedefault" to the partition you want to be the default booted partition. My advice is to make it the first partition entry in the file (the default situation, BTW), having number "0"
 c) add "savedefault 0" to all other partition entries in the file

Have a look at two of my own partition entries:

[FONT="Courier New"]title		linux
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=af74a95f-e4db-4b68-b717-971e69b9cb5a ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
quiet

title		windows
root		(hd0,1)
savedefault 0
makeactive
chainloader	+1[/FONT]


2- Let ordinary user invoke the   grub-set-default command by editing the /etc/sudoers file, using the visudo command, and adding the following line:
ALL ALL=NOPASSWD: /usr/sbin/grub-set-default 

3- copy this script to a directory listed in your PATH:
[FONT="Courier New"]#!/bin/bash
######################################################################
#
# $Id: template 919 2006-12-07 09:24:26Z phil $
# next boot will be partition <parameter> (default 3, Windows)
#
# for this script to work, 
# 1 - default saved in menu.lst
# 2 - all entries but the default one: savedefault 0
# 3 - default entry: savedefault
# 4 - /etc/sudoers: (cmd visudo) ALL ALL=NOPASSWD: /usr/sbin/grub-set-default 
# 
######################################################################

awk '$1 == "title" { printf "%d: %s\n",n++,$2}' /boot/grub/menu.lst
read ans
sudo grub-set-default $ans

######################################################################
[/FONT]

When you run the script, the list of bootable partitions appears with their corresponding entry number; all you have to do is enter the number you want, and next time you'll boot this partition! Of course default value comes back the boot after...

Hope it helps ;-)

---

