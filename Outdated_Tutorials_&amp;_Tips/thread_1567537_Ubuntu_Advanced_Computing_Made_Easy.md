---
title: "Ubuntu Advanced Computing Made Easy"
date: 2010-09-03
forum: Outdated Tutorials &amp; Tips
---

### Post by Paresh on 2010-09-03
**[SIZE="6"]Ubuntu Advanced Computing Made Easy[/SIZE]**

Inspired by TrackerJon's [tutorial]("http://ubuntuforums.org/showthread.php?t=1469825"), I decided to make one for the more advanced user.

The tips presented here are useful for the user who is a bit more capable than the absolute beginner and while I encourage beginners to look at this I must point out that we're not simply paddling on the beaches here, we're in the deep end of the pool.  Please ask if you're unsure about anything.  Doing the wrong thing could make your system stop working.

This page is just a summary of tools I have found useful, with added links for full details.

**etckeeper**([https://help.ubuntu.com/9.04/serverguide/C/etckeeper.html]("https://help.ubuntu.com/9.04/serverguide/C/etckeeper.html"))
[FONT="Courier New"]sudo apt-get install etckeeper[/FONT]
This is a utility that will automatically record changes in the etc directory.

**rabbitvcs** ([http://www.rabbitvcs.org/]("http://www.rabbitvcs.org/"))
[FONT="Courier New"]sudo apt-get install rabbitvcs rabbitvcs-cli rabbitvcs-core rabbitvcs-gedit rabbitvcs-nautilus[/FONT]
This is a GUI front end for subversion.  It integrates into gedit and nautilus.  They will soon have it working with other version control systems (git is in currently next in line).  Note: this is not in the main repository yet, so you can add the PPA, or download the packages manually.
[B]
ecryptfs[/B] ([https://help.ubuntu.com/community/EncryptedPrivateDirectory]("https://help.ubuntu.com/community/EncryptedPrivateDirectory"))
[FONT="Courier New"]sudo apt-get install ecryptfs-utils[/FONT]
Gives you a private directory in your home folder that is mounted automatically.  You can treat it as a normal folder, but any other user won't be able to read the contents.

**zenity** ([http://library.gnome.org/users/zenity/stable/]("http://library.gnome.org/users/zenity/stable/"))
[FONT="Courier New"]sudo apt-get install zenity[/FONT]
For all you script kiddies there, you can now get pretty GUI style dialogs

**xautomation** ([http://manpages.ubuntu.com/manpages/maverick/man7/xautomation.7.html]("http://manpages.ubuntu.com/manpages/maverick/man7/xautomation.7.html"))
[FONT="Courier New"]sudo apt-get install xautomation[/FONT]
This will allow you to control X from the command line.  You can script key presses and mouse clicks, search for images within images and other useful stuff.

**meld** ([http://meld.sourceforge.net/]("http://meld.sourceforge.net/"))
[FONT="Courier New"]sudo apt-get install meld[/FONT]
This is a great file difference viewer.

**rsync** ([http://www.samba.org/rsync/]("http://www.samba.org/rsync/"))
[FONT="Courier New"]sudo apt-get install grsync rsync[/FONT]
A flexible backup utility (grsync is the gui front end with limited options)

Mounting ISO files ([http://ubuntuforums.org/showthread.php?t=704350&highlight=fuseiso]("http://ubuntuforums.org/showthread.php?t=704350&highlight=fuseiso"))
This is just a cool way of mounting your ISO file through nautilus.

Well, that's all for now, I'm open to your suggestions and comments to make this as good as TrackerJon's ([post]("http://ubuntuforums.org/showthread.php?t=1469825"))

---

