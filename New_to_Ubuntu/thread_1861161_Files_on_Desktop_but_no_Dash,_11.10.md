---
title: "Files on Desktop but no Dash, 11.10"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by will547_us on 2011-10-15
I suspect some sort of conflict with Compiz as I was in CCSM looking for a way to change user session applet. I didn't change any settings but screen froze. On restart I have my desktop with files and no dash, applets, etc????

---

### Post by Lisiano on 2011-10-15
Please either log in using Unity 2D and open a terminal (Ctrl+Alt+T) or go to a TTY (Ctrl+Alt+F1-F6) and use this command
```
unity --reset
```
If using a TTY```
DISPLAY=:0.0 unity --reset
```
If you wish to use Compiz, remember to check the Ubuntu Unity Plugin.

---

### Post by ikt on 2011-10-15
Did you install a video driver?

---

### Post by will547_us on 2011-10-15
When I try unity --reset I get this:

Warning: no DISPLAY variable set, setting it to :0
unity-panel-service: no process found

I upgraded from 11.04 through Update Manager and added no new video card or drivers.

Also while looking in CCSM I did not change anything the CCSM window froze.

-Will-

---

### Post by Lisiano on 2011-10-15
Since you tried to do it in a TTY, please prepend DISPLAY=:0.0 or else it will not work
```
DISPLAY=:0.0 unity --reset
```You can switch back to your desktop with Ctrl+Alt+F7

---

### Post by will547_us on 2011-10-15
Lisiano,

 I feel as if I'm floundering. From my desktop CTRL+ALT+F2 gets me tty2.

I entered "DISPLAY=:0.0 unity --reset" 
and I get unity-panel-service: no process found.

CTRL+ALT+F7 takes me back to files on desktop with no unity panel.

-Will-

---

### Post by Lisiano on 2011-10-15
Okay, this is weird. Can you type this in a TTY ```
DISPLAY=:0.0 gnome-terminal
``` Then switch back over to your desktop. Can you type anything in the Terminal? Could you try running the unity --reset in it. Also as a workaround, you could simulate Unity 2D by launching
```
unity-2d-panel
unity-2d-launcher
```

---

### Post by will547_us on 2011-10-15
Terminal Opened, typed unity --reset and I get
unity-panel-service: np process found 
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no 
Backend   :gconf
Integration   :true
Profile   :default 
Adding plugins
Skipping upgrade com.canonical.unity.unity.01 upgrade
Skipping upgrade com.canonical.unity.unity.02 upgrade
 Initializing core, bailer, detection, composite, opengl,decor, mousepoll, vpswitch, animation, snap, expo, move, place, grid, gnomecompat, wall, ezoom, workarounds ALL ...done. 
compiz(expo) - Warn: failed to bind image to texture

Then a series of [ERROR]: Option "next key" already defined
After 36 lines of similar [ERROR]

Initializing resize, fade, scale, session options...done

Cursor

When I attempt to close terminal I get CLOSE THIS TERMINAL? process still running.

CTRL+ALT+F2 takes me back to tty2

-Will-

---

### Post by will547_us on 2011-10-15
In tty I entered unity-2d-panel and I get
"(unity-2d-panel:2081): Gtk-Warning **: cannot open display"
Same result after entering unity-2d-launcher

---

### Post by Fear091 on 2011-10-15
Had the same problem.
Is it possible to log into a guest account and have unity working there? If so, log into your main account with Ubuntu 2-D, open CCSM and [B]make sure the Unity plugin is checked.
If it is not, check it and make any choices necessary to make sure Unity is working again.
[/B]I'm not sure if this will work for you, but your problem sounds very similar to mine, and this solution worked for me.

[EDIT]: Wait, 2-D isn't working for you either?

---

### Post by Lisiano on 2011-10-15
I meant to open those in the Terminal that appeared, this way you don't have to type DISPLAY=:0.0 every time. Or you can type this once (You have to type it again if you relogin to the TTY)```
export DISPLAY=:0.0
```
Also don't close the terminal or else you will kill compiz that started in the terminal.
Also, did you try logging into Unity 2D instead of Unity 3D?
When you boot your computer, there should be a user list, press the little cog on the upper right corner of the box with your username and pick Ubuntu 2D.

EDIT: @Fear091, he tried to start Unity-2D inside a TTY without telling it where it should go (A TTY has no Display) that is why he couldn't start it.

---

### Post by will547_us on 2011-10-15
Thank you Lisiano and Fear091 !!! I didn't realize the "cog" on the login screen took me to different places. I clicked Unity 2d and all is good with the world!

Y'all have a safe weekend, Will

How do I mark this thread solved?

---

### Post by Fear091 on 2011-10-15
'Thread tools' up above the first post on the page.
Last option I recall.

---

