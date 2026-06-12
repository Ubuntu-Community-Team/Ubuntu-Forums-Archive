---
title: "[SOLVED] Samba Shares Broken After Intrepid Upgrade"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by BassKozz on 2008-11-04
I just upgraded from Hardy (8.04) to Intrepid (8.10) and my Samba shares I have setup thru **/etc/samba/smb.conf** are no longer working, my WinXP machines can't even see my Ubuntu box :confused:

Any Idea's?

---

### Post by BassKozz on 2008-11-04
**SOLVED**: For some reason samba got un-installed during the upgrade, so I:
```
sudo apt-get install samba
```
and all is well :D
Anyone know why the upgrade would have un-installed samba?

---

### Post by jwilentz on 2008-11-18
I have had the same problem except that Samba seems installed.  My win boxes can see the Xubuntu server, but the Xubuntu box can't see the Win shares.

---

### Post by jwilentz on 2008-11-18
> **BassKozz said:**
> **SOLVED**: For some reason samba got un-installed during the upgrade, so I:
```
sudo apt-get install samba
```
and all is well :D
Anyone know why the upgrade would have un-installed samba?
How have you set up your samba.conf file, and can your Ubuntu machine see your windows shares?

---

### Post by BassKozz on 2008-11-18
> **jwilentz said:**
> How have you set up your samba.conf file, and can your Ubuntu machine see your windows shares?

_To Share files on your Ubuntu box with other machines_
I manually edited **/etc/samba/smb.conf** to add my shares. (from my Ubuntu Box to WinXP boxes)
Check out this for more info: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[U]
To mount shares from Other machines on your Ubuntu box[/U]
To mount your XP shares you need to place them in your **/etc/fstab** file, check out this thread: [http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)
HTH,
-BassKozz

---

