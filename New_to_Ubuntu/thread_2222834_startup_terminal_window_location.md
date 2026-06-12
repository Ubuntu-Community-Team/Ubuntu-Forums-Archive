---
title: "startup terminal window location"
date: 2014-05-08
forum: New to Ubuntu
---

### Post by Waynetrick on 2014-05-08
hi, I'm using ubutu 14.04. I have a script that runs as part of the startup but unfortunatley when it comes up it's behind the task bar on the left hand side of the screen. Is there a way i can set the window to open more in the center of the screen or at least not behind the task bar as i dont want to hide the task bar. all help is much appreciated

---

### Post by slickymaster on 2014-05-08
Hi Waynetrick, welcome to the forum.

There is Devilspie, a non-gui utility that lets you make applications start in specified workplaces, in specified sizes and placements, minimized or maximized and much more based on simple config files.
```
sudo apt-get install devilspie
```

---

### Post by nivek2 on 2014-05-11
Also, depending on what desktop-manager your using (like compiz) most have options that will save the position and size of where and how large (or small) your last window was for that particular app without using conf files.   edit: (GUI)

---

### Post by mcduck on 2014-05-11
Compiz has the option to set window position and desktop, but if you are using Gnome-terminal , it already has this built in as well. (you only mentioned it's a script, not what it does, just a script alone wouldn't show anything on screen..)

Just give it size and position you want in the command you use to start it with the "geometry" option:
```
gnome-terminal --geometry 132x43+100+100
```
(the first two numbers are width & height in characters, and the last two are horizontal & vertical offset from top left corner of the desktop, in pixels.)

---

