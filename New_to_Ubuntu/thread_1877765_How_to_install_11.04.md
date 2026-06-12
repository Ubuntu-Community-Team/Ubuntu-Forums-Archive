---
title: "How to install 11.04?"
date: 2011-11-08
forum: New to Ubuntu
---

### Post by Nixarter on 2011-11-08
I want to revert to 11.04 from 11.10.  I had to download the windows wubi installer last time to get it to work (to initially install 11.10), BUT now it doesn't seem to want to work for 11.04.  It says at the top "You are about to install Ubuntu 11.10"... and I can't see where to change it.  Last time I just had the iso in the same folder, but now it is insisting on using 11.10, even though I have the 11.04 iso in the folder.  How can I fix this?


My previous thread for 11.10: [http://ubuntuforums.org/showthread.php?t=1863740](http://ubuntuforums.org/showthread.php?t=1863740)

---

### Post by Nixarter on 2011-11-08
I checked the log file, and it apparently searches for 11.10 isos,  wherever they are first.  So, I had to move the 11.10 iso to an external  drive, then physically remove it.  This didn't work, as it didn't try  to find the 11.04.  So, I renamed the 11.04 iso to the 11.10 iso name,  then it failed and the log file returned this:

```
11-08 15:24 DEBUG  CommonBackend: Searching for local ISO
11-08 15:24 DEBUG  Distro:   checking Ubuntu ISO C:\Users\User\Desktop\UbuntuISO\ubuntu-11.10-desktop-i386.iso
11-08 15:24 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\User\Desktop\UbuntuISO\ubuntu-11.10-desktop-i386.iso
11-08 15:24 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
11-08 15:24 DEBUG  Distro:   parsed info={'name': 'Ubuntu',  'subversion': 'Release', 'version': '11.04', 'build': '20110427.1',  'codename': 'Natty Narwhal', 'arch': 'i386'}
11-08 15:24 DEBUG  Distro: wrong version: 11.04 != 11.10
```

The error it spits out complains about an "unscriptable object" (which,  obviously, is not what the problem was, according to the log file).

Any ideas?

Would using a hex editor to change those values make it work?  Or would it just break the install?

---

### Post by Nixarter on 2011-11-08
I finally found the solution.  Apparently, each release has its own specialized wubi installer, and I found the one for 11.04 here: [http://releases.ubuntu.com/11.04/](http://releases.ubuntu.com/11.04/)  (It is at the very bottom, named wubi.exe)

releases.ubuntu.com has similar resources for other releases as well.

---

