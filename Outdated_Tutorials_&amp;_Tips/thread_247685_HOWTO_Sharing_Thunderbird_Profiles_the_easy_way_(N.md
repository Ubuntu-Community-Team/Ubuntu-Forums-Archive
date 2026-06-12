---
title: "HOWTO: Sharing Thunderbird Profiles the easy way (No fat32!)"
date: 2006-08-31
forum: Outdated Tutorials &amp; Tips
---

### Post by kendals on 2006-08-31
Go easy on me as this is my first HOWTO :P

Anyway, after stuffing around, I've found the easiest way to 'sync' your Thunderbird in XP and Ubuntu Dapper :) It does not require you setting up a FAT32 partition so that both can read the profile folder.

You simple follow these steps:

1. Make sure Thunderbird is installed on both systems (can have two different versions- I have TB2 in XP, and TB1.5 in Ubuntu).

2. Download and install this excellent program in XP (it's free)- [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html).

3. Once your Ext3 Ubuntu partition is mounted in XP, simply use your Ubuntu profile as your default (if you have all your accounts and email in XP, use this guide to shift the profile to Ubuntu- [http://www.mozilla.org/support/thunderbird/profile#move)](http://www.mozilla.org/support/thunderbird/profile#move)).

4. In XP, go to your Thunderbird profile folder and open profile.ini (i.e. c:\Documents and Settings\[COLOR="Red"]username[/COLOR]\Application Data\Thunderbird\) and edit it to look similar to this:

```
[General]
StartWithLastProfile=0

[Profile0]
Name=default
IsRelative=0
Path=X:\home\[COLOR="#ff0000"]username[/COLOR]\.mozilla-thunderbird\[COLOR="PaleGreen"]d612f1hx[/COLOR].default
```

Note that I mapped the ext3 Ubuntu partition as X:], so if you called it a  different drive letter, you'll need to change that. Also, your profile folder will be different, so be sure to check, because it won't be the one in green- it'll be unique to your computer, so change that to fit.

Save and close.

Now, whenever you're in XP or Ubuntu, your Thunderbird accounts and email and rules will always be there, no fuss! :KS

---

### Post by MetalMusicAddict on 2006-08-31
I wonder if this can be done on a networked drive? Have multiple PCs see the thunderbird profile?

---

### Post by viviena on 2006-08-31
The same can also be done with Firefox -- and I do love that, sharing email and browser settings across two OSes. Ideal for dual-booters. :D

---

### Post by luca.b on 2006-09-01
A notice, **don't** use this driver if you are on a laptop and use hibernation. If you hibernate in Windows, the driver won't unmount your ext2/3 partition cleanly.

---

### Post by kendals on 2006-09-01
Totally. Now stay tuned as I see if it works the same using VMWare Server for XP in Ubuntu ;)

---

