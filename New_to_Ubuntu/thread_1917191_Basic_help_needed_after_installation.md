---
title: "Basic help needed after installation"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by Minimal Internet on 2012-01-29
Hello :)

To begin with, I am not that new to Ubuntu at all, it is just that I haven't used it for a year or two.

Considering the fact that only a few things are like they were back then, I must ask:[INDENT] - How do I turn off my touchpad when mouse is connected ?

- How do I change startup applications ( I found it under System Settings, but the window ?
[/INDENT]Some other questions might be added to this thread later on, but I guess that's all for now.

Thanks in advance!

*** I am using Ubuntu 11.10.*

---

### Post by BC59 on 2012-01-29
For the touchpad depends from the computer. Usually is fn-F8 or something like this.
In 11.10 to open the startup applications, push the upper-right wheel and it's the third option. If you like to add a new application, keep the window open and then drag and drop inside the icon of the application, from the dash (upper-left wheel)

---

### Post by rgreener25 on 2012-01-29
Ok For the mouse open terminal from the applications bit. Then type ```
sudo add-apt-repository ppa:atareao/atareao
``` then enter, then type ```
sudo apt-get update
``` and enter, then ```
sudo apt-get install touchpad-indicator
``` and enter. Once that is done launch Touchpad-indicator from the Unity Dash and click on the touchpad icon in the system tray in the top right hand corner. Then click prefrences and tick disable touchpad when mouse plugged.

For the startup applications press alt-f2 and type ```
gksudo gnome-session-properties
``` if that doesn't work type ```
sudo apt-get install gnome-session-properties
``` in terminal then run ```
gksudo gnome-session-properties
```

---

### Post by Minimal Internet on 2012-01-29
> **BC59 said:**
> In 11.10 to open the startup applications, push the upper-right wheel and it's the third option. If you like to add a new application, keep the window open and then drag and drop inside the icon of the application, from the dash (upper-left wheel)

What ? :-k

> **rgreener25 said:**
> Ok For the mouse open terminal from the applications bit. Then type ```
sudo add-apt-repository ppa:atareao/atareao
``` then enter, then type ```
sudo apt-get update
``` and enter, then ```
sudo apt-get install touchpad-indicator
``` and enter. Once that is done launch Touchpad-indicator from the Unity Dash and click on the touchpad icon in the system tray in the top right hand corner. Then click prefrences and tick disable touchpad when mouse plugged.

For the startup applications press alt-f2 and type ```
gksudo gnome-session-properties
``` if that doesn't work type ```
sudo apt-get install gnome-session-properties
``` in terminal then run ```
gksudo gnome-session-properties
```

Touchpad indicator seems to be doing exactly what I was looking for, but startup applications window is still empty.

---

### Post by rgreener25 on 2012-01-29
> **Minimal Internet said:**
> Touchpad indicator seems to be doing exactly what I was looking for, but startup applications window is still empty. Then you have no startup applications :)

---

### Post by BC59 on 2012-01-29
You didn't explain for what you need the startup applications. You like to add or remove something?
The startup applications folder is in etc/xdg/autostart
If you like to remove an application run:
gksu nautilus and reach the folder through root nautilus to make changes.

---

### Post by Minimal Internet on 2012-01-29
> **BC59 said:**
> You didn't explain for what you need the startup applications. You like to add or remove something?
The startup applications folder is in etc/xdg/autostart
If you like to remove an application run:
gksu nautilus and reach the folder through root nautilus to make changes.

Sorry for not explaining what I need from the very beginning.
/etc/xdg/autostart contains what was supposed to be in Startup Applications ( for example, I want to turn off Bluetooth manager, Visual Assistance, etc. ), but how do I turn something off without completely deleting it ?

---

### Post by rgreener25 on 2012-01-29
> **BC59 said:**
> You didn't explain for what you need the startup applications. You like to add or remove something?
The startup applications folder is in etc/xdg/autostart
If you like to remove an application run:
gksu nautilus and reach the folder through root nautilus to make changes.

no offence. but why do it like that when you can run ```
gksudo gnome-session-properties
``` and just click add and type in the command

---

### Post by Minimal Internet on 2012-01-29
> **rgreener25 said:**
> no offence. but why do it like that when you can run ```
gksudo gnome-session-properties
``` and just click add and type in the command

If only I could ..
Startup Application Preferences contains only GNOME Login Sound. Where are the rest ?

---

### Post by BC59 on 2012-01-29
Please follow my instructions above.

@rgreener25 if you like to understand what I mean open the etc/xdg/autostart to see where are the startup applications.

---

### Post by Minimal Internet on 2012-01-29
> **BC59 said:**
> Please follow my instructions above.

I do not want to delete anything - I just want to turn something off and keep the option to turn it back on when necessary.

---

### Post by BC59 on 2012-01-29
In that case move the corresponding .desktop file from autostart folder to a new folder called autostartbackup. Then if you like to have it again to autostart, move it again to the original place. All this using gksu nautilus.

---

### Post by rgreener25 on 2012-01-29
> **BC59 said:**
> Please follow my instructions above.

@rgreener25 if you like to understand what I mean open the etc/xdg/autostart to see where are the startup applications.

i get it now, sorry :P

---

