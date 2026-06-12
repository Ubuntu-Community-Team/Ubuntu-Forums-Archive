---
title: "Auto Screen Resolution"
date: 2013-10-11
forum: New to Ubuntu
---

### Post by pesh1985 on 2013-10-11
Hey all,

The problem I am having is that my resolution defualt is currently 1024x768 (4:3), which is rather large on my screen. I want my resolution to be 1920x1080 (16:9), I have followed the following steps ([http://superuser.com/questions/311378/how-to-get-a-higher-resolution-on-ubuntu-11-04-using-an-intel-chipset](http://superuser.com/questions/311378/how-to-get-a-higher-resolution-on-ubuntu-11-04-using-an-intel-chipset)) but this still doesn't work at all!

My resolution changes to 1920x1080 (16:9) when I pass this command in the terminal:

xrandr --newmode clever_name 173.00  1920 2048 2248 2576  1080 1083 1088 1120
xrandr --addmode VGA1 clever_name
xrandr --output VGA1 --mode clever_name

I want this to be saved so everytime I login, this command is run...

Is there anyway to do this automatically?

Thanks in advance

Grant

---

### Post by andreazzz on 2013-10-14
Well, it is possible to make a script so everytime you boot it will be executed..
Therefore paste the commands in a empty document (gedit, Leafpad etc.) and save it as script.run. Go to settings and mark as executable. Next, go to 
Booting programs (or something like that) in the Start-menu and add the script.
Don't you have a Screen/Resolution/Arandr entry in your menu?

---

