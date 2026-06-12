---
title: "How do you make a Backup of all your Data?"
date: 2013-11-27
forum: New to Ubuntu
---

### Post by rmcbride19 on 2013-11-27
Hello everyone...

    Im new to linux and Ubuntu. Just loaded it on a freshly formated hard drive. In the process of customization and loading all the Programs I got to wandering how I can Backup my inportant data from time to time. just in case this HD should Die, I dont want to loose all my Programs and Customizations. Can Anyone Advise of a good Backup program that I can use to make a dup of my Ubuntu Drive when I get finished?

Thanks in Advance.

---

### Post by bashiergui on 2013-11-27
Ubuntu comes with Deja-Dup installed. Here's how to use it
[http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/](http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/)

---

### Post by oldfred on 2013-11-27
discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)


 Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

I just use rsync to back up /home and some data. I have very little data in /home as data is in separate partitions. But as part of my backup process, I make sure I copy any system configuration file I manually edit that is in /etc into /home and backup a list of installed applications to make it easy to reinstall. I just plan to totally reinstall and then restore my backed up data.
My most important data also gets copied to a couple of DVDs every quarter.

Some line full image backups.
      
 Full image backups
[http://clonezilla.org/](http://clonezilla.org/)

My rsync started with this:

 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

---

### Post by sammiev on 2013-11-28
> **oldfred said:**
> discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)


 Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

I just use rsync to back up /home and some data. I have very little data in /home as data is in separate partitions. But as part of my backup process, I make sure I copy any system configuration file I manually edit that is in /etc into /home and backup a list of installed applications to make it easy to reinstall. I just plan to totally reinstall and then restore my backed up data.
My most important data also gets copied to a couple of DVDs every quarter.

Some line full image backups.
      
 Full image backups
[http://clonezilla.org/](http://clonezilla.org/)

My rsync started with this:

 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

Lots of great info here. I use clonezilla myself and likely over kill for a lot of folks but I run so many OS at a times and I like to backup to a large USB backup all at once. At least you have a lot of option to play with. :)

---

