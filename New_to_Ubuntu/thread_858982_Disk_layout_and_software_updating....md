---
title: "Disk layout and software updating..."
date: 2008-07-14
forum: New to Ubuntu
---

### Post by xeriouxi on 2008-07-14
Hi!

First I wanna thank everyone who's helped so far! =)

I've only ran Ubuntu via Wubi at the moment on a 10gb virtual drive. Say Windows was to vanish. I have 2 HD's in my PC. If I did a fresh Ubuntu install would it find and manage this drive for me? I notice that the layout of the drive is bin, etc, home etc. so does this mean that Ubuntu will merge both drives into one, or will it show 2 seperate hard drives both with their own bin, home etc. file system on? (Hope that made sense! ^^)

Also I have a query about software updates. I know that many programs are in the Synaptic package manager and therefore will get updates just fine. If I was to download a .tar archive or something of that nature, would it add itself to the repository and find updates or is this not possible?

Thanks for your time! =D

---

### Post by kevincai96 on 2008-07-14
I found this really cool site that lets you make money! It's real, since I use it. [http://www.AWSurveys.com/HomeMain.cfm?RefID=kevincai96](http://www.AWSurveys.com/HomeMain.cfm?RefID=kevincai96)

---

### Post by nowshining on 2008-07-14
for ur tar Question - NO, u will need to get an url if any for updates thru the update manager, etc.. otherwise if they don't do have update urls, u will need to download and re-compile each time a new app. version comes out or download a new deb file manually and remove the ol' version and install the new one.

---

### Post by mcduck on 2008-07-14
If you install Ubuntu you'll only get one file system. The second drive will be mounted into it's own directory inside /media. Of course you can change it to mount into any directory you want.

For example you could make the second drive your home directory: or even your desktop, if you wanted..

---

### Post by CatKiller on 2008-07-14
If you were to get rid of Windows, your current Ubuntu install would also go. If you backup your home folder from your current install, you could keep your existing settings by restoring that to your new Ubuntu install.

Linux has a unified filesystem, so you would mount the second hard drive somewhere in the filesystem tree. Many people would have a second drive as their home folder, to keep it separate from the rest of the install, but it could really be anywhere. For example, I have a second drive mounted at /mnt/music for all my music.

If you compile your own software, it is possible to manage it with your package manager by installing it with **checkinstall**. This will automatically package the software before it gets installed. Then, if the software becomes available through the repositories, it can be updated automatically too.

---

### Post by xeriouxi on 2008-07-14
Thanks for your replies! =)

Is there any documentation on how to add update URL's to Ubuntu to monitor for .tar installed software updates?

Likewise, any documentation for mounting my 2nd HD to the /home folder?

Thanks! =)

---

### Post by nowshining on 2008-07-14
it depends on the site on whether they have a url for updates, etc..

try software sources ;) it's in the menus.

---

### Post by nowshining on 2008-07-14
it depends on the site on whether they have a url for updates, etc..

try software sources ;) it's in the menus.

---

### Post by CatKiller on 2008-07-15
> **xeriouxi said:**
> Is there any documentation on how to add update URL's to Ubuntu to monitor for .tar installed software updates?

If you install **checkinstall** through Synaptic (I don't think it's installed by default) then you can read **man checkinstall** for the documentation. It's pretty straightforward to use, though - instead of the **sudo make install** step, you would instead run **sudo checkinstall**.

A number of projects host their own repositories, either because the project is not popular enough to have their packages included in the standard repositories, or because the standard repositories include an earlier version. If this is the case for a given project, then instead of downloading and compiling the source code, you simply add an entry in Software Sources (in the System -> Administration menu). Then you can install and update the package exactly as you would any of the standard Ubuntu packages. If this is the case, then the projects webpage will tell you the entry to put in.

You might also be interested in reading [this page]("http://monkeyblog.org/ubuntu/installing/") for details on the different ways that you can install software in Ubuntu.

> Likewise, any documentation for mounting my 2nd HD to the /home folder?

[This page]("http://www.psychocats.net/ubuntu/separatehome") is a tutorial on how to create a separate partition for use as /home. The principal is exactly the same for using a second drive, except that you create the partition on the second drive instead of the first.

There is also some other interesting information on that site.

---

### Post by arpanaut on 2008-07-15
[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

This will tell you how to pull your install in wubi out of windows and have an install of the OS on its own dedicated partition.

Hopefully Helpful???

---

### Post by OffAxis on 2008-07-15
> Is there any documentation on how to add update URL's to Ubuntu to monitor for .tar installed software updates

.tar files and programs have no readily available means for monitoring / updating. A .tar file usually means source code that has to be compiled locally and then installed.

For keeping a program updated, a website will usually set up a repository of .deb files, and have a text file on the site that lists the files and latest release on the site. These have already been compiled, and these can be monitored by adding the url of the text file to the sources.list file.
The file can be appended to this list:
**/etc/apt/sources.list**
or a fragment configuration file can be put here:
**/etc/apt/sources.list.d/**

---

