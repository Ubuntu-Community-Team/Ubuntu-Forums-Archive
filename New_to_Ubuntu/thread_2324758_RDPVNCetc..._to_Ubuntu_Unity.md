---
title: "RDP/VNC/etc... to Ubuntu Unity"
date: 2016-05-16
forum: New to Ubuntu
---

### Post by oisin-kenny on 2016-05-16
Hello,

I am a beginner with Ubuntu, and I like it.

I enjoy using  powerfulish machine with a few thin clients to access it - this is how I have worked with Windows in the past.

Is there any way to use RDP or VNC or something similar without changing the desktop GUI to something else?

Thank you!

p.s. I'm using Ubuntu 16.04

---

### Post by TheFu on 2016-05-16
Unity requires 3D-accel GPU access. That is a design decision made by Canonical to provide the best possible experience for console users, but creates an issue for any remote access methods.  While there may be a way, I don't know about it.

The way that I access remote applications it is explained here:  [http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)
TL;DR
1) on the same LAN, use X11 over ssh.   ssh -X userid@IP application-to-run &
2) over the internet, use X2go with a lite GUI (not unity). Unity is NOT supported under x2go according to the x2go pgs. [http://wiki.x2go.org/doku.php/doc:de-compat](http://wiki.x2go.org/doku.php/doc:de-compat) - read the parts about Unity and other Compositing solutions.

p.s. 16.04 will have less-than-great support for about another 6 months by other teams. On 14.04, x2go is the best, most secure, fastest, most efficient, remote desktop solution, by far. rdp and vnc are 2-3x slower.

---

