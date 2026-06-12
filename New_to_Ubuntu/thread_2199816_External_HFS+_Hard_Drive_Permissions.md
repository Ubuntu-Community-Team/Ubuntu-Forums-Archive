---
title: "External HFS+ Hard Drive Permissions"
date: 2014-01-15
forum: New to Ubuntu
---

### Post by corbin.loftis on 2014-01-15
I have been using Ubuntu for a while (on and off), but just today switched over entirely to 12.04 LTS on my MacBook Pro 7,1.

The problem I've been having is being able to enable read/write permissions on my external hard drive (formatted as HFS+). I have already:

-- used gksudo nautilus to enter as root and right-click the drive and go to properties-permissions, but it still says it is a read-only volume and unable to complete the action.
-- I have tried using -$ sudo chmod 777 /media/Element, and -$ sudo chown -R /media/Element and /dev/sdc1, but neither have worked. When I changed the permissions in nautilus under root, I was able to copy one directory before something happened and it moved back to read-only, and it won't keep the settings for read/write if I exit root nautilus.

If anyone can tell me how to explicitly give full read/write permissions on an external (HFS+) volume, that will NOT CHANGE after they've been updated, it would be greatly appreciated. And yes, I know how to use terminal to a good extent.

---

### Post by corbin.loftis on 2014-01-16
BUMP. Does nobody have an answer?

---

### Post by fosterD on 2014-01-16
Hi, it seems like you have to turn off the journalling.

This case looks similar to yours
[http://askubuntu.com/questions/182433/hfs-hard-drive-being-mounted-as-read-only](http://askubuntu.com/questions/182433/hfs-hard-drive-being-mounted-as-read-only)
or
[http://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os](http://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os)

Hope this help.

---

### Post by corbin.loftis on 2014-01-16
> **fosterD said:**
> Hi, it seems like you have to turn off the journalling.


Is there a way to turn off journaling on Ubuntu, or am I able to do it from any Mac? Because my computer no longer runs Mac. It's now Ubuntu-only. If I can only do it from a Mac, then I guess I can try and go to the university library and use theirs. If it works, PROPS!

---

### Post by fosterD on 2014-01-16
If it is a journaled HFS+ file system, it is not recommended to disable it from a non-Mac pc.
Or someone may have a better ideas?

---

### Post by corbin.loftis on 2014-01-17
It worked! I was able to go to a library that had Macs, and I used Disk Utility to disable journaling. THANK YOU!

---

