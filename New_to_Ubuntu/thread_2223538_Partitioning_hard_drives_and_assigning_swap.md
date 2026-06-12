---
title: "Partitioning hard drives and assigning swap"
date: 2014-05-11
forum: New to Ubuntu
---

### Post by Dizkazter on 2014-05-11
Hi there

I've been getting to grips with all this stuff in the past week with very little prior computing experience. I started off with a laptop running windows 7 and have managed to set up a dual boot with ubuntu, however I don't think I configured my hard drive partitions correctly for what I want to do. I deleted the system partition in order to make way for logical paritions. I then shrank the C volume to make room. I created a small 20Gb partition on which I installed Ubuntu. I then left half the remaining room for the C drive running windows, and the remainder I intended to use as storage space for both operating systems.

When I installed Ubuntu the first time it didn't quite work and the installation didn't start succesfully, however during that botched instalation I think I may have assigned my intended storage partition as swap space, which I now realise was the wrong thing to do. Shall I delete this partition and create two in it's place? One small one for swap, and the remainder as storage? How can I assign each of these into the right file format and get each OS to recognise them? At the moment Ubuntu will not mount the storage volume (which may be currently recognised as swap).

Here is a screenshot of what the partitions currently look like. The highlighted partition is the one I want to use as storage:

[IMG]http://s27.postimg.org/3sjxi142q/Partitions.jpg[/IMG]

I'm a real beginner with this stuff so any instructions would need to be a real walkthrough, or a link to any guides that do that. Ubuntu works just fine if it's easier for me to boot into that instead of windows.

Many thanks for your help,
Diz

---

### Post by jensmaucher on 2014-05-11
There is no screenshot ...

---

### Post by Dizkazter on 2014-05-11
That's funny, I can see it on my screen. Here is the link:

