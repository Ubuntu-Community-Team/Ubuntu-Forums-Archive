---
title: "uninstalling windows xp"
date: 2013-04-09
forum: New to Ubuntu
---

### Post by volksgewer on 2013-04-09
Hello, I am running an old computer with windows XP and I am trying to uninstall XP and just make Ubuntu the primary OS on this machine.  I am new to this and have no clue where to start.  If any one could help me out with a step by step guide or just something to get my brain going it would be greatly appreciated.

---

### Post by docJ on 2013-04-09
[URL="https://help.ubuntu.com/community/Installation"]Before you do anything, make 100% sure you know if any valuable data is on the computer on which XP is installed
Then, have a read: 
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

[/URL]

---

### Post by ppjdee on 2013-04-09
Don't forget to back up your data! Pictures, movies, etc. onto a USB flash drive or DVD or any method you prefer. Installation is pretty straight forward, follow the onscreen instructions and use a wired Ethernet connection, so updates and codecs can be downloaded during the process.

---

### Post by pfeiffep on 2013-04-09
take your time making this decision ... make a live dvd and test Ubuntu on the pc for a week or so. Try to do your daily tasks using Ubuntu to discover whether you have all the tools you'll require. Of course if this is a 'second' pc and not your primary PC make a live dvd test for an hour then install Ubuntu to replace WinXP  there really no need to uninstall Win because Ubuntu will blow it away for you!

---

### Post by mastablasta on 2013-04-10
what kidn of hardware? Ubuntu might not run well on some very old maschine. well unless you really know how to configure it. and even then.... but then again you can always try it in live session and see how it goes. 

good alternatives in UBuntu family for older hardware are Xubutnu and Lubuntu. they both have user interface that is lighter on resoruces.

data and windows will be erased during instalation & disk formatting.

---

### Post by amanchesterman on 2013-04-10
About a year ago I did what you are wanting to do: took an old XP laptop and installed Ubuntu instead. (I'm using it now.) I would strongly endorse the advice given above, i.e.:
-- make back up copies of all the files and data from the XP machine that you might at any time want in the future: store these carefully on separate media (I used CDs and a USB drive);
-- try out Ubuntu with a Live CD before you install it, to make sure that it works with your hardware: in particular, check that it's ok with the keyboard, wireless, screen display etc.

An additional piece of advice I would offer is to install Ubuntu with a separate /home partition. It's a little more work, but it has benefits in the long run. You can then put all your data files (documents, photos, music etc.) into that partition and they won't be corrupted if you have to re-install Ubuntu at a later date or (as I did) want to try out different versions of Linux.

---

### Post by gnugen on 2013-04-10
1. First, make sure that your hardware can handle Ubuntu and that the graphics card or your wifi card are supported.
2. Download the .iso for which version of ubuntu you want.[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
3. Check the md5 sum.
4. Next, burn the .iso to a cd. (or use a usb to boot) There are some links to helpful guides on the ubuntu website.
5. Configure your BIOS to boot the USB or CD.
6. Once you have booted ubuntu, click on try ubuntu and check out if everything works.
7. Double click the install icon and cick next, following the installer. 
8. When the option of install alongside XP or wipe drive and install Ubuntu, click on the wipe drive option.
9. Make sure you set up your computer name, password and everything the installer requests.
10. Restart computer and enjoy.

REMEMBER: To backup all data on the hardrive you install Ubuntu to.
WARNING: If you do not see install ubuntu alongside XP option, do not install even if there is a wipe disk option as your hard disk may be corrupt.

---

### Post by pfeiffep on 2013-04-10
+2  excellent procedure!
> [COLOR=#000000]1. First, make sure that your hardware can handle Ubuntu and that the graphics card or your wifi card are supported.[/COLOR]
[COLOR=#000000]2. Download the .iso for which version of ubuntu you want.[/COLOR][http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[COLOR=#000000]3. Check the md5 sum.[/COLOR]
[COLOR=#000000]4. Next, burn the .iso to a cd. (or use a usb to boot) There are some links to helpful guides on the ubuntu website.[/COLOR]
[COLOR=#000000]5. Configure your BIOS to boot the USB or CD.[/COLOR]
[COLOR=#000000]6. Once you have booted ubuntu, click on try ubuntu and check out if everything works.[/COLOR]
[COLOR=#000000]7. Double click the install icon and cick next, following the installer. [/COLOR]
[COLOR=#000000]8. When the option of install alongside XP or wipe drive and install Ubuntu, click on the wipe drive option.[/COLOR]
[COLOR=#000000]9. Make sure you set up your computer name, password and everything the installer requests.[/COLOR]
[COLOR=#000000]10. Restart computer and enjoy.[/COLOR]

[COLOR=#000000]REMEMBER: To backup all data on the hardrive you install Ubuntu to.[/COLOR]
[COLOR=#000000]WARNING: If you do not see install ubuntu alongside XP option, do not install even if there is a wipe disk option as your hard disk may be corrupt.[/COLOR]

---

### Post by grahammechanical on 2013-04-10
Advice is fine. How to is better. You uninstall XP by simply running the Ubuntu live Session and selecting Install Ubuntu and one of the screens will give you choices.

1) Install Ubuntu alongside existing operating system.
2) Use the entire disk
3) Do Something Else.

If you select to install Ubuntu using the entire disk then everything on the disk will be erased, including XP. That is the simple way.

It is good to have a separate /home partition but you will need to learn how to create partitions. I suggest that you read through this. Study the pictures.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Then install ubuntu using the Entire disk (if that is your decision). The installation process will create two partitions for you. One will be / and the other will be swap.

Now, Run the live session and open Gparted (It is in the Dash). That will show you the partitions. You now need to

1) Shrink the partition with Ubuntu in it. This will create Unallocated space.
2) Create another partition in the unallocated space
3) Install Ubuntu again using the Do Something Else option

At the partitioning stage 

a) Select the first partition (with Ubuntu in), Click change and give it a format of Ext4, a mount point of /, and marked for format.
b) Select the newly created and empty partition. Click change and give it a format of Ext4, a mount point of /home, and marked for format.

Continue with the install process. It will find the existing swap partition and use it.

Regards.

---

