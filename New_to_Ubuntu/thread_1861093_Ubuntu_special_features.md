---
title: "Ubuntu special features"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by dep0 on 2011-10-15
Hi, i am running ubuntu 11.10 and i want to enable the special features i had in older versions. ( windows shaking, multiple screens rotating as a cube, etc).
Anyone knows how?

---

### Post by card_ace on 2011-10-15
go into the Ubuntu Software Center and search for "compiz"
install "Compiz" "Compiz Fusion Icon" and "CompizConfig Settings Manager"
after this you should be able to go to the dash home and type "ccsm" and go into the compiz settings and enable any effects that you want.

note: i know that there were issues in 11.04 between Unity and the desktop cube, and i'm not sure if they've been addressed, most of the others should work fine as far as i know

---

### Post by Lisiano on 2011-10-15
This is a bit more complicated, but I will try to write how to do it in Oneiric. Note: This is how I did it and there might be a better way, read it to the end before actually doing anything.

**Step 0:** Open a terminal (Ctrl+Alt+T) and install the prerequisite applications
```
sudo apt-get install compiz compiz-gnome compizconfig-settings-manager
```
**Step 1:** Type this command so we have a even ground to work on
```
unity --reset
```
**Step 2:** Type this so Compiz launches correctly```
gedit ~/.config/compiz-1/compizconfig/config
```
Now replace the content of this file with this ```
[general]
profile = unity
integration = true
backend = file

[general_ubuntu]
profile = 
integration = true
backend = file

```
**Step 3:** Type these commands so we can edit the Compiz settings out of CCSM instead of editing files
```
rm ~/.config/compiz-1/compizconfig/Default.ini
ln -s ~/.config/compiz-1/compizconfig/unity.ini ~/.config/compiz-1/compizconfig/Default.ini
```
**Step 4:** Open up CCSM make sure Ubuntu Unity Plugin is ticked
```
ccsm
```
Or Dash -> Customization -> CompizConfig Settings Manager

**Step 5:** Configure as you want it.
Note: The desktop might disappear and you can't type anything, if this happens, tick every plugin you wish to use and switch to a TTY (Ctrl+Alt+F1-F6) and login (You password will not be shown even as asterisks) then type ```
killall -9 compiz
DISPLAY=:0.0 compiz --replace
``` then you can switch back to your Desktop (Ctrl+Alt+F7). Now you can adjust the settings of the plugins.

**Step 6: **Make compiz start when you log in
Go to Dash -> Customization -> Startup Applications
Add new entry
Name: Compiz (Or anything you will understand later)
Command: compiz --replace
Description: *Blank* (Or anything you will understand later)

(Optional) **Step 7:** Relogin.

---

### Post by dep0 on 2011-10-15
Ok. Thank you both. I think i'll take lisiano's advice first and see how it goes.

---

### Post by card_ace on 2011-10-15
good plan, it seems as though there's a very large experience gap here . . . :)

---

### Post by dep0 on 2011-10-16
Well i only have ubuntu for a month if this is what you mean.

---

### Post by card_ace on 2011-10-16
no not you.  I meant between me and Lisiano.  I've been using Ubuntu for a while but I'm still lousy with terminal commands.  I still tend to use the GUI if I can help it.

---

### Post by Lisiano on 2011-10-16
Hey. I still consider myself a noob because I still don't know a lot of stuff about Linux. I use Ubuntu since 9.10 Karmic Koala btw.
Also yea, that's why I started using apt:// links to programs instead of their terminal equivalents. For example, which would the user be more scared of ```
sudo apt-get install skype
``` or pressing [Skype](apt://skype)?
(Note the terminal is used in my post above since it's both faster that way and the user would get used to it sooner, which is good due to the chance of encountering a TTY later on.)

---

