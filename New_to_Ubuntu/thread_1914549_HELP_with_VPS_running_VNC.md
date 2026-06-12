---
title: "HELP with VPS running VNC"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by neophytemessiah on 2012-01-24
Ok first off i'm totally new to Ubuntu. I'm going to school and I have a pc desktop which i'm not allowed to install Ubuntu on. So I got a vps at 1and1 and have ubuntu 10.04 LTS minimal system installed on it. What i'm wanting to do is set up a VNC so I can access the server and use it like a desktop through my browser on what ever computer I am on. I know it is possible i've read alot of the stuff on google and I am using this guide [http://anhblog.net/pc-place/setup-ubuntu-vps-as-a-vnc/](http://anhblog.net/pc-place/setup-ubuntu-vps-as-a-vnc/)  to try and get it done. The problem is when I get to the section about sudo nano ~/.vnc/xstartup it tells me sudo: nano: command doesn't exist. Also the part below that says to add the line gnome-session & to the xstartup but I don't know how to add the line. I'm using putty to connect.  I know the guide i'm using is an old one so I was wondering if there is a new guide that anyone knows so I can try to get this done? Please? Anyone? :confused:

---

### Post by /bin/sh on 2012-01-24
Maby nano isn't installed:
```

sudo apt-get install nano

```

---

### Post by neophytemessiah on 2012-01-24
thankyou I will try that

---

### Post by haqking on 2012-01-24
> **neophytemessiah said:**
> thankyou I will try that

Allowing VNC over the internet is like smashing your machine with a hammer ;-)

VNC should only be used for LAN only IMO.

ssh is preferred for remote admin/connectivity to a Linux box and is inherently more secure.

Or something like Teamviewer if you want a easy and GUI interface.

Cheers

---

### Post by Cheesemill on 2012-01-24
Whatever you do, don't setup a VNC connection that's accessible from the internet.

Look into SSH forwarding instead, an open VNC will be cracked in minutes.

Also most VPS's that I have used will have problems if you try and install X. Most of them are meant for command line access only.

---

