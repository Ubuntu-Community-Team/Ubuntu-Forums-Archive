---
title: "x11vnc not starting at startup"
date: 2013-04-21
forum: New to Ubuntu
---

### Post by mcapri76 on 2013-04-21
I was wondering if anyone is able to help. I've setup remote access to my Ubuntu server following this post: [http://ubuntuforums.org/showthread.php?t=1622843](http://ubuntuforums.org/showthread.php?t=1622843)

 In the end this is what worked for me: x11vnc -rfbversion 3.6 -rfbport 5907 -rfbauth /home/rick/.vnc/passwd -forever -bg

 One problem is when I set the command in 'Startup applications' it does not work, the only way to make it work is to manually sudo su once logged in and run the command above.
 I followed a guide to run x11vnc as root (sudo visudo) but it did not work. Any idea?

---

### Post by mcapri76 on 2013-05-08
Anyone ?
;)

---

