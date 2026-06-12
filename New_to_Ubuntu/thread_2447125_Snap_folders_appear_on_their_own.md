---
title: "Snap folders appear on their own"
date: 2020-07-13
forum: New to Ubuntu
---

### Post by nunchuks on 2020-07-13
Hi I have been using Ubuntu for a few months now, and I noticed recently that** a couple of apps - Libreoffice and Opera - suddenly created a new folder **each in Snap (they have number labels). 

For example, Opera usually has under Home >> Snap >> Opera >> 81, common and current. But a new folder **83 **appeared. 
Libreoffice's usual 180 or 183 gained a friend.

I did not update or upgrade, and when I reformatted and reinstalled the apps from the App Store they disappeared/went back to the usual. 

I am concerned if this means someone had gained root access, added a file and changed permissions on the file, and how they would do it.

---

### Post by Dennis N on 2020-07-13
There's nothing wrong. You had snap versions of LibreOffice and Opera. When you reformatted and reinstalled them, you installed the .deb versions.

There is a folder in ~/snap for every snap application.

```
dmn@Sydney-vm:~/snap$ tree
.
&#9500;&#9472;&#9472; atari800-jz
&#9474;** &#9500;&#9472;&#9472; 1
&#9474;** &#9500;&#9472;&#9472; common
&#9474;** &#9492;&#9472;&#9472; current -> 1
&#9500;&#9472;&#9472; chromium
&#9474;** &#9500;&#9472;&#9472; 1193
&#9474;** &#9500;&#9472;&#9472; 1213
&#9474;** &#9500;&#9472;&#9472; common
&#9474;** &#9492;&#9472;&#9472; current -> 1213
&#9500;&#9472;&#9472; gnome-calculator
&#9474;** &#9492;&#9472;&#9472; current -> 730
&#9500;&#9472;&#9472; gnome-characters
&#9474;** &#9492;&#9472;&#9472; current -> 399
&#9500;&#9472;&#9472; libreoffice
&#9474;** &#9500;&#9472;&#9472; 180
&#9474;** &#9500;&#9472;&#9472; 183
&#9474;** &#9500;&#9472;&#9472; common
&#9474;** &#9492;&#9472;&#9472; current -> 183
&#9492;&#9472;&#9472; snap-store
    &#9500;&#9472;&#9472; 415
    &#9500;&#9472;&#9472; common
    &#9492;&#9472;&#9472; current -> 415

19 directories, 3 files
```

A folder exists for each snap application with subfolders corresponding to each revision number that's installed. The system keeps at most two revisions, with a symbolic link to the currently used one. The numbered folders are (at the moment) empty on my system. The applications themselves are not stored here.

---

### Post by Holger_Gehrke on 2020-07-13
snap comes with a background process (called a daemon in UNIX parlance, which is why these programs often have names ending in 'd') called snapd. One of the things snapd does is keep your snaps up to date by downloading and installing newer versions automatically. A certain, configurable number of revisions is kept in case you want to roll back to an older version.

Holger

---

