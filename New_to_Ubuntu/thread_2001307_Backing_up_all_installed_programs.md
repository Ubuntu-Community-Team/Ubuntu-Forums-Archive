---
title: "Backing up all installed programs"
date: 2012-06-10
forum: New to Ubuntu
---

### Post by tempore on 2012-06-10
Can I make a backup of all my installed programs and settings by copying /bin /etc /home /lib /sbin /usr somewhere and if I have to reinstall just copying it back?

I've spent a lot of time customizing my system and would like an easy way to get it back if needed.

EDIT:

OneConf looks like it would do what I want but I can't find a way to use it to make a local list, only on the cloud.

---

### Post by lindsay7 on 2012-06-10
Take a look at Clonezilla. And Remastersys.

---

### Post by oldfred on 2012-06-10
The user configuration files are in /home. If you made any system changes they may be in /etc. You can export a list of installed applications to redownload if download speed is not an issue. 

A full image backup is ok, but as soon as you have any changes then the image is out of date.  I prefer to regularly rsync /home, settings in /etc, some configuration data and a list of installed applications.

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

Oldfred's list of stuff to backup May 2011 - not changed much since:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

