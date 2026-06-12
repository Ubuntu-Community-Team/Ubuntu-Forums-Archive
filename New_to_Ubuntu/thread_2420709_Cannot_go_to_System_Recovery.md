---
title: "Cannot go to System Recovery"
date: 2019-06-09
forum: New to Ubuntu
---

### Post by nugulus on 2019-06-09
Device: HP Spectre x360 laptop
Ubuntu: 18.04
Issue: During boot, I am prompted to hit ESC key to go to system start up. I did, and hit F11, instead going to System Recovery, I will be brought to Desktop Login prompt. Tried F12, same.

Accidentally I did "usermod -G groupname myuserid", and lost the admin group membership. Now I want to bring it back.

Dalton

---

### Post by wildmanne39 on 2019-06-09
*Thread moved to **New to Ubuntu a more appropriate sub-forum**.*

---

### Post by cruzer001 on 2019-06-09
Any of this tie in with your problems?

[https://ubuntuforums.org/showthread.php?t=2420559](https://ubuntuforums.org/showthread.php?t=2420559)

---

### Post by TheFu on 2019-06-11
> Accidentally I did "usermod -G groupname myuserid", and lost the admin group membership. Now I want to bring it back.


If it were me with this, I'd boot off some install media - "Try Ubuntu" - then mount the / partition or LV from the installed HDD version and manually modify the passwd and group files inside /etc/.  The group and passwd file s are just text and follow a well-documented colon delimited format.  Make a backup copy of each before you get started, since if you screw these up, the system might not boot.

The top location for the files and backups will need to be filled in.  The locations below ARE NOT correct inside a live "try ubuntu" environment.

sudo cp /etc/passwd /etc/passwd.bak
sudo cp /etc/group /etc/group.bak

```
man -s 5 passwd
```
and
```
man -s 5 group
```
explains the format for each. -s 5 tells the man program use use only section 5 manpages. That is where configuration file data is stored.

The only real trick to all of this is modifying the correct files in the correct partition and not the "live" - Try Ubuntu directory /etc/.

This is one of those things that takes a chapter to explain, but it is just 5 characters to actually fix.  The fix is inside the "group" file. Append your username to the end of the line where you need it, following the pattern already there.  Might need a comma. Might not.

---

