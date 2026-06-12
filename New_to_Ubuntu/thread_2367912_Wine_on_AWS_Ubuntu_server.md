---
title: "Wine on AWS Ubuntu server"
date: 2017-08-04
forum: New to Ubuntu
---

### Post by oschenker on 2017-08-04
Hi guys!
I am trying to run windows app on AWS Lightsail Ubuntu server.
I have installed wine 2.0.2 and now am trying to start application.
Unfortunately, I have got message:


**Application tried to create a window, but no driver could be loaded.**
**Make sure that your X server is running and that $DISPLAY is set correctly.**


After I tried to start X server (startx) I've got a message:


**Fatal server error.**
**Parse_vt_settings: Cannot open /dev/tty0 (Permission denied)**
**...**
**xinit: giving up**
**xinit: unable to connect to X server: Connection refused**
**xinit: server error**
**Couldn't get a file descriptor referring to the console**


I am not Ubuntu user (zero experience) so I have no idea even how to diagnose the problem.
Could anyone help?

---

### Post by deadflowr on 2017-08-04
Do not post duplicate threads
see: [https://ubuntuforums.org/showthread.php?t=2367911]("https://ubuntuforums.org/showthread.php?t=2367911")
This thread is closed.

---

