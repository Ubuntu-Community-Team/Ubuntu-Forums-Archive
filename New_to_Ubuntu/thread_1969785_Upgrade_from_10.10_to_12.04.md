---
title: "Upgrade from 10.10 to 12.04"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by blackhill on 2012-04-30
Since late 2010, I have happily used ubuntu 10.10. I preferred its format to the more recent versions. However, 10.10 is no longer supported and I feel I should upgrade to a current version.
Can anyone suggest how best to do this. I could probably obtain the intermediate versions and do a series of sequential updates but this would be laborious and offer numerous opertunities for introducing errors. Alternatively, I could install 12.04 directly. 
Obviously, I do not want to loose access to my personal data files. Could someone please advise me which route to take and how best to minimise any loss of data or access to it.
Thank you

---

### Post by kurt18947 on 2012-04-30
Personally I'd do a fresh install.  Before I did anything, I'd make sure to back up hard-to-replace data.  Preferably in two different formats or places.  Make sure you can read the backups.  I think a big consideration is how much personal data do you have?  I don't have much so I just copy my entire /home directory to an external hard drive.  I can then pick and choose what to copy to my new install.  If you have many gigabytes of videos, pictures etc. you might approach it differently.   I don't know what you use for browser and email.  I use Mozilla's sync service to move cookies, bookmarks etc. from an old install to a newer install.  You're *supposed* to be able to move a Thunderbird profile from one install to another.  My luck has been mixed doing that.  I've had good success with the same version between machines, less so trying to move a profile from an older version of Thunderbird to a newer version.  Thunderbird and Firefox data is stored in your user home directory in .mozilla folder and .thunderbird folder.  'Dot' files are hidden and can be revealed in your file manager by either clicking 'view' -> 'show hidden files' or <ctrl>h in your file manager.

---

### Post by Niemand000 on 2012-04-30
I'm new to Ubuntu, but from what I understand to do what you want to do would mean either

1. go upgrade by upgrade until you get to 12.04 (so as to keep your personal files)

or 

2. backup your files via an external hard drive and fresh install. (which is what I would do.  Saves time, and it results in you having an up to date OS with all of your files intact with an external backup to boot.  It's a win win)

---

### Post by Rex Bouwense on 2012-04-30
+1 for a fresh install.  You would have to go through too many upgrades to make it worth while (10.10->11.04->11.10->12.04).  Just too many chances for a screw up or a power failure or any kind of glitch.  If you have data that you cannot live without, do back it up because you will lose it when you do a fresh install.
Download the ISO
Check the md5sum
burn the image at the lowest possible speed
Try it before you install to make sure everything is copacetic.
Install
Enjoy.

---

### Post by DaveMcC on 2012-04-30
When you do a fresh install, does it completely wipe the hard drive

Or does it re-write the files, 

Reason why I ask, I remember others doing like wise with XP ver 1 and then with XP + sp3 and it made a right mess

I also remember seeing people on here with different versions of Linux, ie. Ubuntu, Xubuntu, Mint at the same time

Dave

---

### Post by Rex Bouwense on 2012-04-30
When you do a fresh install there is nothing saved on your hard drive unless you are dual booting and you have told it to install on a particular partition.  I just did a fresh install of Lubuntu 12.04 on an old Dell laptop.  Nothing left of the old system and it runs fine (and fast).

---

### Post by geovino on 2012-05-15
Please do a clean install. Backup files and install clean. It will format the drive and install a new clean Ubuntu 12.04.

You'll feel better, fast. :)

---

