---
title: "HOWTO: Replace Metacity with IceWM"
date: 2006-04-15
forum: Outdated Tutorials &amp; Tips
---

### Post by SomeoneWhoIsntMe on 2006-04-15
I was bored, so I tried out window managers. I liked IceWM, but it doesn't work with the "--replace" command. However, you can still use IceWM with GNOME. I apologize in advance for using so many ```
's but I know that if I used quotation marks there would be one winner that would copy and paste them into whatever and break something, then yell at me. Also, the poor formatting in this guide would probably lead you to belive that I'm too lazy to make a nice guide. [SIZE="1"][COLOR="LemonChiffon"]You'd be right.[/COLOR][/SIZE]

**Installing**
**1.** In a terminal, type [code]sudo apt-get install icewm icewm-gnome-support
```
**2.** Go into your terminal, and type ```
cp /usr/share/gnome/default.session ~/.gnome2/session
```
**3.**Type ```
sudo gedit .gnome2/session
```Remove the line ```
0,id=default0
``` and change ```
0,RestartCommand=gnome-wm --sm-client-id default0
``` to ```
0,RestartCommand=icewm
``` Note: If you were so inclined, you could replace "icewm" with the name of any other window manager, but you'd have to figure out how to configure it yourself.
**4.** In a terminal, type ```
sudo nautilus /etc/X11/icewm[code] In another terminal, type [code]sudo nautilus .icewm
``` Drag all the files from /etc/X11/icewm to ~/.icewm, and make a folder in ~/.icewm called ```
themes
``` If you dowload any themes for IceWM, you just untar them into folders in there.
**5.** Open the preferences file in ~/.icewm, and at the bottom, add the lines ```
ShowTaskBar=0
UseRootButtons=0
```
**6.** Log out, and log back in (no need to muck about with sessions), and you have IceWM instead of Metacity as your GNOME Window Manager. You can edit the files in ~/.icewm to customize it if you'd like, and there's plenty of themes at freshmeat.

---

### Post by tseliot on 2006-04-23
Guide added to the USDF!
[http://doc.gwos.org/index.php/Icewm_Gnome]("http://doc.gwos.org/index.php/Icewm_Gnome")

---

### Post by Rikostan on 2006-04-24
Thanks for the guide!
Besides the obvious "to see how it works" factor. What would be some of the positives for using another WM(specifically IceWM) instead of Metacity? I would think that Ice would be a slight be faster, but what else?

---

### Post by shof2k on 2006-04-30
For those who want a gui to edit the preferences file, install icepref.  I had to change themes from the icewm taskbar though.

---

### Post by szymon_g on 2007-03-13
hi
i've translated it into polish.
you can see that translated howto here :

[http://forum.ubuntu.pl/viewtopic.php?t=28683](http://forum.ubuntu.pl/viewtopic.php?t=28683)

btw, although icewm under gnome looks nice, i prefer icewm + thunar/rox 'standalone' :-)

szymon

---

### Post by zedfrugnug on 2007-04-26
I tried this guide, and it worked fine, til step 4.; no .icwm folder was found:confused: 
I made the folder myself and put the files from /etc/X11/icewm to ~/.icewm in.
This seems to work, (I'm using Icewm right now) but there is no preference file for step 5, and maybe I'm missing more files in the .icwm folder?

---

