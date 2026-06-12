---
title: "Gnome Panel issue"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by jerrallan on 2008-05-09
I have Hardy.  I lost both panels. Since I couldn t access anything, I went into recovery mode. I did an apt-get install gnome-panel.

The panel was restored upon reboot, but now I get an error message:The panel encountered a problem while loading OAFFIID:Gnome_FastSwitcherUserApplet"

It asks do I want to delete. Do I?

Apparently, I ran into problems when I deleted two libraries [libgweather] I didn t think I would need. I got these messages when I was in recovery mode

Thanks

---

### Post by scragar on 2008-05-09
makes no difference, delete it and you can add it again in a few secs. With keeping it you may have problems displaying the panels...
run```
sudo apt-get install -f
```to fix the problem from any terminal you can get your hands on to fix the applet.

---

### Post by jerrallan on 2008-05-09
sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfreebob0 python-zopeinterface libjack0 unixodbc libfltk1.1
  odbcinst1debian1 libmikmod2 libgavl0 python-setuptools python-pkg-resources
  libpq5 jackd libquicktime1 gstreamer0.10-gnonlin libfaad0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

 The bottom and top panels were installed. I had to add display windows and switch window. When I try to reinstall the trash can, I get error message:problem encountered with Gnome Panel Trash Applet. 

I get two error messages every time I reboot

Well, I solved the problem by doing what I did not want to do. I reinstalled 8.04.  It would take less time that finding out how to resolve the applet issue.  That libgweather app that I deleted must have deleted some dependencies that caused the applet problem.  Reinstilling the weather apps didn't fix the problem though.

---

