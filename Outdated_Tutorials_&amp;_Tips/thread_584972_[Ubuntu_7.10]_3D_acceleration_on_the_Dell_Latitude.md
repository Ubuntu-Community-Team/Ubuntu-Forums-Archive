---
title: "[Ubuntu 7.10] 3D acceleration on the Dell Latitude D600 (Radeon Mobility OSS driver)"
date: 2007-10-21
forum: Outdated Tutorials &amp; Tips
---

### Post by laughingLoki on 2007-10-21
(Last updated on 2007.10.30)

[SIZE="5"]Credit[/SIZE]

Complete credit for this goes to Hjalmer.  His post on the matter is _[here](http://www.hjalmer.com/journal/archives/2007/08/ubuntu_gutsy_gi.html)_.  I just automated the process with a script.


[SIZE="5"]Testing[/SIZE]

This has been tested on a Dell Latitude D600 (32 bit) with Ubuntu 7.10.  The D600 has an ATI Radeon Mobility 9000 integrated graphics card.  This script may work for other laptops with the same or similar cards, but they have not been tested.  Use this script on other configurations at your own discretion.


[SIZE="5"]Details[/SIZE]

This script replaces the following files to get 3D acceleration working with the OSS Radeon Mobility driver (the one Ubuntu 7.10 uses by default for the D600):
```
 
/etc/X11/xorg.conf
/etc/modules
/etc/drirc

```

For details on why each file is modified, _[please see the source information here](http://www.hjalmer.com/journal/archives/2007/08/ubuntu_gutsy_gi.html)_.

Backups are made of each of your original versions of the files.  The backups are timestamped (.backup_$date_$time) for your convenience.  If your system gets nuked, replace the above files with their backups.


[SIZE="5"]Requirements[/SIZE]

There aren't any special requirements, really.  Just extract the attached archive and run the installation script: 
```

 sudo ./install.sh

```

You may need to chmod the script so it's runnable, though:
```

chmod a+x install.sh

```

[SIZE="5"]Undoing the script[/SIZE]
Replace the changed files with the backups that the script automatically made.  This will restore your system to how it was before running the script.  You'll do something like this:

```

sudo cp /etc/X11/xorg.conf.backup_20071225_010001 /etc/X11/xorg.conf
sudo cp /etc/modules.backup_20071225_010004 /etc/modules
sudo cp /etc/drirc.backup_20071225_010007 /etc/drirc

```

[SIZE="5"]Support[/SIZE]

WARNING: I will not provide support for this guide.  If something changes, and this script is found not to be working, then someone else is more than welcome to change it, and post the replacement script in the guide.  If someone else wants to maintain this guide, they're more than welcome to it.  I'm sure a mod or admin could give them privileges to modify this post.  It's one thing to post this guide, but I don't have time to maintain it.  Sorry!

[SIZE="5"]Changelog[/SIZE]
```

2007.10.30: install_20071030.tar.gz
* Updated script so it wouldn't break X when using the D600 docking station
* Mouse options are set back to the Ubuntu default (no scroll area on pad, et cetera)
* Makes sure permissions are set properly on modified files (Fixes possible issue where X won't start after running the script)

2007.10.21: install.tar.gz
* Original script

```

---

### Post by davidw89 on 2008-10-16
What about for Hardy Heron and Intrepid Ibex?

---

