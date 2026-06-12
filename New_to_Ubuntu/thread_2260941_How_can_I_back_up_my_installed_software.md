---
title: "How can I back up my installed software?"
date: 2015-01-15
forum: New to Ubuntu
---

### Post by tiamat2009 on 2015-01-15
On windows I have a folder with all the applications I have downloaded and installed. That way I can re-install even without an internet connection.

How can I do this on ubuntu, everything is done through the software manager, but I then have no idea: 1 - where the apps are going, or 2 - how to back them up incase I want to install without an internet connection.

Thanks.

---

### Post by grahammechanical on 2015-01-15
Linux does not work like Microsoft Windows. But we can create our own offline repository from which to reinstall applications. We also have the ISO image that we used to install Ubuntu. That also can be used as a software source.

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

Regards.

---

### Post by tiamat2009 on 2015-01-15
Thnaks for this, I shall read the link tonight. 

So is there a special folder where the apps go once installed? I find the number of folders in "/" confusing and am not sure what they all do, apart from a few that I needed for web devlopment, or is there maybe a wiki link or something that explains this?

---

### Post by TheFu on 2015-01-15
Package managers really need an internet connection to work. **This is the magic of dependency checking and extremely easy updates. It is the main reason I prefer Linux over Windows.** I never want to go back.  You can minimize the internet bandwidth by using a package caching server like **apt-cacherng**.  I do, but an internet connection is still needed to get updated dependencies and packages. Installing packages outside the package manager is usually a mistake.  How software is installed under Ubuntu matters. Downloading a .deb file is NOT the same as installing it through the package manager. 

Being able to backup a system is critical.  There are a few different ways.
* create an image of the system partition. Clonezilla, partimage, fsarchive, dd, or any of 10-20 other tools can do it. The most important part of this method is that the OS cannot be running for it to work. You must boot off alternate media to clone/image the OS you want.  That makes this nearly impossible to automate.  Restores are just shoving the image onto a HDD or a partition of a HDD.
* backup the entire OS, Data, and Settings.  This is the normal way that UNIX people have performed backups for 40+ yrs.  The most popular backup tools do it. It gets everything on the system, including things that never change (about 4G of files). Fine if you have 1-2 machines.  Extremely wasteful if there are 5-50,000 machines. Backups need to quiesce any actively used files, like DBMSes, to prevent corrupted backups. Restores are relatively simple.
* My favorite: backup the list of installed packages, OS settings, personal settings, files and data.  [http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview) explains in more detail. Backups need to quiesce any actively used files, like DBMSes, to prevent corrupted backups. It is more complex to restore. 

Oh ... and you can find all the .deb files downloaded to be installed on your system in the /var/ partition.  
To teach you to fish .... 
```
find /var -type f -iname \*deb
```
or 
install **locate** and use **sudo updatedb**, then ```
locate deb|egrep 'deb$'
``` Locate will automatically update where every file is on the system (not temporary mounted storage) periodically, so you can nearly instantaneously find any file. It honors file/directory permissions, so you may need to use sudo for some file types, but usually that isn't an issue.

Knowing where UNIX/Linux systems place files is an important tidbit of knowledge. It is all documented. [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
Also, most Linux training guides cover this fairly early in the process to help folks just learning where thing belong. Here's my favorite, free, book: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) - BTW - it is #1 on Amazon.

---

