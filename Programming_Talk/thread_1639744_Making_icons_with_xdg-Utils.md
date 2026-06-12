---
title: "Making icons with xdg-Utils"
date: 2010-12-07
forum: Programming Talk
---

### Post by r3bol on 2010-12-07
Hi, I had this crazy idea to use the desktop icon concept as little info centers that could update itself when clicked (by pointing to a script that modified it). I can't seem to figure out how to create the icon though. I've been going through xdg-Utils ( [http://portland.freedesktop.org/wiki](http://portland.freedesktop.org/wiki) ) and this is what I managed so far... 
```
#!/usr/bin/env xdg-open

# http://linux.die.net/man/1/xdg-desktop-icon

[Desktop Entry]
Version=1.0
Name=Hello World
Comment=This is an info icon
GenericName=info icon
Exec=icon.py 
Type=Application
Terminal=false
Icon=./home/Dev/python/info_icons/icon.png
Categories=Application
MimeType=image/png
Name[en_US]=test.desktop
```
I ran the command to create the icon on the desktop...
xdg-desktop-icon install [--novendor] test.desktop
There are no errors and I get something called test.desktop created on my desktop. The desired .png image isn't shown nor is name of the icon been added as expected. The icon also doesn't allow execution of icon.py either. 
I was wondering if anyone could spot where I am going wrong here. I'm using Linux Mint9 (Gnome version).

---

### Post by SledgeHammer_999 on 2010-12-07
How about removing the leading "."?

```
Icon=/home/Dev/python/info_icons/icon.png

```

---

### Post by r3bol on 2010-12-07
> **SledgeHammer_999 said:**
> How about removing the leading "."?

```
Icon=/home/Dev/python/info_icons/icon.png

```
Thanks for the suggestion, but it didn't work. I also tried Icon=icon.png and Icon=icon

---

### Post by r3bol on 2010-12-07
Owww dude, it was a permissions thing. Looks fine now ;)

---

### Post by r3bol on 2010-12-08
Looks like this idea didn't work out so well. It seems you can't really write over an image linked icon and have the icon image change in real time. That is, I can update the image with the same name, but it doesn't pass that change on to the icon until I restart the OS.

Edit: No wait, seems to be working fine now. XD

---

