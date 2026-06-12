---
title: "best way to do rdp"
date: 2012-10-11
forum: New to Ubuntu
---

### Post by fachhoch on 2012-10-11
Please advice what is the best solution for remotely working   with ubunut workstation, 
I dont know which one to choose , xrdp, vnc or something else.I tried xrdp it  has lot of issues, desktop   is missing  session menu and lot more problems, with vnc the speed is not good like rdp and also I canot get full screen like windows remote desktop connection.

---

### Post by Tralce on 2012-10-11
I would highly suggest VNC over RDP. Here: [https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)

---

### Post by TheFu on 2012-10-11
> **fachhoch said:**
> Please advice what is the best solution for remotely working   with ubunut workstation, 
I dont know which one to choose , xrdp, vnc or something else.I tried xrdp it  has lot of issues, desktop   is missing  session menu and lot more problems, with vnc the speed is not good like rdp and also I canot get full screen like windows remote desktop connection.

A few questions, before trying to answer:

[LIST]
[*]Which is the client and which is the server?
[*]Are you trying to remote into Ubuntu or remote out to some other machine?
[*]Are you on the same LAN or going across the internet?
[*]Is the internet link slow - like under 1Mbps?
[/LIST]
There is a great, secure, fast solution for LAN and another for WAN.
[http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) provides a little background and both solutions.

---

### Post by fachhoch on 2012-10-11
Which is the client and which is the server?

Client windows xp
server ubuntu workstation

Are you trying to remote into Ubuntu or remote out to some other machine?

remote into Ubuntu 

Are you on the same LAN or going across the internet?
same LAN

is the internet link slow - like under 1Mbps?

No


but vnc client I did not find it friendly like rdp. rdp I can do full screen which in  vnc I could not(I think I can do but did find one yet)

---

### Post by TheFu on 2012-10-11
On the same LAN, just use a X/Server on your Windows PC. Forget about RDP or VNC.
X/Windows is built into all UNIX/Linux desktops. On the same LAN, it works great.

You need to find an "X Server" for Windows.  I decided years ago that wasn't worth the hassle to me, so I run a small Linux VM using virtualbox on Windows. That is probably overly complex for your needs.    I haven't tried this things in years, but here's a link: [http://www.calcmaster.net/visual-c%2b%2b/xwinlogon/](http://www.calcmaster.net/visual-c%2b%2b/xwinlogon/)

If you check that link I already provided, it gives all the information.

Another option if you don't like VNC is to use NX.    

Depending on the version of Ubuntu you are running there is a newer, faster possible solution called "spice" that does sound and 3D accel for remote desktops. It is fairly advanced and non-trivial to get working, but it is designed to be used from Windows to Linux servers. [http://www.spice-space.org/](http://www.spice-space.org/)

---

