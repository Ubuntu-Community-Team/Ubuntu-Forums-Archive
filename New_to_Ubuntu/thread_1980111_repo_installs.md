---
title: "repo installs"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by JNMoose on 2012-05-14
Need  help installing the Repository disks from osdisc.com? need to move file to /tmp then run installer and load the disc 1-11 sounds easy but not need help thks....:confused:

---

### Post by QIII on 2012-05-14
I'm not familiar with osdisc.com other than that you buy OSes from there (which is a waste of money IMO since you can download Ubuntu for free).

Could you describe what you are trying to accomplish and what you have tried to do?

---

### Post by JNMoose on 2012-05-14
I got everything install by the means of the os just ading the medibuntu repo, But in the read me file it tells me to move a file to /tmp folder then run this install and it should load disk 1 though 11 and have all the repo on the hard drive.  Just cant figure how to do it?

---

### Post by QIII on 2012-05-14
Again, I'm not sure what you are trying to do.  When Ubuntu is installed, it comes with all of the Ubuntu repos.  Adding medibuntu is an extra that has to be done separately because of legal restrictions.  It can be done easily from here

[http://medibuntu.org/](http://medibuntu.org/)

---

### Post by JNMoose on 2012-05-14
Yeap i all ready got it installed, I'm talking about the entire repository for ubuntu 12.04 all the software so i don't have to download them.  I got all the packages on 11 4.7 gb disks just trying to install it on the hard drive so when i goto software center i just pick the program and its there on the hard drive ready to install no watiting for a mirror to download it..It tells me to copy the installer from the dvd to /tmp says cp /media/cdrom/installrepo /tmp.. Then run the install by typing sudo /tmp/installrepo.. It then says the installer will copy all the files from the dvd and then prompt for the next dvd. Once it has finshed copying all the dvds, you will have a complete copy of the repository in /usr/repo.  Packages can be installed using APT, THE PACKAGE MGR, OR THE SOFTWARE CENTER.

---

### Post by JNMoose on 2012-05-14
Just got it and it is install thks for help!!!!!!

---

### Post by QIII on 2012-05-14
Using the repos on a hard drive has the very serious disadvantage in that the repos are fixed.  You should use the repos on line for security and software updates.  Using repos on a local hard drive is suitable for people with a low bandwidth (or no) internet connection.

Had it been me, I wouldn't have paid for a disk and would just have downloaded and burned the official disk and installed from it.  Then everything would have been in order -- lacking only the need to add the medibuntu repo.

Were I you, I would use the on-line repos.

---

