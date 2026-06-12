---
title: "VNCViewer tip"
date: 2006-01-18
forum: Outdated Tutorials &amp; Tips
---

### Post by irv on 2006-01-18
Just a quick tip on VNCViewer.
I didn't want to keep typing “vncviewer -fullscreen 'my server name' every time I wanted to vnc to my server so I made a little scrip and put it in **usr/bin** and named it **vnc.sh**.
The scrip has one line:
vncviewer -fullscreen wabasha-server
Replace my server name with yours and this should work for you. The next time you want to use vncviewer just go to the command line in a terminal window and type vnc.sh.

Remember you need to create this scrip as supper user (su) and this scrip is used from a Linux to Linux not windows.

---

