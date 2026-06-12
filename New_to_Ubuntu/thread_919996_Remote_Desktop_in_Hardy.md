---
title: "Remote Desktop in Hardy"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by dmg412 on 2008-09-14
I am attempting to have a headless server running ubuntu.  After going to System -> Preferences -> Remote Desktop, we can now connect to the computer using vncviewer computer-name:0

This is currently running really slow.  I was wondering if there was a way to change the color depth on the server.  If I change the xorg.conf file, vnc no longer works and will not let you connect.  I have also tried to connect using vncviewer -depth 8 computer-name:0 and it still uses 32 bits for colors.

Is there anyway to change the color settings so vnc will work faster without the refresh delay?

How do you change the default color settings for the server after enabling it through System -> Preferences -> Remote Desktop?

There will be some windows machines and ubuntu machines connecting to this computer.

Please help me out, as I am new to vnc.

---

### Post by nhasian on 2008-09-14
hello dmg412,

try playing with the -compresslevel and -depth command line options.  for more info, try 
```
man vncviewer
```

---