[http://s27.postimg.org/3sjxi142q/Partitions.jpg](http://s27.postimg.org/3sjxi142q/Partitions.jpg)

I've currently got it open in Gparted, but can't figure out how to paste screenshots to libeoffice image!

---

### Post by Zavation on 2014-05-11
Hi Dizkazter 					 						[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1923186"),

In the past I've always found it easier ( for example) to have a 400GB Partition for Windows C:, then just create a non-partitioned space then when you boot up into the Live Enviroment, select use all free space.

The other way, is to have your 400GB for windows, and create a non-paritioned space for Ubuntu (250GB), then when in the live installer, select "Advanced Partition Manager" then create the partitions manually on the 250GB partition that you created. You can create your system in a few different ways. You could have a root (meaning your home folder and root system files are on the same partition) & swap parition, or you could have a Root, Home (then your home & root are on completely differnt partitions), Swap paritions, it all depends on what you need to do. 

After you have done this, it should ask you which device you want to put the GRUB boot loader on, just select the HDD it's self, so /dev/sda <-- This can change depending on how many hard drives you have etc..

Please remember that doing this kind of thing, there is no guarantees that your data is safe, so just make sure that you have backups. So if you were to accidently delete your Windows partition or mess up the MBR you would be safe.

---

### Post by JeQhdMD on 2014-05-11
One way to get screenshots onto a forum is thru a 3rd party graphics website such as "Imgur".

What's done is:

>Image is saved as png or jpeg to a standard folder in your home drive
>Image is uploaded to your registered page at Imgur (or similar site).  note, you have to register first with the site and setup an account (which is free at Imgur ATT).
>You navigate to your image page at Imgur, then select the image you want to display on a web forum or other web site presence.
>You copy the code provided on this image page that is designated for "web forums" or wording similar to this (there are usually 4-6 options for code appropriate for your intended website type)
>Typically, the last step is to paste the code into your message on the forum webpage, where it will display your image.

Note to users or mods:   IF the process at Ubuntu Forums is different from above, please advise original poster and/or correct steps I've listed.   Thanks.

---

### Post by oldfred on 2014-05-11
Forums also supports screen shots. You use Advanced editor and in edit panel at top click on paperclip icon. You then open a Windows into your system to upload a screen shot or larger text file.

 Guide to Forum features:
[http://ubuntuforums.org/showthread.php?t=2054969](http://ubuntuforums.org/showthread.php?t=2054969)
[http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656)
Forum do & don't
[http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)

---

### Post by mansonfan78 on 2014-05-11
In gparted, assuming there is nothing on the 250gb partition, delete the partition and create two new ones in it's place.  The first one should be formatted as swap - if you plan to hibernate your pc it needs to be at least the same size as your ram, if you don't hibernate 2-4 gb would be more than enough (linux rarely uses virtual memory).  The other partition needs to be ntfs if you want to share it between windows and linux.  Ubuntu should automatically mount ntfs partitions, although you may need to install ntfs-config tool (search for it in the software manager) to set write access.

---

### Post by MrSteve on 2014-05-11
my 500GB hybrid HDD is set thus
20GB / (root)
2GB /swap
rest of drive /home

a very simple set-up ...

---

### Post by LastDino on 2014-05-11
I don't see ''swap'' label on that drive, in either case; you can easily just format it to NTFS after breaking away amount equal to your RAM, then assign it as swap. 

Mind you; doing this wont automatically tell your OS to mount this new swap partition during boot process. You might need to change few things in file called ''Fstab'', unless of course, ''swapon'' command works. 

Some one better should help you on that.

---

### Post by Dizkazter on 2014-05-15
Thankyou for all the help. I decided to delete the 250Gb partition. Gparted wouldn't allow me to do it, so I booted in windows and used partition wizard. I then tried to boot into Ubuntu but found that I can no longer get the Grub menu. Instead it takes me to Grub rescue, which as far as I can tell does nothing.

I booted a live session of Ubuntu from my USB stick and used Gparted to create two partitions in the unallocated space created by deleting that partition, one 10Gb logical partition assigned as 'Linux-swap' and the remainder as one big NTFS partition that I labelled storage.

However it seems the OS still doesn't recognise the new swap space, so Grub still won't work. Is there a way I can fix this? If there isn't a quick way to repair Grub then I guess I will just re-install Ubuntu from my USB stick and use the correct place for swap now that I have my partitions set up correctly.

One other minor thing - there is a 2Gb unallocated space between my C drive and the newly created storage partition that wasn't there before. I can't extend storage into it. Any ideas why that has happened?

---

### Post by LastDino on 2014-05-15
You don't need 10 GB swap. You can repair Grub from that same Live USB you've, but I'll wait for someone else to let them explain as I've never done it myself.  As far as that unallocated space is concerned, I suspect that it is there because you got little careless with Gparted while making those 2 new partitions, you need to check the numbers before hitting ok, often we forget to put numbers in right place and top column ends up having something other than 0.

---

### Post by Dizkazter on 2014-05-15
The unallocated space gap is between the C drive (windows) and the storage partition. Even if I was careless with Gparted and didn't allow storage to take up all the available space, shouldn't I still be able to extend it now?

---

### Post by oldfred on 2014-05-15
Do not use Windows own partition tools to delete or add partition, just to shrink the Windows NTFS partition. 
Windows does not correctly see Linux partitions and often just does not write them back into partition table. Third party Windows tools may work but gparted is preferred.
You cannot edit partitions from a working install. You have to use your live installer.

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

      
 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by mansonfan78 on 2014-05-15
The unallocated space is often unavoidable, it's just the way the partitions are aligned to the blocks.  The larger the hard drive, the larger the unallocated space.  You'll always have some, although 2 gb does seem rather large.
If you need to reinstall grub, load the live cd and open a terminal.  You'll need to know the partition Ubuntu is installed on (sda2, sdb1 - whatever).  For example if it's sda3 you would type (without the quotes) "sudo mount /dev/sda3 /mnt" and hit enter.  Then you would type "sudo grub-install --root-directory=/mnt /dev/sda"  (NOT sda3, just sda).  Finally, type "sudo umount /mnt".  Reboot.

---

