---
title: "Ubuntu data and applications directories"
date: 2014-04-01
forum: New to Ubuntu
---

### Post by Stuart_Aitchison on 2014-04-01
Is it possible to have the data and the user applications stored on a different hard drive to the one on which the actual operating system is loaded.  If so, then how?

Stuart Aitchison

---

### Post by Impavidus on 2014-04-01
In principle, yes. The user programs (that is everything not necessary to fix the system if broken) and their accompanying data (edit: program data, not user data) are stored in /usr. You can put that on a separate partition or hard drive and mount it automatically using fstab, the same way you can do it for /home. There aren't many circumstances in which it would be useful though.

Edit: See [this](https://help.ubuntu.com/community/Partitioning/Home/Moving). Instead of home you can also move most other directories in almost the same way.

---

### Post by oldfred on 2014-04-01
Yes, just about every folder in / (root) can be located anywhere. But why?
I tend to want everything on one drive, so if a drive fails I have a bootable system. And I install Ubuntu on every hard drive, so every drive is bootable.
But Linux is not like Windows where an application is just in an application folder. Parts of every program are in various folders. Your user data for every application is in /home in hidden files & folders.

 Explanation of file structure
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
[http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)
[http://en.wikipedia.org/wiki/Unix_directory_structure](http://en.wikipedia.org/wiki/Unix_directory_structure)

---

### Post by TheFu on 2014-04-01
Yes.  The '/home' is not special - in name or any other way.
Format a partition, mount it somewhere (any directory - perhaps '/h'), then mv/cp all your /home files over as root with rsync to maintain permissions, links, etc.
Update the fstab with the new folder, update any home-directory settings in /etc/passwd files (or ldap, if that is used) OR just set the mount location to /home inside the fstab.

Sorry if this seems cryptic.  For someone new to Linux, it is much easier to set this up during the install, but it really isn't all that hard once you know your way around either. During the file partitioning part of the install - choose "do something else" and make a partition with a mount point for /home - the installer knows what to do with that.  If you run virtual machines, it might be nice to mount another partition on /var/lib/libvirt too. That can get large.

The passwd file has a HOME specified for every userid. That is the only thing that needs to match wherever you choose to put the HOME for any user.  Different users can have different partitions used for HOME too.

99% of all programs look for user data based on HOME, so everything except your own custom scripts that directly access the specific old HOME location will keep working.

Oh ... almost forgot. If you do decide to mount the new partition onto /home - all the files/directories currently located there will be unreachable - mounts overlay any existing files, but do not delete them.

---

### Post by Stuart_Aitchison on 2014-04-02
Thanks for the info.  I am currently an enforced Windows "freak", it that Windows regularly freaks me out.  An acquaintance of mine recently got me to load Ubuntu 13.10 on to his machine for him alongside Windows 7, and the install went rather well (I've been in I.T. for nearly forty years).

For years now I have had the system on one drive, and my apps and data on another, and it has saved my bacon on a good handful or more of occassions, when I have had drive issues of one sort or another, so it is a practise I would like to continue.

I am currently setting up another machine for myself and I want to install Ubuntu onto it with Windows 7, and the issue of the apps and the data will make a difference to the size of hard drive I use for the system.

I would welcome any further input and information on this.

Stuart Aitchison

---

### Post by oldfred on 2014-04-02
Linux requires some different ways of doing things.
 Linux is not Windows:
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

   Ubuntu is not Windows
[http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/](http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/)
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

I now have a 64Gb SSD. I have two / (root) partitions of about 28GB, one current working 12.04 and one for 14.04 shortly. In my working install I use about 11GB of the 28GB. And since Linux is easy to reinstall (as opposed to Windows), I only backup /home and a list of installed applications, plus a few other things.

But one of my goals is always have a fully bootable system on every hard drive. But I do have data on my rotating hard drive which I separately backkup.

---

