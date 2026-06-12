---
title: "HOWTO: Play video from SAMBA share without mounting"
date: 2006-07-26
forum: Outdated Tutorials &amp; Tips
---

### Post by brin on 2006-07-26
Hello,

Some people like myself have had issues of wanting to play audio and videos files from a Windows samba shared directory and have been told that you can only do so if you mount the smb shared directory first as access the files as local files. 

This HOWTO shows a method of playing videos using MPlayer directly from nautilus window without having to mount the shared directory.

Packages that you need from you favourite ubuntu mirror:
mplayer
nautilus-actions-config
necessary samba packages (not sure which is critical but I have installed samba-common, libsmbclient, smbfs and smbclient

The latest standard MPlayer package actually supports smb and you can check by running the following in terminal with a valid smb address:

mplayer smb://192.168.1.3/shared/example.avi



If this doesnt work, then you either need the latest mplayer or samba client package.

Once we know that mplayer supports smb, we need to next configure a handler for opening movie files with mplayer.
I tried to simply using the "Open With" action in nautilus but it never seemed to fire up mplayer with the correct file details, so had to use nautilus-actions-config to configure individual action.

After installing nautilus-actions-config package, simply run nautilus-actions-config from terminal. This should bring up a new dialog box where you can create a new action. 

For quick setup, enter the following;
Menu item and Action:
 Label: Open with Mplayer
 Path: /usr/bin/mplayer
 Parameters: %u

* For params you can further add mplayer parameters such as -cache for possibly smoother stream across network. *

Advanced Conditions:
Ensure that smb windows shares is checked and you can uncheck the rest if you wish.


Regards,
Brinley

---

### Post by curtis on 2006-07-26
Works great here, I got it working fine with VLC as well.

---

### Post by rp2615 on 2006-11-07
I'm sorry for bringing this post "back from the dead" but I've followed the instructions in the 1st post and it makes the option "open with mplayer" appear when I right-click the file I want to open but it won't start mplayer when I click on it.

Any ideas why?

Thanks!

---

