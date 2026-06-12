---
title: "Remote Desktop for 16.04 - access with TightVNC from Windows"
date: 2016-06-12
forum: New to Ubuntu
---

### Post by timg11 on 2016-06-12
I use TightVNC for remote desktop access among Windows machines. I just set up a Ubuntu 16.04 machine, and I want to access it too. I went to install TightVNC for Ubuntu, but in [this guide]("https://help.ubuntu.com/community/VNC/Servers") I discover *"Whereas most VNC servers share your desktop, tightvnc creates a completely new desktop, not attached to any actual screen"*

That's not what I want. I want to see the same screen I'd see if I was sitting at the machine. 

There are various other servers listed. Which should I use to allow the TightVNC viewer to see the current screen/monitor on the Ubuntu 16.04 system?

---

### Post by X-RED_Tech on 2016-06-12
You can use other server(s) with the TightVNC client you like. Or other clients... Or Teamviewer...

---

### Post by timg11 on 2016-06-12
I tried X11VNC per the instructions on the same page linked above. I set the password with "x11vnc -storepasswd" and then ran the example commandline to start it. 
That did not work - it rejected logins from TightVNC viewer.  But when I simply ran the command x11vnc on the Ubuntu machine, then TightVNC viewer was able to connect.  Thanks!

---

