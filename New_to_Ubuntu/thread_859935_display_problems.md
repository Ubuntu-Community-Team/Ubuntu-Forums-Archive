---
title: "display problems"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by Fierylightness on 2008-07-15
hi when i turn on my computer it loads up to the part when it is supposed to load with the loading bar then the screen goes blank and says change screen resolution to 1280x756 60hz it then goes onto the login screen and works fine is there anyway to stop it saying this? as it is quite annoying.

p.s i tried changing resolution but still says same thing

---

### Post by cmnorton on 2008-07-15
It sounds like you are going to have to play with your display. There is a good way to do it, but it takes time. I boot into recovery mode, and dpkg-reconfigure xserver xorg. Usually if you take the default answers and then put in the screen resolutions you want, you should be okay. If you have a driver problem, this gives you the chance to use a different driver.

This program causes a saved copy of the /etc/X11/xorg.conf file to be created, so you can go back if something goes wrong.

I have a Thinkpad T61p, but I use the vesa instead of the nvidia driver, because the Thinkpad works standalone and in a KVM environment, and I could not get the nvidia driver to work.

---

### Post by sowelie on 2008-07-15
What you need to do is configure the resolution usplash uses.  The message change the resolution to 1024x768 60Hz is coming from your monitor.  The easiest way to set the usplash resolution is to install the package startupmanager.

```
sudo aptitude install startupmanager
```

Then open startup manager (System -> Administration -> Startup-Manager).  Then change the resolution to 1024x768. See if that helps.

---

