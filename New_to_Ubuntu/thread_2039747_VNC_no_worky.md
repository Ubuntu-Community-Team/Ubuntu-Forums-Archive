---
title: "VNC no worky"
date: 2012-08-09
forum: New to Ubuntu
---

### Post by Slownis on 2012-08-09
I'm trying to VNC to my old desktop, running Ubuntu 11.10 with  LXDE desktop enabled.  The laptop client has Ubuntu 11.10 also running gnome 3 desktop environment.  When ever I try to remote to the old desktop, no connection is made.

I am able to remote the other way via VNC.

This used to work, but one day I was messing around and installed SSH on the desktop and it hasn't worked since.   I have since tried to remove SSH.

I'm not even sure what else info I need to provide.  any help is greatly appreciated.

---

### Post by steeldriver on 2012-08-09
Do you have a vnc log on the desktop side (usually in ~/.vnc) that sheds any light on your connection attempts?

Did you maybe set the vnc server to run with -localhost (to force ssh tunneling) when you installed ssh? try

```
ps -ef | grep vnc
```

to see what parameters it's being invoked with

---

### Post by Slownis on 2012-08-09
> **steeldriver said:**
> Do you have a vnc log on the desktop side (usually in ~/.vnc) that sheds any light on your connection attempts?

Did you maybe set the vnc server to run with -localhost (to force ssh tunneling) when you installed ssh? try

```
ps -ef | grep vnc
```

to see what parameters it's being invoked with

Returned nothing.  So apparently I'm not running a vnc server. Face palm. What packages should I install, or what settings do I set?

---

### Post by Slownis on 2012-08-09
More info:  Ubuntu software center does show that I have the 'desktop sharing' checked, but I can't seem to find how to envoke it from Lubuntu desktop.

---

### Post by steeldriver on 2012-08-09
sorry not much help here - I've never done it through the GUI, I've always invoked it via the command line

---

### Post by Slownis on 2012-08-09
command line works for me.....?

---

### Post by steeldriver on 2012-08-09
OK so it depends a bit exactly what you want to do:

1. (easiest) log in normally at the physical machine, and run x11vnc as user on display :0 so that you (or - optionally - anyone else with your vnc password) can connect to and share the same display remotely - something like this *should* work (you may need to set a vnc password with x11vnc -storepasswd if you didn't already)

```
x11vnc -rfbauth ~/.vnc/passwd -rfbport 5900 -display :0 -shared -forever -nowf -norc -notruecolor -bg -xkb 
```2. (more complicated) set up x11vnc to start from the lightdm session so you can do all of the above but also log in remotely via VNC rather than having to start it at the physical machine

[http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/](http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/)

3. run a completely separate X server / display rather than connecting to the 'real' desktop - I've played with this using tightvncserver and my work server is set up to do it but I don't know much more than that 

If you are doing ANY of these outside of a NAT-firewalled LAN, I would STRONGLY recommend ssh tunneling.

---

### Post by Slownis on 2012-08-10
> **steeldriver said:**
> OK so it depends a bit exactly what you want to do:

1. (easiest) log in normally at the physical machine, and run x11vnc as user on display :0 so that you (or - optionally - anyone else with your vnc password) can connect to and share the same display remotely - something like this *should* work (you may need to set a vnc password with x11vnc -storepasswd if you didn't already)

```
x11vnc -rfbauth ~/.vnc/passwd -rfbport 5900 -display :0 -shared -forever -nowf -norc -notruecolor -bg -xkb 
```2. (more complicated) set up x11vnc to start from the lightdm session so you can do all of the above but also log in remotely via VNC rather than having to start it at the physical machine

[http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/](http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/)

3. run a completely separate X server / display rather than connecting to the 'real' desktop - I've played with this using tightvncserver and my work server is set up to do it but I don't know much more than that 

If you are doing ANY of these outside of a NAT-firewalled LAN, I would STRONGLY recommend ssh tunneling.

Thank you so much, I got solution 1 working.  My goal is solution 2, but so far that's a bust.  Question:  if I leave my desktop logged in upstairs, should the vnc server still be running?  Or is only running from the lightdm screen?

---

### Post by steeldriver on 2012-08-10
when invoked with the -bg -forever options it should stay running until you either log out or kill the X session/server I think

iirc option (2) worked for me right out of the box - although I have since altered it to add -localhost to the command line (to require ssh tunneling)

---

