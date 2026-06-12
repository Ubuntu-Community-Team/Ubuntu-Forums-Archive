---
title: "unable to load nvidia settings after a restart"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by SandyM on 2008-09-28
This is my third month of using Ubuntu.But due to some changes I was seeking in my drive structure through Windows I lost my linux drive and thus I had to reinstall it. But this time I am facing a new problem. I am using Nvidia 8800GT with latest 173.14.12 driver which I had been using since it was launched and was working perfectly before I lost my Ubuntu drive.
The problem is that every time I restart ubuntu or X-server I loose nvidia settings and the very moment I open Nvidia settings through terminal my settings get applied. 
I have tried every remedy in my knowledge. I always open settings through terminal command **_gksu nvidia-settings_**. I always save settings before exiting. I even created a start up entry through sessions in preference window with command "nvidia-settings -l". All these things used to work before but now they aren't working at all.
PLEASE HELP

---

### Post by Nepherte on 2008-09-28
In the menu there's an option to view your xorg file with the changes included. Copy/paste that in your xorg file and save it with a text editor.

---

### Post by SandyM on 2008-09-28
I can do that but the problem is that I regularly change contrast,gamma and brightness. And ,now for doing that I have to always repeat this procedure but in my prior installations of ubuntu ,merely saving the x-config through trminally opened(through sudo) was enough to bring permanent changes,
***_I just want to know the core of my problem. Why nvidia-settings are not getting saved as they used to be in my prior ubuntu installations?_***

---

### Post by diggerOS on 2008-12-04
..problem still exists.. :(

---

### Post by diggerOS on 2008-12-18
i finaly googled it...you should add:

nvidia-settings --load-config-only

..to your startup programs in sessions.
cheers!

---

