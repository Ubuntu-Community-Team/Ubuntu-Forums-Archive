---
title: "[SOLVED] OpenOffice 3?"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by reg4c on 2008-10-18
Hey, 

OO.org 3 was release a week or so ago so I was wandering when it would be in the repos. It has not been updated yet.

I have some assignments due and am not in the mood to do them in Winblowz....

Anyone has any info?

Cheers

---

### Post by MasterNetra on 2008-10-18
Maybe its being reserved for 8.10 only?? I know 8.10 will have it.

---

### Post by bruce2000 on 2008-10-18
Hi,

Here is a Howto for installing it:

[http://www.kshoster.net/node/56]("http://www.kshoster.net/node/56")

---

### Post by Zzl1xndd on 2008-10-18
Not sure when it will be added to the repos but Im pretty sure there is a .deb for it at OO.o


[http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US)

---

### Post by cwsnyder on 2008-10-18
If you don't need to hand in your assignment in Office 2007 or OOXML format, you could probably do most of your work in the older OOo versions.

There seems to be binary and source code availability at [http://linux.softpedia.com/progDownload/OpenOffice-dot-org-Download-253.html](http://linux.softpedia.com/progDownload/OpenOffice-dot-org-Download-253.html)  Warning: This site lists only bittorrent downloads for the binary.

---

### Post by philinux on 2008-10-18
Lots of interest for this.

[http://ubuntuforums.org/showthread.php?t=951519](http://ubuntuforums.org/showthread.php?t=951519)
[http://ubuntuforums.org/showthread.php?t=942645&highlight=open+office](http://ubuntuforums.org/showthread.php?t=942645&highlight=open+office)
[http://ubuntuforums.org/showthread.php?t=801196&highlight=open+office](http://ubuntuforums.org/showthread.php?t=801196&highlight=open+office)

---

### Post by reg4c on 2008-10-18
AAaah, you see I was not thinking that it is possible to download software from things called websites

apt-get has trully spoiled me...

Cheerio

---

### Post by SunnyRabbiera on 2008-10-18
> **reg4c said:**
> AAaah, you see I was not thinking that it is possible to download software from things called websites

apt-get has trully spoiled me...

Cheerio

Just remember, this will be a pain in the @#$% because there are so many installer files inside the debian versions.
I have a Mini guide:
This guide mainly applys to recent versions of Ubuntu (Versions 7.10 through 8.10) as I am unsure if Open office 3 will work in older versions of Ubuntu.
Anyhow I will keep this simple:
Step 1: Download open office 3 for debian
2: Extract the zip file
3: In the debs folder move everything you have into the desktop integration folder by selecting as many of the debian insallers you can at a time but there are a whole crap load of them so this might take a while.
4: For normal Ubuntu users install the package nautilus-open-terminal, for Kubuntu and xubuntu users skip this
5: For normal Ubuntu users, restart your computer, for Kubuntu and xubuntu users skip this.
6: Remove as much of open office 2 as you can
7: go into that desktop integration directory and open up a terminal, now how to open your terminal in Ubuntu is by right clicking in the folder and selecting Open terminal.
Kubuntu and xubuntu users should have the open terminal command in the main menu of both Thunar and Dolphin/Konqueror
8: put in the command: sudo dpkg -i *.deb
9: after dpkg is done you may wish to try to install the package openoffice.org3.0-debian-menus_3.0-9354_all located in your desktop integration folder.
10: done

---

### Post by reg4c on 2008-10-18
Thanks but no thanks

I guess I don't HAVE to use v3, although from testing it on Windows there are some merits

I will just hold it for a while

Cheerio

---

