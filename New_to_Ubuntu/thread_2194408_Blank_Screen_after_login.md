---
title: "Blank Screen after login"
date: 2013-12-18
forum: New to Ubuntu
---

### Post by elang on 2013-12-18
I have an Inspiron N5010 running Ubuntu13.10 64b. It uses Intal HD Graphics (i.e. no ATI/Nvidia graphics card)

I need a software that uses OpenGL, and I installed multiple packages using synaptic that had the word "opengl"

Now, system boots up fne, but I only get a blank screen when I login (I can see and move the mouse pointer). Closing the laptop lid, or pressing Ctrl+Alt+L gives me the usual lock screen w/o any problems.

After opening tty1, I ran **startx** which again switched to a black screen. Going back to tty1, I saw startx was stuck at [B]Loading Extension GLX.
[/B]Used Ctrl+C to close it

After googling, I tried
```
sudo apt-get reinstall ubuntu-desktop
sudo apt-get unity
```
but it did not help

Any ideas on what I should do now?

---

### Post by jones quest on 2013-12-18
OpenGL is included in the mesa packages, installed by default in basically all linux distributions. If you need specific packages to create openGL stuff, then that's a different thing, but you don't need to install additional packages to view openGL content if your hardware supports it. 
You shouldn't install random stuff in synaptic. You can view your package install history in: /var/log/apt/history.log
I suggest you remove the random packages you installed previously to get back to a working X.

---

### Post by fantab on 2013-12-18
Intel Graphics a quite well supported in Linux. Just installing Ubuntu is all you need to do if you have Intel Graphics.

Follow the advice in the above post, if that doesn' help then re-installing ubuntu can be a good option. BACKup you important DATA before you reinstall.

---

