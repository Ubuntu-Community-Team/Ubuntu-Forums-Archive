---
title: "Vnc"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by DoubleMcLovin on 2008-10-05
I know theres Krfb in the k-menu, and while thats well and fine, I noticed one fatal flaw in that during the initial setup: the password restriction. It is only allowing my 9 characters as a password, where as my target password that I'm using on the other 4 computers in my house running a VNC server is about 24 characters. Is there any way to get around this limitation? Or perhaps another program I can install to substitute?

---

### Post by jamesrl on 2008-10-05
I'll suggest a different vncserver like x11vnc (even if you are in kubuntu) as it won't have that design flaw.
See: [http://ubuntuforums.org/showthread.php?t=196572]("http://ubuntuforums.org/showthread.php?t=196572")

---

### Post by DoubleMcLovin on 2008-10-05
Thanks, I got an error when I tried to install vncserver, but did a apt-cache search vnc | grep serve command and found vnc4server, assuming thats the same??

---

