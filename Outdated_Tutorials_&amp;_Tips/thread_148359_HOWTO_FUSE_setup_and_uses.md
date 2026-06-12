---
title: "HOWTO: FUSE setup and uses"
date: 2006-03-21
forum: Outdated Tutorials &amp; Tips
---

### Post by tuxcantfly on 2006-03-21
Fuse is used by several filesystem drivers, such as ntfs-fuse (howto at [http://www.ubuntuforums.org/showthread.php?t=142481](http://www.ubuntuforums.org/showthread.php?t=142481)) and gmailfs (howto at [http://www.ubuntuforums.org/showthread.php?t=139872)](http://www.ubuntuforums.org/showthread.php?t=139872)). However, several older kernels do not include fuse support. This howto covers building the fuse module and installing the utilities for breezy, hoary, and warty (dapper users skip to step 5).
1. Open a terminal, which is either in the System Tools menu or the Accessories menu. Type:
**sudo gedit /etc/apt/sources.list**
Add the line:
*deb [ftp://ftp.ubuntu.com/ubuntu](ftp://ftp.ubuntu.com/ubuntu) dapper main restricted universe*
Now save, and exit gedit.
2. Then, type:
**sudo apt-get update**
Which will reload the repositories.
3. Now type:
**sudo apt-get install module-assistant fuse-utils python-fuse**
Which installs necessary utilities.
4. Once done, type:
**sudo module-assistant**
Highlight &#8220;prepare&#8221; and press enter. Afterwards, highlight &#8220;select&#8221; and press enter, find fuse, select it with space, and hit enter, highlight &#8220;build&#8221;, press enter, and continue pressing enter when it asks &#8220;The source package may not be installed. Would you like to install or upgrade selected source packages now?&#8221; and &#8220;Would you like to install the created module package(s) now?&#8221;. Now exit module-assistant.
5. Type:
**sudo modprobe fuse**
And if you don't get any error messages, fuse works.
6. To load it on boot, type:
**sudo gedit /etc/modules**
Add this line at the end:
*fuse*
Now save, and exit.
7. (optional) If you are using nautilus or konqueror as your file manager, it is recommended to install thunar:
**sudo apt-get install thunar**
Which works better with many fuse filesystems, especially gmailfs.
8. You can now proceed to installing gmailfs (howto at [http://www.ubuntuforums.org/showthread.php?t=139872)](http://www.ubuntuforums.org/showthread.php?t=139872)), which allows you to use your gmail account as online storage, or ntfs-fuse (howto at [http://www.ubuntuforums.org/showthread.php?t=142481)](http://www.ubuntuforums.org/showthread.php?t=142481)), which lets you read and write ntfs partitions, used by Windows XP, 2000, and NT.

---

### Post by tuxcantfly on 2006-03-21
Fuse is used by several filesystem drivers, such as ntfs-fuse (howto at [http://www.ubuntuforums.org/showthread.php?t=142481](http://www.ubuntuforums.org/showthread.php?t=142481)) and gmailfs (howto at [http://www.ubuntuforums.org/showthread.php?t=139872)](http://www.ubuntuforums.org/showthread.php?t=139872)). However, several older kernels do not include fuse support. This howto covers building the fuse module and installing the utilities for breezy, hoary, and warty (dapper users skip to step 5).
1. Open a terminal, which is either in the System Tools menu or the Accessories menu. Type:
**sudo gedit /etc/apt/sources.list**
Add the line:
*deb [ftp://ftp.ubuntu.com/ubuntu](ftp://ftp.ubuntu.com/ubuntu) dapper main restricted universe*
Now save, and exit gedit.
2. Then, type:
**sudo apt-get update**
Which will reload the repositories.
3. Now type:
**sudo apt-get install module-assistant fuse-utils libfuse2**
Which installs necessary utilities.
4. Once done, type:
**sudo module-assistant**
Highlight “prepare” and press enter. Afterwards, highlight “select” and press enter, find fuse, select it with space, and hit enter, highlight “build”, press enter, and continue pressing enter when it asks “The source package may not be installed. Would you like to install or upgrade selected source packages now?” and “Would you like to install the created module package(s) now?”. Now exit module-assistant.
5. Type:
**sudo modprobe fuse**
And if you don't get any error messages, fuse works.
6. To load it on boot, type:
**sudo gedit /etc/modules**
Add this line at the end:
*fuse*
Now save, and exit.
7. (optional) If you are using nautilus or konqueror as your file manager, it is recommended to install thunar:
**sudo apt-get install thunar**
Which works better with many fuse filesystems, especially gmailfs.
8. You can now proceed to installing gmailfs (howto at [http://www.ubuntuforums.org/showthread.php?t=139872)](http://www.ubuntuforums.org/showthread.php?t=139872)), which allows you to use your gmail account as online storage, or ntfs-fuse (howto at [http://www.ubuntuforums.org/showthread.php?t=142481)](http://www.ubuntuforums.org/showthread.php?t=142481)), which lets you read and write ntfs partitions, used by Windows XP, 2000, and NT.

---

