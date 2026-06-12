---
title: "What is this SSH?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by FleetAdmiral74 on 2008-05-03
I've been using Kubuntu for over a year now, and during that time have read a ton of comments about SSHing to remote control your PC, or something to that effect. I know a little about SSH, its something related to a secure, remote protocol, so you can remotely manage your PC. 

*Question section*
Do you recommend any good starter-guides for this topic? I'm no Linux expert, (obviously), but I like to kinda know whats going on underneath.  
How easily is this done from a Windows computer, instead of another Linux box?
To what degree of control do you  have? As in, can you control the mouse, seeing your desktop, or its it more CLI-ish. 

Just looking for a nice introduction, thanks for your time!

---

### Post by scorp123 on 2008-05-03
Sorry and I don't mean to be rude, but this is really something you could have easily found out if you had used Google or Wikipedia.

[http://en.wikipedia.org/wiki/Secure_Shell](http://en.wikipedia.org/wiki/Secure_Shell)

---

### Post by SunnyRabbiera on 2008-05-03
Yeh secure shell needs the terminal I am afraid

---

### Post by scorp123 on 2008-05-03
> **SunnyRabbiera said:**
> Yeh secure shell needs the terminal I am afraid Not necessarily. See the Wikipedia article above. Depending on what you do you get a terminal session, or access to the remote system's filesystem, or you access the remote system's desktop... It isn't really that hard. And the forums here are full of tutorials. You'd just need to make use of the "search" function ;)

---

### Post by aktiwers on 2008-05-03
I use SSH through nautilus too.
Places => Connect to server
And pick SSH :)

---

### Post by scorp123 on 2008-05-03
> **aktiwers said:**
> I use SSH through nautilus too.
Places => Connect to server
And pick SSH :) Exactly. And that's just one way to use it. What I do e.g. with some friends who I have converted to Ubuntu is that I tunnel VNC through SSH so I can help them if they encounter problems.

---

### Post by Joeb454 on 2008-05-03
I don't think SSH can literally display the desktop of the remote PC, you can have X Forwarding however, which allows you to run GUI app's over SSH.

If you want remote control with mouse and screen et al. You need to look into VNC :)

---

### Post by PeterJS on 2008-05-03
> **Joeb454 said:**
> I don't think SSH can literally display the desktop of the remote PC, you can have X Forwarding however, which allows you to run GUI app's over SSH.

If you want remote control with mouse and screen et al. You need to look into VNC :)

It can be done. It's a bit of a hack, but I've run a full on Gnome session over X forwarding. If you set up a nested Xephyr session and Forward X in to that, you can launch nautilus and gnome-panel which between the two of them should start all the usual Gnome services in your nested session. You'll want a really good connection, because running that many apps over X forwarding isn't quick.

```

user@Local:~$ Xephyr :1 -ac -screen 800x600 &
user@Local:~$ DISPLAY=:1 ssh user@host -X
user@Remote:~$ metacity &
user@Remote:~$ gnome-panel &
user@Remote:~$ nautilus -n &

```

---

### Post by StOoZ on 2008-05-03
a good place to start
[https://help.ubuntu.com/community/AdvancedOpenSSH]("https://help.ubuntu.com/community/AdvancedOpenSSH")

---

### Post by lazyart on 2008-05-03
> **Joeb454 said:**
> I don't think SSH can literally display the desktop of the remote PC, you can have X Forwarding however, which allows you to run GUI app's over SSH.

If you want remote control with mouse and screen et al. You need to look into VNC :)

Correct.. but you can use SSH to secure your VNC session.  VNC, by default, is wide open.

---

