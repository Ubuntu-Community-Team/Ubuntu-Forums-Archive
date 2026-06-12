---
title: "HOWTO restore a backup images of XP and Ubuntu Dapper Drake Linux as a dualboot setup"
date: 2007-08-27
forum: Outdated Tutorials &amp; Tips
---

### Post by vectoravtech on 2007-08-27
Ok, I have a dual boot system so when I boot up I can choose to boot either xp or linux. What I used to image was Drive Image 2002 which was eventualy bought by Symantic and they filled it with alot more options and called it Norton Ghost, When I started this software from the 2 bootable floppys I created it repaired 2 or 3 errors so I can make the image graphicly. After restoring a linux image I booted a Dapper Drake Ubuntu live cd with safe mode because I have a Sapphire X800 Video Card. [http://davidwinter.me.uk/articles/2006/10/25/getting-ubuntu-dapper-to-dance-with-ati-x800-gto/](http://davidwinter.me.uk/articles/2006/10/25/getting-ubuntu-dapper-to-dance-with-ati-x800-gto/)   If it doesnt work:
sudo su
sudo spt-get update
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

(PS is about how I created the boot floppys.)

At any rate To perform the Inode error fix I needed to do because I saw the error popup in Dapper Drake I booted the D.D. live cd and opened the terminal and sudo su then typed this:
1) umount /dev/sda7
2) fsck.ext2 -f /dev/sda7
3) fsck.ext3 /dev/ext2
4) mkdir /mnt/sda7; mount /dev/sda7/mnt/sda7

(im testing some discrepancies in the coding to rationalize the proper architechture) If you have any Inode error fixes please post them in the forums at the end of this tutorial.

After number two it should check and repair the Inode errors.
I'm not sure if anyone cares that I found this out but I decided to spread the word anyway. It works like a charm.

Also what you need to do to repair the duplicate entrys in the grub boot menu:

Sudo su 
sudo gedit/boot/grub/menu.lst
To test first before deleteing anything the extra entrys please put a # in front of each one to make it a note then save it and reboot to test.

P.S. (Since SATA wasnt created in 2002 I had to do this)  Im using sata (serial ATA) harddrives so I after creating the repair floppys without selecting any of the drivers they provided what I did was pull my VIA chipset Sata driver from my motherboard drivers cd and create a folder on the first floppy called (Drivers) and pasted my driver in there. If you end up trying another operating system, be it windows, linux, bsd, solaris, or unix, and drive image 2002 isnt able to restore the image because it cant use that type of partition I would just use the (hirens boot cd which is free to download) to reformat that partition to what you had before when you created the xp, ubuntu partitions so its compatable with DRV. IMG. I use Acronis True Image boot cd to create a drive clone incase the install formats the whole HD. For yahoo chat I use (zinc chat) console chat client. [http://www.larvalstage.com/zinc/](http://www.larvalstage.com/zinc/) and I like to use a slight transperant term. (edit/current profile/ effects: transparent) I also like to half and half the screen with konversation which works on ubuntu gnome.

**Screenshots**

Ubuntu Partition Manager screenshot:
[http://img214.imageshack.us/my.php?image=screenshot2gc9.jpg]("http://img214.imageshack.us/my.php?image=screenshot2gc9.jpg")
(What you see thats transparent on the right side here is called Zinc which is a yahoo chat client that basicly runs from the terminal.)

XP Pro Partition Manager screenshot:
[http://i36.tinypic.com/330sidu.jpg]("http://i36.tinypic.com/330sidu.jpg")

You should save these backups in another harddrive incase it fails and you need to replace it, I did it this way just for testing.

**Heres a great tutorial I found on how to speedup dapper drake; all I used so far was the XML speedup Orvil left on the bottom of this page**

Speedup Dapper Drake Ubuntu Tutorial:
[http://ubuntuforums.org/showthread.php?t=189192]("http://ubuntuforums.org/showthread.php?t=189192")


**I**f you want to add more information about this type of setup that I didnt cover please post in Abxzone at this link: [http://www.abxzone.com/forums/f22/recovering-image-xp-pro-ubuntu-linux-111036.html#post1386227](http://www.abxzone.com/forums/f22/recovering-image-xp-pro-ubuntu-linux-111036.html#post1386227) 
Heres my original posting of this tutorial also:
[http://ubuntuforums.org/showthread.php?p=3261395#post3261395]("http://ubuntuforums.org/showthread.php?p=3261395#post3261395")

My avatar is called tropicaldreamswp.jpg from wolfmansart.net.

---

