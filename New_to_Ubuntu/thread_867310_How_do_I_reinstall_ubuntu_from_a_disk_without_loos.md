---
title: "How do I reinstall ubuntu from a disk without loosing my settings &amp; data?"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by fogelfink on 2008-07-22
It might sound a bit stupid, but I need some advice on how to reinstall ubuntu.

I have basically destroyed my ALSA by installing OSS, which didn't work for me - and after numerous attempts of fixing it, I have been told that the only way to fix it is a clean fresh install of Ubuntu.  [[http://ubuntuforums.org/showpost.php?p=5437671&postcount=292]](http://ubuntuforums.org/showpost.php?p=5437671&postcount=292])
I am coming round to that idea (I tried reinstalling a fresh kernel, which didn't help) - so now I wonder how I can do that with some sort of backup.  

I would like to install Ubuntu Studio (Hardy), but am currently using the regular Ubuntu (Hardy).  I would like to keep my personal settings such as evolution mail settings, firefox bookmarks, tomboy notes, etc.  AND of course my files in the home directory (lots of graphics and music stuff, so it's about 110GB!!).  What I don't want to back up is my screwed sound settings.

Do I make some sort of backup (if yes how?) and then create a new Ubuntu Studio partition without erasing the existing Ubuntu partition and then drag my home direcory files (graphics and music) somehow into my new home directory (if so, how?), while using the backup for the settings.  And last try to erase the old and faulty Ubuntu partition?

OR, do I have to get all my data from the home directory shifted onto an external harddrive, then make a backup of the settings and finally install Ubuntu Studio with reformatting the harddrive?  Could I then use some form of settings backup to get the data from evolution etc back into the new system, while simply shifting my home directory files back onto the internal drive?

OR, worst case scenario, do I have to reconfigure my mail accounts, address book, bookmarks, etc. because I use a different distro of ubuntu?

Your advice is appreciated.

---

### Post by Xerp on 2008-07-22
This should help:

[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)

---

### Post by mkvnmtr on 2008-07-22
I am sure someone else knows more than I do about this but last night I reinstalled 7.04 over 7.10 when the upgrade did not go well. The installer asked me if I wanted to migrate any accounts. I didn't but assume thats what you are asking about.

---

### Post by YaroMan86 on 2008-07-22
My recommended way is putting your /home on its own partition, and regularly copying key configuration files from /etc onto that same partition.

You'll retain all your documents and local user settings, and, provided you copy the /etc files back, the same system configuration.

---

### Post by sdowney717 on 2008-07-22
I have been wondering about this.
Your /home partition contains all your stuff like bookmarks etc...
Can you just copy this over and then setup a new user using this folder?

---

### Post by Xerp on 2008-07-22
Yes, I regularly keep backups of my home directory and restore parts from it. I've never done a total restore that way though, just the particular item I wanted.

---

### Post by loboc on 2008-07-22
> **fogelfink said:**
> It might sound a bit stupid, but I need some advice on how to reinstall ubuntu.

I have basically destroyed my ALSA by installing OSS, which didn't work for me - and after numerous attempts of fixing it, I have been told that the only way to fix it is a clean fresh install of Ubuntu.  [[http://ubuntuforums.org/showpost.php?p=5437671&postcount=292]](http://ubuntuforums.org/showpost.php?p=5437671&postcount=292])
I am coming round to that idea (I tried reinstalling a fresh kernel, which didn't help) - so now I wonder how I can do that with some sort of backup.  

I would like to install Ubuntu Studio (Hardy), but am currently using the regular Ubuntu (Hardy).  I would like to keep my personal settings such as evolution mail settings, firefox bookmarks, tomboy notes, etc.  AND of course my files in the home directory (lots of graphics and music stuff, so it's about 110GB!!).  What I don't want to back up is my screwed sound settings.

Do I make some sort of backup (if yes how?) and then create a new Ubuntu Studio partition without erasing the existing Ubuntu partition and then drag my home direcory files (graphics and music) somehow into my new home directory (if so, how?), while using the backup for the settings.  And last try to erase the old and faulty Ubuntu partition?

OR, do I have to get all my data from the home directory shifted onto an external harddrive, then make a backup of the settings and finally install Ubuntu Studio with reformatting the harddrive?  Could I then use some form of settings backup to get the data from evolution etc back into the new system, while simply shifting my home directory files back onto the internal drive?

OR, worst case scenario, do I have to reconfigure my mail accounts, address book, bookmarks, etc. because I use a different distro of ubuntu?

Your advice is appreciated.

All of your settings and data should be in your home directory unless you were hacking around in /etc to configure something.  So plug a USB drive in and copy the whole thing over to the USB stick, clean install and copy it back.  Things that aren't stored in ~/ that you may have configured with a gui tool that come to mind are samba and NFS shares but how many of those can you have.

---

### Post by loboc on 2008-07-22
> **sdowney717 said:**
> I have been wondering about this.
Your /home partition contains all your stuff like bookmarks etc...
Can you just copy this over and then setup a new user using this folder?

try it: fire up a terminal and do a 

```


sudo adduser newguy

sudo cp -R /home/oldguy /home/newguy/

cd /home

sudo chown -R newguy ./newguy

sudo chgrp -R newguy ./newguy


```

I never have but I think thats all thats to it.  If you set up a skeleton directory you can use the adduser.conf to determine which files would be in there from the start and avoid the chgrp and chown

---

### Post by ace007 on 2008-07-22
Here is an excellent guide for migrating your current /home folder to a new partition.  Once your home is on a new partition you can just install with a new Ubuntu.  In step 4 when it asks you to choose a partition, DO NOT CHOOSE GUIDED. Select the manual option and then set your new home partition to mount at "/home"

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by bodhi.zazen on 2008-07-22
> **loboc said:**
> try it: fire up a terminal and do a 

```


sudo adduser newguy

sudo cp -R /home/oldguy /home/newguy/

cd /home

sudo chown -R newguy ./newguy

sudo chgrp -R newguy ./newguy


```I never have but I think thats all thats to it.  If you set up a skeleton directory you can use the adduser.conf to determine which files would be in there from the start and avoid the chgrp and chown


Well, not quite *that* simple, lol

If you are moving /home , follow a tutorial

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

        [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by sdowney717 on 2008-07-22
I have gone thru 3 distribution upgrades and the last 2 upgrades, I had no problems. I did not have to wipe it and start fresh, so losing /home has not yet been an issue. 
Some music, video, bookmarks and a few programs is all I care to keep backed up. My mail is hotmail so it is on the web.
If keeping /home in its own partition is preferable, why is this not the default on an install?

---

### Post by bodhi.zazen on 2008-07-22
> **sdowney717 said:**
> I have gone thru 3 distribution upgrades and the last 2 upgrades, I had no problems. I did not have to wipe it and start fresh, so losing /home has not yet been an issue. 
Some music, video, bookmarks and a few programs is all I care to keep backed up. My mail is hotmail so it is on the web.
If keeping /home in its own partition is preferable, why is this not the default on an install?

Because it depends on who you ask, lol.

IMO a /home is not preferable, I prefer a /data partition. /home then has a bunch of config files, none of which are particularly valuable (IMHO).

You then

 ln -s /data/music /home/user/music 

and on ...

---

