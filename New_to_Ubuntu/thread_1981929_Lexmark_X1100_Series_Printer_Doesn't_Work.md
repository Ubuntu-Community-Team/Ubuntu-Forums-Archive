---
title: "Lexmark X1100 Series Printer Doesn't Work"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by smiley07 on 2012-05-17
I haven't used my printer for a number of months, but when I tried to use it today it wouldn't work. When I looked under my printer's properties I got this: 

Idle - File "/usr/lib/cups/filter/rastertoz600" not available: No such file or directory

Does anyone know how to fix this, so I can get my printer back up and running?

---

### Post by Daveth on 2012-05-17
I think this may ease your woes
[http://ubuntuforums.org/showthread.php?t=1282957](http://ubuntuforums.org/showthread.php?t=1282957)

---

### Post by smiley07 on 2012-05-17
> **Daveth said:**
> I think this may ease your woes
[http://ubuntuforums.org/showthread.php?t=1282957](http://ubuntuforums.org/showthread.php?t=1282957)

So, I tried installing libstdc++5, and got the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libstdc++5 is already the newest version.
The following package was automatically installed and is no longer required:
  libunity6
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

Also, I deleted and reinstalled my printer. Everything looks fine, but my printer state is Idle and I can't print anything, not even a test page. When I try to print something, it doesn't even show up in the print queue, it's completely blank.

---

