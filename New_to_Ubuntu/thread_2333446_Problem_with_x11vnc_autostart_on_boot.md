---
title: "Problem with x11vnc autostart on boot"
date: 2016-08-10
forum: New to Ubuntu
---

### Post by dudongwtf on 2016-08-10
Hi, I just installed x11vnc on my Lubuntu 16.04 but can't managed to set it up on boot. I did this step on Lubuntu 12.04 and it worked everytime. But in 16.04, it is not. Here are my steps installing x11vnc on my Lubuntu 16.04. Please help me figure out what went wrong. I managed to connect via UltraVNC (Windows7) but when I close the terminal, It will disconnect.

> 1.Install packages
sudo apt-get install x11vnc vnc-java
1. Set up password to allow clients to view
x11vnc -storepasswd
2. Open up ports 5800 and 5900 on your firewall
3. Run this command:
x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800
At this point I realised that the connection is temporary - at reboot you loose 
the connection and have to restart it - so to have VNC start at boot:-
4. Add the command from 4) to your sessions, so that it starts at each login.
This is how you do 5)
Open terminal window
Accessories/LXterminal in command terminal type:
sudo leafpad /etc/xdg/lxsession/Lubuntu/autostart (note use of upper case) 

You will be prompted for you user password

Autostart will open 

Add at bottom of list
@x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800
Save and close. Test by rebooting - that should work

---

### Post by cmcanulty on 2016-08-10
This works for me in multiple xubuntu 16.04 machines.It is because of the new systemd that runs services instead of the old init (I think) I expect it will work in Lubuntu. If you have issues get back to me as I have done it a lot.

[http://c-nergy.be/blog/?p=8984]("http://c-nergy.be/blog/?p=8984")

---

### Post by dudongwtf on 2016-08-11
Hi Sir cmcanulty

This script worked like a charm!!! Thanks x100 Sir.

---

