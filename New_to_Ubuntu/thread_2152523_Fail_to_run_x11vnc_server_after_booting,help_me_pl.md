---
title: "Fail to run x11vnc server after booting,help me please!"
date: 2013-06-08
forum: New to Ubuntu
---

### Post by huangchenmin on 2013-06-08
Dear all:
I installed Lubuntu+LXDE on Acer notebook TravelMate 612TXV, and set auto login after booting.
Reference by this [article]("http://ubuntuforums.org/showthread.php?t=1868554") from web, I fail to make x11vnc server execute automatically after booting.
Following are those I did:
1.sudo nano /etc/lxdm/lxdm.conf&#65292;saved xauth_path=~/.Xauthority to lxdm.conf.
2.sudo nano /etc/lxdm/PostLogin&#65292;saved following to PostLogin.
!/bin/sh
# X11VNC AutoStart
sudo x11vnc -auth /tmp/.Xauth1000 -forever -rfbport 5900
3.sudo x11vnc -storepasswd Password /etc/x11vnc.pass
4.sudo nano /etc/lxdm/PostLogin&#65292;modified last row as following and saved&#12290;
sudo x11vnc -auth /tmp/.Xauth1000 -forever -rfbauth /etc/x11vnc.pass -rfbport 5900

I wonder if x11vnc really represent x11vnc server?
where did I go wrong actually? Please help!
I thank you in advanced.
chenmin

---

### Post by gordintoronto on 2013-06-08
I don't know Lubuntu, but most *buntus have a "startup programs" GUI, which is the place to put what you want to do.

Did you run: man x11vnc

If you open Terminal and run: x11vnc
does anything happen?

---

