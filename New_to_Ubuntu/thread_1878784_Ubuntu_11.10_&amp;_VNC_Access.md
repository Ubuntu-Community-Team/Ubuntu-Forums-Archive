---
title: "Ubuntu 11.10 &amp; VNC Access"
date: 2011-11-10
forum: New to Ubuntu
---

### Post by Andy.Neenan on 2011-11-10
Hey guys, 

Completely new to Ubuntu and have been looking for a tried and tested way to get Ubuntu Desktop 11.10 accessable via VNC over a local network.

All the information I have managed to find so far seems to suggest a "Remote Desktop" option but I can't locate this - where should it be?

Failing that, a complete beginners guide on how to install a VNC server (loaded at startup) would be great.

Thanks for any help

---

### Post by sadaruwan12 on 2011-11-10
Welcome to the forum.

The easiest way to is to install Teamviwer on both PC's and allow incoming LAN connections from the options. And if you want to load it at start up add it to the start up applications.

---

### Post by dolphin194 on 2011-11-10
By default, Ubuntu installs a VNC server on your machine. You do not need to install any additional software to be able to access your computer with a VNC client. However, the VNC server is disabled by default.

You can set up your VNC server by going to your Dash Home, and typing in "Desktop Sharing." This will open your VNC server configuration. Configure it the way you want, and you will then be able to access your machine with a VNC client.

---

### Post by Andy.Neenan on 2011-11-11
> **dolphin194 said:**
> By default, Ubuntu installs a VNC server on your machine. You do not need to install any additional software to be able to access your computer with a VNC client. However, the VNC server is disabled by default.

You can set up your VNC server by going to your Dash Home, and typing in "Desktop Sharing." This will open your VNC server configuration. Configure it the way you want, and you will then be able to access your machine with a VNC client.

Thank you so much! That is exactly the option I was looking for!

Do you know how to make the VNC server load at startup? Im running it on a headless "server" and had to reboot - now I have to plug a keyboard / mouse / monitor back in to log in, before the VNC server loads up...

Thanks again!

---

### Post by dolphin194 on 2011-11-18
> **Andy.Neenan said:**
> Thank you so much! That is exactly the option I was looking for!

Do you know how to make the VNC server load at startup? Im running it on a headless "server" and had to reboot - now I have to plug a keyboard / mouse / monitor back in to log in, before the VNC server loads up...

Thanks again!

Turn on the Automatic Login option in your user accounts.

---

### Post by Muahdib on 2011-12-18
Can someone tell me how to start this vnc server at boot from the cammand line?

---

### Post by spiky001 on 2011-12-18
Is there a reason you want to use vnc dose the pc have a monitor? Have you thought about ssh

---

