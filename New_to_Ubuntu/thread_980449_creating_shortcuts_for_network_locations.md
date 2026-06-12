---
title: "creating shortcuts for network locations"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by Matt26 on 2008-11-12
is there a simple way to create a shortcut to a network drive that resides on a separate computer (windows xp) and place in the Computer location?

thanks.

---

### Post by nhasian on 2008-11-12
not sure how to place it in the computer location, but you can have it automount the windows share by editing /etc/fstab.  

[http://ubuntuforums.org/showpost.php?p=1681827&postcount=5](http://ubuntuforums.org/showpost.php?p=1681827&postcount=5)

---

### Post by fatphilthethird on 2008-11-13
Bookmark it in nautilus?

---

### Post by Matt26 on 2008-11-13
> **nhasian said:**
> not sure how to place it in the computer location, but you can have it automount the windows share by editing /etc/fstab.  

[http://ubuntuforums.org/showpost.php?p=1681827&postcount=5](http://ubuntuforums.org/showpost.php?p=1681827&postcount=5)

thanks i have tried this but unfortunately it didn't work for me.  i am assuming that the samba credentials are the username and password for the windows xp system?  if this is correct, i don't currently have a password set for my login to the windows system, so i'm not sure how this would be set in fstab- i have read suggestions of using ***password=,*** and ***password="",*** but i don't know how it should go- itried with ***password=,*** but that didn't work.  any ideas on this?  also, is cifs better to use than samba for a windows xp pro system?

---

