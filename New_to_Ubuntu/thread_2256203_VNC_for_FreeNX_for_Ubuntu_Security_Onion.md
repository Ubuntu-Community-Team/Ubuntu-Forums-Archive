---
title: "VNC for FreeNX for Ubuntu Security Onion"
date: 2014-12-10
forum: New to Ubuntu
---

### Post by numan2 on 2014-12-10
I installed Security Onion on a server... it's linux based and its used for IDS.  It already has a GUI.  Do I still need to install VNC for FreeNX on the box?

I was following the instructions here: [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)
but I didn't say if it would work for 12.04 security onion.

Please help!

---

### Post by TheFu on 2014-12-10
It sounds like you are new to Linux and X/Windows.

If it already has a GUI, then why not just use that?
If you want remote access to the server, there are many ways: [http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)
That article is dated - for 12.04, freenx is ok, but for 14.04, I've switched to x2go for secure, remote, desktops ... when necessary.  On the LAN, normal X/Windows display management is fine, it is only when on the internet that I feel the extra security for x2go is needed.

I avoid RDP and VNC - security for those is poor and requires a VPN before using if you don't want to be hacked.

If anything isn't clear, ask.

---

