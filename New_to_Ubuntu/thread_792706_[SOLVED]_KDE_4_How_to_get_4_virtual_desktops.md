---
title: "[SOLVED] KDE 4: How to get 4 virtual desktops"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by thisismalhotra on 2008-05-13
Long time Gnome user trying KDE4 here,,

This might seem silly and weired, but to see desktop cube in compiz I need to enable 4 virtual desktops on my KDE4. I have tried all the settings I could find and so even if I set the number of desktops to 4, It will show only 2 desktops...dont know why :(
[B]
Help please ....[/B]

Also, what is the equivalent of system monitor (as in gnome) in KDE4

Thanks all...

---

### Post by smoker on 2008-05-13
you may have tried this, if so apology, right click on the workspace switcher, and look for a preference menu.

system monitor, don't know, i'm afraid

---

### Post by NightwishFan on 2008-05-13
You can change it under desktop in system settings. As for system monitor there is a program called system monitor. :popcorn:

KDE4 is not even using any of its main features in its current version though. (Still nice)

---

### Post by stevebakerj on 2008-05-13
Right Click on the Virtual Desktop pager, select 'Pager Settings' and select 2 rows

Do you mean 'System Activity'? if so just Ctrl + Esc

or perhaps run ksysguard at the command prompt Alt + F2

---

### Post by thisismalhotra on 2008-05-13
Okay, I think now I figured it out ...

If it uses Kwin everything works fine.. but as soon as I enable ... compiz .. it will only take 2 desktops ... 

I can make no. of rows as 2 but when I right click on pager and click configure desktops and make them 4 and apply it will still show 2.. can anybody help

---

### Post by thisismalhotra on 2008-05-14
/bump

help people !!

---

### Post by Golem XIV on 2008-05-14
If you're using Compiz (and you have to, to get the cube) you can't change the number of workspaces from the panel applet (or from any KDE applet for that matter).

First, make sure you have ccsm installed:
```
sudo apt-get update
sudo apt-get install compizconfig-settings-manager
```
Now go to System -> Preferences and start Advanced Desktop Effects Settings

Find the Desktop Settings button (it should be on the top)

Go to the Desktop Size tab

Set the Horizontal Virtual Size to 4, all others to 1

That should do it.

---

### Post by thisismalhotra on 2008-05-14
> **Golem XIV said:**
> If you're using Compiz (and you have to, to get the cube) you can't change the number of workspaces from the panel applet (or from any KDE applet for that matter).

First, make sure you have ccsm installed:
```
sudo apt-get update
sudo apt-get install compizconfig-settings-manager
```
Now go to System -> Preferences and start Advanced Desktop Effects Settings

Find the Desktop Settings button (it should be on the top)

Go to the Desktop Size tab

Set the Horizontal Virtual Size to 4, all others to 1

That should do it.

AWESOME Thanks that worked just a little edit...

install ccsm (which I had installed already)

Kmenu -> Application -> Settings -> Advanced Desktop Effects Settings -> General Options -> Desktop Size ..

Set the Horizontal Virtual Size to 4, all others to 1

Walla :popcorn:

---

### Post by craq on 2010-03-16
Hi,

I have the same problem, but the solution given doesn't work for Karmic. At least, I can't find the menu:
Kmenu -> Application -> Settings -> Advanced Desktop Effects Settings -> General Options -> Desktop Size ..

And what I assume is the equivalent:
System Settings -> Desktop -> Multiple Desktops
doesn't make any new desktops appear. Nor, incidentally, can I reduce it to just one desktop.

Two-sided cubes are just not as cool...

---

### Post by craq on 2010-03-16
Ok, problem solved. I didn't realise the menu was inside ccsm (not on the K-menu). see here
[http://ubuntuforums.org/showthread.php?t=509775](http://ubuntuforums.org/showthread.php?t=509775)

---

