---
title: "Permissions help and Disk mounting"
date: 2014-10-21
forum: New to Ubuntu
---

### Post by Ian_Dixon on 2014-10-21
Ok so first a confession, I was playing around with things and now have an issue with permissions and drives not mounting .

Firstly, I have 4 Hard Disks, ubuntu is installed on an SSD, then I have 3 disks for data. originally I could access these disks directly under \media\Label1 , \media\Label2 etc. 

I wanted to change the labels so did that using Gparted. Then i did some other stuff and as it sits now, the 3 disks can be accessed under \Media\<User>\LabelA, \Media\<User>\LabelB. using my user logon. I can access the files and folder no problem, and I have a Samba share which is working to allow access from my windows pc to the drive


Issue 1, the disks now don't mount automatically when i reboot, I can see the disks in the file system unmounted, and clicking on them mounts. How do I change this so they mount automatically at start up?

Looking in fstab I only have my SSD listed so assume I have to edit this and enter a line for each of the other Disks?

e.g. something like

[COLOR=#333333][FONT=UbuntuMono]/dev/sdb1 /media/<User>/LabelA ext4 defaults 0 2
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono]/dev/sdc1 /media/<User>/LabelB ext4 defaults 0 2
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono]/dev/sdd1 /media/<User>/LabelC ext4 defaults 0 2[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono]
[/FONT][/COLOR]
is that correct?

Issue 2, I have set up plex media server, my media is located on one of the disks, I can see the drives listed in plex but cant see any folder below the Drive Label. I can also see \media\<User>\ in Plex on the file system but I cant see the the Drive Labels or any folders below. I have been into the folders to try to set permissions using GUI to Others set to read / write. Have gone and tried terminal to set the directory to set Sudo [COLOR=#484848][FONT=Courier New]chmod 755 Media/<User>/LabelA/plexmedia [/FONT][/COLOR]but just can't seem to get it to work. The directories and the folders are all owned by root.

How do I set a drive, directory and all the sub folders and files within those folders to be readable and executable by any user? or by my User and the Plex user?

I did have it all set up and working previously, but then I started tinkering with it!, it is probably very simple but could do with a simple pointer on how to do it.

---

### Post by TheFu on 2014-10-21
a) / is the directory separator, not \
b) IMHO, mounting things under /media is only to be used for mounts that are automatic by the system - basically for unknown disks and quick access. I'd never leave storage there that I intend to use more than once since automatic mounting can royally screw things up.  I prefer to mount my extra data partitions under /D/ - but do whatever you like.
c) If you want storage mounted without having to do something there are two methods - fstab and autofs.  In the fstab, it is better to use UUIDs than device names, since those can change, but (in theory) UUIDs will not.
d) All the permissions questions depend on the file system used by each partition. If NTFS, then only the mount options can control that. chmod will not work.  If any Linux file system is used (there are 20+ of those) like EXT4, EXT3, BTRFS, jfs, xfs, zfs, reiserfs, .... then just use chmod.  If the disks will never be connected to Windows, please format with Linux file systems. Things work better that way and if you need to allow Windows systems access you can easily share over the network with samba. **Don't use NTFS, unless there is no other choice.**

If you don't understand the permissions, might I suggest that skimming a Linux book on CLI/shell interfaces will save you days, weeks of wondering about this stuff?  No need to memorize anything - just learn where the answers are in the book and some of the terms, so that later, when you need it, you have the vocabulary. I am really trying to be helpful, not snooty.  There is a great free PDF book here: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) - no hassle download.

So - lots of things above are my opinion. Others will have different opinions and hopefully they will share so you can make the best decision for your needs.

---

### Post by Ian_Dixon on 2014-10-21
Thanks for the reply, I guess the main issue I have is that this is my first linux box after decades of Windows based machines, i am happy with a command line but when i look for something like mounting drives or permission there is too much information! The link to the book already proving very useful

---

### Post by TheFu on 2014-10-21
Might be good to start with [http://blog.jdpfu.com/Lin_4_Win_Users](http://blog.jdpfu.com/Lin_4_Win_Users) to get acclimated and de-MSFT-brain-ified.  Things that look similar ARE NOT 80% of the time.  BTW - you can use / on Windows too - it works.

The great thing about UNIX/Linux is how flexible it is.
The terrible thing about UNIX/Linux is how flexible it is.

There are many different ways to mount storage, depending on what you want to accomplish. Generally, using the fstab is the way, but even that has options for using devices, UUIDs, labels, device-paths, .... scary to someone new - each has a specific purpose and solves a problem that some people had, but not that everyone has.  Flexible.

You can mount storage almost anywhere. The only requirement is a directory to be used as a mount point. The OS will let you do dumb things - like mount new storage over existing files/directories. Somethings that is desired - but not 99% of the time. Still, it is a feature.

Glad that book is helpful. Using it to get the background and organized introduction should save days, weeks, months of frustration. The design of UNIX really is smart.  As you learn more and more, it will become even clearer how smart those first guys were. It makes the design of other OSes seem ... er ...

Learn the shell/CLI and that knowledge will work today, next week, next year, in 20 yrs ... Learn a GUI and that works for 6 months to 2 yrs.  I'm using the same shell scripts and CLI commands from 1994 today.  Actually, I can use the same GUI too - fvwm, but that isn't the default. I still use fvwm from time to time to show people how there really isn't anything new in all this time.  We had opaque windows back then, buttons, applets, ...

---

