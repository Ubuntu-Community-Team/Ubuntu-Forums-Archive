---
title: "ubuntustudio-audio problem..."
date: 2008-11-01
forum: New to Ubuntu
---

### Post by jackgu1988 on 2008-11-01
I installed today ubuntu studio over ubuntu 8.10 and when I try to install packages that require ubuntustudio-audio... well I just can't... So I try to remove ubuntustudio-audio... and I can't!!! :(

> jack@jack-laptop:~$ sudo apt-get remove ubuntustudio-audio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  ubuntustudio-audio
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 53.2kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 257398 files and directories currently installed.)
Removing ubuntustudio-audio ...
Traceback (most recent call last):
  File "/usr/share/ubuntustudio-audio/rtprio.py", line 3, in <module>
    import changesettings
ImportError: No module named changesettings
dpkg: error processing ubuntustudio-audio (--remove):
 subprocess pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/share/ubuntustudio-audio/rtprio.py", line 3, in <module>
    import changesettings
ImportError: No module named changesettings
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ubuntustudio-audio
E: Sub-process /usr/bin/dpkg returned an error code (1)

I also tried synaptic but still nothing... I am confused... what should I do?

---

### Post by jackgu1988 on 2008-11-04
anybody?:confused:

---

