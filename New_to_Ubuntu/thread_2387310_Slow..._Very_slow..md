---
title: "Slow... Very slow."
date: 2018-03-17
forum: New to Ubuntu
---

### Post by shyler-casavant on 2018-03-17
Hello all,

Installed 16.04.4 (Unity) to an Intense PC. i7, 16GB, SSD. It's using an Ethernet connection. I VNC into it; on my LAN, Not across the internet... It's slower than any computer I've ever seen. Any ideas? 

It's like... Windows XP on a Windows 95 box slow lol.

---

### Post by TheFu on 2018-03-17
Unity wants direct access to 2D and 3D accelerated GPUs.  VNC doesn't provide that.  By using a different DE, perhaps XFCE or LXDE or Mate, you will get good performance.  If you want better, more secure performance, might I suggest using x2go instead of VNC?  x2go is 2-3x faster than VNC, IMHO. x2go doesn't like Unity either.

There is a Unity fallback mode ... I've never used it.

---

### Post by ubname on 2018-03-18
> **shyler-casavant said:**
> Hello all,

Installed 16.04.4 (Unity) to an Intense PC. i7, 16GB, SSD. It's using an Ethernet connection. I VNC into it; on my LAN, Not across the internet... It's slower than any computer I've ever seen. Any ideas? 

It's like... Windows XP on a Windows 95 box slow lol.

Hi I use to remotely connect to Ubuntu 16.04 and it works not as slow or very slow as in your case, how I do it:

1 use the standard tools that Ubuntu 16.04 offer "Desktop sharing" (probably based on vnc but it just works)

2 (fully updated Ubuntu 16.04 for this) Use Unity Low Graphics Mode with this line:

```
gsettings set com.canonical.Unity lowgfx true
```

reboot

3 As a client use included Remmina 

4 Gigabit LAN and you (almost) forget you're in a remote session

5 disable encryption it you fell like going even faster,[U] only if your LAN is trustworthy of course
[/U]

HTH

---

### Post by TheFu on 2018-03-18
[https://www.omgubuntu.co.uk/2017/04/unity-low-gfx-mode-toggle](https://www.omgubuntu.co.uk/2017/04/unity-low-gfx-mode-toggle) says the lowgfx is for 17.10 and later.  Hopefully, the low graphics stuff was backported and works correctly on 16.04.  Sounds like ubname is confirming that. Nice.

The good thing about VNC is there are lots and lots of different clients from almost every platform.  That's great if you have a tablet. x2go only has clients for Windows, OSX and Linux, which can be limiting.

But security for VNC is weak. On a home LAN, that might not be too big a concern. There is a --localhost option for vncserver ... to only allow connections from localhost, which effectively forces either a VPN or ssh-tunnel to be used.

---

### Post by ubname on 2018-03-18
> **TheFu said:**
> [https://www.omgubuntu.co.uk/2017/04/unity-low-gfx-mode-toggle](https://www.omgubuntu.co.uk/2017/04/unity-low-gfx-mode-toggle) says the lowgfx is for 17.10 and later.  Hopefully, the low graphics stuff was backported and works correctly on 16.04.  Sounds like ubname is confirming that. Nice.



Yes it works on 16.04, and I use it so I can confirm 100%.

---

### Post by ank2 on 2018-03-18
If all other suggestions here fail, have an ssh server (openssh) on the other machine and the ssh client on you local machine installed. The a 

ssh -X REMOTE_IP some_app

with REMOTE_IP being its IP and some_app the application youi want to run, should grant a faster connection. Well not faster, but less data being tranfered, so "faster". :-)

---

### Post by TheFu on 2018-03-18
+1 - Excellent point ank2!

ssh -X is my preferred method when I'm on the SAME LAN and have a 100mbps connection or higher.  While you can run a remote desktop, most people just run remote applications. ssh handles setting the DISPLAY for us and provides an encrypted tunnel for the X11 traffic.  Not sure if this will work under Wayland (17.10), but it will work on anything running both ssh and X11 all the way back to 1994-ish, unless the ssh settings prevent it.

I use this for remote GUI terminals on other systems (still on the same LAN).  Out of 10 currently open windows, only 3 are local.

It is also possible to mix and match each of these methods ... so when I'm traveling and want a remote desktop (I leave all important files at home), then I'll use x2go to get to my LAN, then treat everything like it is local - rdp to Windows, X11 via ssh to other local systems, ... or VNC to a BSD system that can't run x2go (assuming I need more than normal X11).

While I don't do it, others use x2go to connect to other local systems via x2go.  It does have a GUI that is pretty intuitive, while also using ssh tunnels (part of the NX protocol) and providing real control over the compression and colors used to make even ISDN connections workable. I've used x2go from 5 continents.  It works well for office applications.

---

