---
title: "[SOLVED] External hard drive permissions"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by nkri on 2008-07-02
Hey guys,

I got a Seagate Freeagent 500GB hard drive a couple of weeks ago and formatted to HFS because I do all my photo stuff with it in OS X.  I finally figured out how to write to it, but can only set permissions for the folders instead of the entire drive (sudo nautilus, right-click on the folders, give myself permissions).  When I click Properties on the HDD icon on the desktop and go to the "Permissions" tab, it says "The permissions of Seagate FreeAgent could not be determined."  This is *really* frustrating, as I've been trying to create a disk image with PartImage on the external drive and it won't let me since I don't have full authority.  Anyone know how to fix this for good?

Thanks!
-nkri

---

### Post by jpkotta on 2008-07-02
You can add an entry in /etc/fstab.  Adding uid and gid options will probably get you what you want.  To find your uid (uid is a unique number that is associated to your user),
```
id
```

And in /etc/fstab, maybe something like:
```
/dev/sdb1 /media/pics hfs rw,user,uid=1000 0 0
```

Look at the output of ```
mount
``` to see which device the drive comes up as.  Look at ```
man mount
``` in the hfs section to see other options.

---

### Post by nkri on 2008-07-03
Well, I deserve to be slapped.  I did what you said, and it didn't work (/etc/fstab didn't seem to recognize that I entered anything at all).  I then worked for about 3 hours straight trying everything I could think of to fix it.  Nothing seemed to being going the right way until I looked at my syslog and it said the HDD was not cleanly unmounted and to perform fsck.  I did this, and it works perfectly.  I could've had a V8.  Anyway, thanks a ton for the help!
-nkri

---

