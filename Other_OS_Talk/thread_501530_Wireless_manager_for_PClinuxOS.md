---
title: "Wireless manager for PClinuxOS"
date: 2007-07-15
forum: Other OS Talk
---

### Post by jamieh on 2007-07-15
I noticed that PClinuxOS doesn't come with a good WiFi manager, I just hate Kwikimanager, is it possibe to install Ubuntu's Network Manager to PClinuxOS, or is there another good EASY-TO-USE wifi manager?

---

### Post by ThinkBuntu on 2007-07-15
> **jamieh said:**
> I noticed that PClinuxOS doesn't come with a good WiFi manager, I just hate Kwikimanager, is it possibe to install Ubuntu's Network Manager to PClinuxOS, or is there another good EASY-TO-USE wifi manager?
I believe NetApplet was originally developed by Mandriva, so it may be a good fit. Note that it's no longer maintained or developed, though. KNetworkManager's the obvious choice, and is under active development by SUSE. Most distros bundle this as the network manager.

---

### Post by ThinkBuntu on 2007-07-15
Actually, you have a good point: Neither KNetworkManager nor NetApplet are available in the main repository via Synaptic. For us warchalkers (going onto open networks) having to use the Control Center all the time, along with typing in the root password, is a pain.

On an unrelated note, I'm working on lightifying my PCLOS installation, and then remastering the ISO for personal use. Normaly, I'd choose Ubuntu or a similar distro to remaster, but PCLOS' speed and out-of-the-box configuration really lend it to this. Should be useful along with dyne:bolic when I'm on the go, and would be a nice go-to for people I know who prefer, say, Abiword to OpenOffice.

---

### Post by ThinkBuntu on 2007-07-15
Actually, I'm mistaken. NetApplet is hidden in PCLOS. To find it, go to: KMenu>System>Monitoring>NetApplet.

Right-click the applet, go to Settings, and check off "Always launch on startup"

---

### Post by Stew2 on 2007-07-16
> **ThinkBuntu said:**
> Actually, I'm mistaken. NetApplet is hidden in PCLOS. To find it, go to: KMenu>System>Monitoring>NetApplet.

Right-click the applet, go to Settings, and check off "Always launch on startup"

Sweet! :D Thanks for the info ThinkBuntu, I was looking for a network monitor and couldn't find one. This works great!

---

### Post by b9anders on 2007-07-19
it's there, but when I used PCLOS a few months back it didn't work. Kept crashing on me - might have been fixed since though.

---

### Post by floflooo on 2007-12-24
> **ThinkBuntu said:**
> Actually, I'm mistaken. NetApplet is hidden in PCLOS. To find it, go to: KMenu>System>Monitoring>NetApplet.

Right-click the applet, go to Settings, and check off "Always launch on startup"

Thanks ThinkBuntu, it was useful.
For it to work though, I had to modify the ~/.net_applet file, replacing "false" by "true", and then restarting my session.

---

### Post by intrepion on 2008-04-14
> **floflooo said:**
> Thanks ThinkBuntu, it was useful.
For it to work though, I had to modify the ~/.net_applet file, replacing "false" by "true", and then restarting my session.

Thanks floflooo!  That was exactly what I needed!  :D

---

### Post by MONODA on 2008-04-15
tryt wicd

---

### Post by quickshade on 2008-04-15
PCLinuxOS is great and fast distro, but they lack some of the things that some of the major Distros have: Including an update checker, network applet and some other things. But overall it's a great distro.

---

