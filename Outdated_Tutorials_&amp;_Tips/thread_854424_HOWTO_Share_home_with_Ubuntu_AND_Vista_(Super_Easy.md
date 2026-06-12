---
title: "HOWTO: Share /home with Ubuntu AND Vista (Super Easy!)"
date: 2008-07-09
forum: Outdated Tutorials &amp; Tips
---

### Post by mrumble on 2008-07-09
Hi all... this is my first time posting here, so I apologize if I make any mistakes (but I understand there will be hundreds of people to point out if I do). First disclaimer: I'm a n00b. Migrated to Ubuntu because I don't like MS, but still in that category of people that tend to accidently re-format their hard drive from time to time.

I have a triple boot (Ubuntu/Vista/XP) and still need to periodically use Vista from time to time. I found this way to make /home and C:\Users\Mike the SAME directory.
[B][SIZE="3"]
1) Move /Home in Linux to it's own partition[/SIZE][/B]
I followed [this]("http://ubuntuforums.org/showthread.php?t=46866") guide ([http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)) to move /home to it's own partition (single hard drive laptop)

**I used EXT2 instead of EXT3... mostly because I don't know a lot about the file systems and the Windows driver I'm using seemed to be more compatible with EXT2**

**Oh, and I first tried FAT32 (because I knew it was natively supported by Windows... didn't work. FAT32 doesn't recognize file permissions**

**One last thing... when I do the CTRL+ALT+F1, my screen dies and I have to use ALT-F7 to bring it back to life. Don't know what's wrong, but rather than try to fix it, I booted into the Ubuntu recovery mode, selected the terminal and used the login command to login to my Ubuntu.**

[INDENT]MOVING THE HOME DIRECTORY

If we have a free disk or a partition to play around with a good choice is to make a separate /home partition. By having a separate /home partition we don't have to worry that much about our files and folders anymore If everything breaks down and we get to the point of an upgrade or a reinstall, we can do so and just leave our files where they are.

This is what we do:
[B]
1.) Creating the filesystem[/B]

Use fdisk or any partitioner you feel comfortable with (Preferably not Windows fdisk), and create a partition or format your drive to a Linux filesystem. Ext3 is good, some prefer ReiserFS or other, but this is your own choice. If you don't know the difference, choose Ext3.
Note: More information about mounting and partitioning disks in linux:
[http://wiki.linuxquestions.org/wiki/...new_hard_drive](http://wiki.linuxquestions.org/wiki/...new_hard_drive)


[B]2.) Moving the /home
[/B]
First we need to log out of gnome. At the GDM (Gnome Login Screen) press:
Ctrl+Alt+F1

Then Login as your user and type (Without the #):
# sudo -s
To permanently become root.


# mkdir /mnt/home
# mount -t ext3 /dev/hda5 /mnt/home
Note: In this case I use hda5, which is my second aprtition on my first hard drive, this needs to be changed to your correct partition number. Also when I mount the partition I tell the command which type of filesystem I'm mounting (Ext3). this also needs to be changed to the correct file system of your choice.

Then we need to copy all the files from your /home directory, this may take a while since you probably have a lot of documents to move

NOTE: dradul suggest to use rsync -aS instead of cp -a
[http://ubuntuforums.org/showpost.php...5&postcount=25](http://ubuntuforums.org/showpost.php...5&postcount=25)

# cp -a /home/* /mnt/home

now we have to edit the /etc/fstab to point the direction to the new home drive


Understanding the fstab

/etc/fstab is the configuration document that tells Ubuntu where to find your disks.
Next you need to understand the disk structure. If you have one hard drive, that will most likely be named hda, if you have a slave hard drive to, that will most likely be named hdb. Your cd-rom will be hdc. If you partition your disk, hda will turn into hda1, hda2, hda5 and so on, the number is individual depending how your disk is partitioned.
Ex.: /dev/hda1 ...means: dev = the devise directory. Your devise information is stored in the"/dev

# pico /etc/fstab
Will bring up something like this in the Pico Text Editor:

#-------------------------------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda6 none swap sw 0 0
/dev/hda5 /home ext3 defaults,errors=remount-ro 0 1
/dev/hdb1 /mnt/sys2 ext3 defaults,errors=remount-ro 0 1
/dev/hdc /media/cdrom0 udf,iso9660 ro,user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/.iso/ubuntu-5.04-install-i386.iso /mnt/iso iso9660 ro,loop,auto 0 0
#---------------------------------------------------------------------------------------------------------

Note: We need to ad a line like this, again changing the (ext3) filesystem of your choice and the (hda5) the disk / partition you have moved your /home to.

/dev/hda5 /home ext3 defaults,errors=remount-ro 0 1

Note: I like to add this line in accordance to your disk structure like shown above

when you are done press:
Ctrl+o to overwrite your old fstab. Press Enter to confirm the overwrite and Ctrl+x to exit

Then rename the old /home, remove the mounted home dir and mount the new /home by:

# mv /home /homeOLD
# mkdir /home
# umount /mnt/home
# mount -a



[B]3.) Check that all your files and configuration is correct in your new /home.
[/B]
Log in and see that everything is as it should, and if it is we are now ready to delete your old home directory.

Open a terminal window and type (Without the $):
$ sudo rm -rf /homeOLD
[/INDENT]
[B][SIZE="3"]
2) Install EXT2 Drive in Windows[/SIZE][/B]

Boot into Vista and install the EXT2 driver found [here: www.fs-driver.org/]("www.fs-driver.org/")

It will prompt you with all the partitions of your hard drive. I chose to name common home drive the m: drive
[B][SIZE="3"]
3) Move /User data to /home partition[/SIZE][/B]

Edited from [this (http://blogs.zdnet.com/Bott/?p=215) guide]("http://blogs.zdnet.com/Bott/?p=215"), you can tell Vista to change where it stores your /Music /Documents /Videos, etc. etc. etc.... all of your \Users files and folders.

[INDENT]Moving your user data folders is ridiculously easy. The instructions below assume you have added a second drive using the letter E:.

   1. Click Start, Computer, and double-click the icon for your data drive (M:, in this example).
   2. Select the folder of your Ubuntu user name (mike, in this example). Double-click this folder to open it in the current window.
   3. Click Start and then click your user name (at the top of the right column on the Start menu). This opens a second Explorer window containing your data folders.
   4. Press Ctrl+A to select all folders. Point to any selected folder, hold down the right mouse button, and drag to the folder you opened in Step 2.
   5. Release the mouse button. Windows displays a shortcut menu asking whether you want to move or copy the selected items. Choose Move Here.
[/INDENT]

I had to go back in and manually move a few other files because of Vista saved data (like when you rotate a picture) and then I had to fix the common /Desktop directory so it wasn't so cluttered... but now I have a common folder. No need to sync or copy files back and forth between Ubuntu and Vista.

Hope this helps someone else break free from MS!

---

