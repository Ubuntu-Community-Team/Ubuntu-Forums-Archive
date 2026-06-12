---
title: "3d Games Don't Run"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by boho103 on 2008-06-15
I have installed my ati drivers through a tutorial and I'm on hardy 8.04, and I have an ATI radeon x1400 installed, and I have 2 gigs of ram. Yet I cannot run 3d games, or they do run but at extremely low framerate. I have posted this problem before except I haven't had a new reply in over about 2 weeks. I tried disabling compiz and I tried uninstall and reinstalling my drivers but it didn't work. Please help, and if you could direct me through it Via AIM, that would be extremely helpful, can anybody help please? I followed this tutorial, [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide). Method 2, anybody know any other drivers I could maybe use that would work?

---

### Post by markharding557 on 2008-06-15
did you try method1 and did you restartx or reboot i had same problem untill doing that

---

### Post by boho103 on 2008-06-15
Oh no I didn't, thanks I'll try that!
Should I uninstall my current drivers and then do that?

---

### Post by boho103 on 2008-06-15
FIXED!
I did this
sudo apt-get remove xserver-xgl
and it fixed all my problems :DD

---

