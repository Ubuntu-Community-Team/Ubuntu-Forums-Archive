---
title: "Attempt at installing new desktop wiped Vista from boot menu"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by halberdier25 on 2008-05-18
[http://ubuntuforums.org/showthread.php?t=799025](http://ubuntuforums.org/showthread.php?t=799025)

Yeah, now I can only see Ubuntu, the recovery, and the memory test in the OS selection menu.  No longer can I see my Vista loader or the Vista recovery loader.  Any idea as to how to get it back?  I kind of need it.

---

### Post by Paqman on 2008-05-18
The file that creates the grub boot list is located at /boot/grub/menu.lst

If your Vista isn't listed somewhere on there you can add it yourself:
```

gksu gedit /boot/grub/menu.lst

```
This will open the file as root, so you can edit it.
Add an entry that says:
```

title		Microsoft Windows
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```
NB: This assumes that Windows is located on the first partition on your hard drive. If it isn't then change the (hd0,0) to reflect that. Number starts from zero, so partition sda1=hd0,0 while sda5=hd0,4 for example.

---

