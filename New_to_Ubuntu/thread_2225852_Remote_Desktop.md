---
title: "Remote Desktop"
date: 2014-05-23
forum: New to Ubuntu
---

### Post by thault on 2014-05-23
How do I go about remote desktopping into a xubuntu 12.04. I have a windows 7 computer. Also what would I need to do to enable this remote desktop to connect from outside the network. Thanks for the help!

---

### Post by cariboo on 2014-05-25
[Teamspeak]("http://www.teamspeak.com/") works for many users, I just didn't like the nag notice

---

### Post by steeldriver on 2014-05-25
There are so many options and opinions out there that it's difficult to answer concisely

For Xubuntu, the canonical (with a small 'c') way of doing it would probably be to install and configure x11vnc, and install a 3rd party VNC client such as UltraVNC or TightVNC on the Windows box. Within your LAN that should be all you need to do - if you want to connect from outside the LAN then you will want to configure it ONLY to connect via an SSH tunnel, for security (as well as all the other stuff i.e. static IP / port forwarding etc.)

There are other VNC servers such as vino-server (but that may drag in a bunch of gnome dependencies). There is also xrdp, which uses the Microsoft RDP protocol and therefore can be used via Windows native Remote Desktop Connection instead of requiring a 3rd party viewer. However since VNC is the native *nix protocol, it is somewhat better supported from the server side. 

There is also FreeNX which uses SSH by default and supposedly provides better compression (i.e. better for lower bandwidth connections). I haven't used it (yet) but it's probably the way I'd go if starting from scratch today.

A good overview is --> [https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)

---

### Post by Quarkrad on 2014-05-25
Have you looked Teamveiwer?  This is what I use.

---

### Post by charlieprime on 2014-08-02
TeamViewer would not install in Xubuntu 14.04.1

---

### Post by Martinjo84 on 2014-08-02
Install the 32bit


wget download.teamviewer.com/download/teamviewer_linux.deb
sudo dpkg -i teamviewer_linux.deb
sudo apt-get install -f

---

### Post by Paulgirardin on 2014-08-02
I use Remmina to connect to my MythTV box

---

### Post by WB0HYQ on 2014-08-04
Windows already has remote desktop connection software.  I use 'mstsc.exe' which is located in "\windows\System32".  Using this, I connect from my Win7 machine to all my Ubuntu machines (which run 'xrdp').  I took me a few retries to get the connections set up, but once that happened, I was able to connect just fine.

Bill

---

