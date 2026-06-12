---
title: "[SOLVED] is it possible to make awn only have launchers?"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-06-30
ok, last question of the day


is there a way to make awn have only launchers, and make all windows minimize to gnome panel only?

also can i remove the little arrows undr the launchers?

if not then are there any other good docks for ubuntu that i can do this with?

---

### Post by bhadotia on 2008-06-30
I am also waiting for the answer:D.

---

### Post by Sam Lars on 2008-07-05
I have AWN installed from this:
```
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
```
The package is called awn-manager-bzr.
It's a newer testing version that has many more config options.  I believe you can remove the applet that provides the task manager and just add your launchers.

---

### Post by tjwoosta on 2008-07-05
>  	
Re: is it possible to make awn only have launchers?
I have AWN installed from this:
Code:

deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main

The package is called awn-manager-bzr.
It's a newer testing version that has many more config options. I believe you can remove the applet that provides the task manager and just add your launchers. 

hey thanks, but thats actually the same awn that i already have but when i remove the tasks applet it makes my launchers dissapear, the only things that stay are other applets like stacks

---

### Post by Sam Lars on 2008-07-06
You could try the Cairo dock.

---

### Post by tjwoosta on 2008-07-06
yea i was using cairo dock before and it works, but i dont really like the way it looks

even with the 3d look it still looks like crap compared to AWN (i even tried to make a custom background for it but it just doesnt look right)


anyway i think i have solved the launchers only problem with awn for the most part (i just made launchers for all of the apps that i use all the time, so now when i open one of them it just makes the little arrow underneath the launcher dissapear rather than poping up a new icon)

still i cant find  any way to get rid of the arrow from launchers (even with gconf-editor) and the only way to make icons not pop up everytime you open an app is to make a launcher for that app (not exactly what i wanted but whatever it works)

---

### Post by Sam Lars on 2008-07-06
To get the arrows to disappear you could move them off the screen or set their color to transparent.

---

### Post by tjwoosta on 2008-07-06
your a genius  :)

---

