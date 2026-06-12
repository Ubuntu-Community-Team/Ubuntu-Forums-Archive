---
title: "VNC on xubuntu 12.04"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by jwshgeek on 2012-10-16
I previously posted this in the general help forum with no replies, hoping you guys might have an answer.

I'm trying to setup an Xubuntu desktop system that will be headless for testing. I need vnc to simply show me what is on the screen of the workstation, not create a new session and I need it to be able connect to it even if it's not logged in (trying to emulate a multi-user setup for a remote client).

Any help will be much appreciated.

---

### Post by lmm5247 on 2012-10-17
> **jwshgeek said:**
> I previously posted this in the general help forum with no replies, hoping you guys might have an answer.

I'm trying to setup an Xubuntu desktop system that will be headless for testing. I need vnc to simply show me what is on the screen of the workstation, not create a new session and I need it to be able connect to it even if it's not logged in (trying to emulate a multi-user setup for a remote client).

Any help will be much appreciated.
I'm pretty sure Ubuntu comes with Vino pre-installed. Vino is a VNC server.
In the terminal, type this:
```
vino-preferences
```
You'll have to tick some boxes (see screenshot). I run Linux Mint, but it should be the same. I've tried XRDP, but it creates a new session, Vino uses the current session. However, I'm not sure if it will work with no user logged in...

---

### Post by jwshgeek on 2012-10-18
vino doesn't work at the login screen, already tried that, and I tried tightvnc, which I can make work at the login screen, but that creates it's own session

---

### Post by steeldriver on 2012-10-18
sounds like x11vnc might work for you - iirc that is the default desktop sharing app for xubuntu anyhow

[http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/](http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/)

you can use -localhost and tunnel over ssh if you want to connect securely (recommended if going outside your private LAN)

---

### Post by jwshgeek on 2012-10-18
so after installing x11vnc I ran the following,

sudo x11vnc -storepasswd yourpasswordhere /etc/x11vnc.pass
sudo chmod 744 /etc/x11vnc.pass

then  I added the following to /etc/lightdm/lightdm.conf

greeter-setup-script=/usr/bin/x11vnc -auth /var/run/lightdm/root/:0 -noxrecord -noxfixes -noxdamage -rfbauth /etc/x11vnc.pass -forever -bg -rfbport 5900 -o /tmp/x11vnc.log

I've tested it with logouts and reboots and it works fine with one minor flaw of disconnecting the active connection when you log out and having to reconnect once its at the login screen

---

