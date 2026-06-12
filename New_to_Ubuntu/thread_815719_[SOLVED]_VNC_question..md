---
title: "[SOLVED] VNC question."
date: 2008-06-01
forum: New to Ubuntu
---

### Post by sp00ner on 2008-06-01
I want to be able to remote my Win2k computer from my Ubuntu laptop. At work, I use a program from Pointdev called Ideal Amin to remote WinXP desktops from a WinXP desktop. It is nice because there doesn't need to be any client on the remote workstation. It sends a tightvnc client on the fly (I believe) to the remote workstation if it is the first time you are connecting to it. This is the functionality I am looking for at home. Any thoughts on what I need to install on my laptop to do this?

---

### Post by diablo75 on 2008-06-01
You can use TightVNC for Windows.

[http://www.tightvnc.com/](http://www.tightvnc.com/)

Setup your server to run in the background (There's a way to actually make this a service that auto loads on boot if you want).  The next good thing to have is a router with DynDNS.org capability.  Then finally, you'll have to set your router up for port forwarding port 5900 to that PC, and you should set that PC to have a static IP address.  But if you don't have a router, you won't have to worry about this stuff...you can just go off of the IP your ISP is assigning your computer via the modem (but check it daily, because it will likely expire and you'll get a slightly different address).

Good Luck!

---

### Post by sp00ner on 2008-06-01
OK, that worked great. Now my problem is that I am remoted to my win2k desktop in full screen mode and I dont know te hot key to break out of it....help :lolflag:

---

### Post by diablo75 on 2008-06-02
Try F8.  That usually brings up a hidden menu you can use to disable fullscreen mode.

---

### Post by buntu_Geek on 2008-06-02
Alt+Tab .... swtiches between minimized windows in the task bar...

---

### Post by sp00ner on 2008-06-02
I tried Alt-Tab but it was only Alt-Tabing in Windows. Diablo's solution worked like a champ. Thanks to all for responding.

---

### Post by bengoza on 2008-06-15
This is sort of related: I exited out of the terminal session in vncviewer using the exit command (I wanted to see what was under it), and now can't get it back. It's pretty useless if you don't have a terminal.

---

