---
title: "ULE and quicklist editor."
date: 2011-09-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by philinux on 2011-09-25
[http://www.webupd8.org/2011/05/quicklist-editor-for-ubuntu-unity.html](http://www.webupd8.org/2011/05/quicklist-editor-for-ubuntu-unity.html)

Been googling away but could not find if this is going to get packaged for the repos.

---

### Post by mc4man on 2011-09-25
There is still some dev going on, possible features to be added, this is a current against packaging (ppa
[https://bugs.launchpad.net/unity-launcher-editor/+bug/793444](https://bugs.launchpad.net/unity-launcher-editor/+bug/793444)

---

### Post by philinux on 2011-09-26
Thanks for that. 

I dragged my chroot launcher into the sidebar but it loses it custom icon. Where the heck does unity store this. Cant find it anywhere.

It's a standard desktop launcher that points to my chroot script. A simple thing. I want to edit the file that unity has created.

---

### Post by castrojo on 2011-09-26
Not 100% sure, but look in .local/share/applications

---

### Post by philinux on 2011-09-26
> **castrojo said:**
> Not 100% sure, but look in .local/share/applications

Yeah I already looked in there. Unity must know how to get at the script from a link/file somewhere.

---

### Post by mc4man on 2011-09-26
open your chroot launcher in gedit & post
unity launcher items (the favorite icons) are just  shortcuts to .desktops

---

### Post by philinux on 2011-09-26
> **mc4man said:**
> open your chroot launcher in gedit & post
unity launcher items (the favorite icons) are just  shortcuts to .desktops

Thats the problem I can see the Chroot.desktop on my Desktop but not the file that unity has created for it's launcher or not :confused:
The launcher on the dock has the default launcher icon. I'm just trying to get a handle on how Unity treats dragged to the dock stuff.


```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Icon[en_GB]=gnome-panel-launcher
Name[en_GB]=Chroot
Exec="/home/philcb/Ubuntu One/Scripts/chroot.sh"
Name=Chroot
Icon=/usr/share/pixmaps/gnome-term.png
```

---

### Post by mc4man on 2011-09-26
Unity doesn't 'create' anything - launchers (.desktops), added to the unity launcher are just added to a gsettings key as a string
```
gsettings get com.canonical.Unity.Launcher favorites
```

Your .desktop is what 'controls' this - 1st. try removing the dupe Icon= line (you also don't need 2 Name= lines
Any changes to a .desktop that is in the unity launcher require restarting unity to take effect, a log out/in will do

```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Exec="/home/philcb/Ubuntu One/Scripts/chroot.sh"
Name=Chroot
Icon=/usr/share/pixmaps/gnome-term.png
```

side note:
if you move the location of a .desktop after adding to unity launcher it will disappear, best place to store .desktops that   are to be added is ~/.local/share/applications or /usr/local/share/applications **before** adding to unity launcher

I'd probably add this chroot as a quicklist to a utilities unity icon rather than a standalone, no matter

---

### Post by philinux on 2011-09-26
> **mc4man said:**
> Unity doesn't 'create' anything - launchers (.desktops), added to the unity launcher are just added to a gsettings list
```
gsettings get com.canonical.Unity.Launcher favorites
```

Your .desktop is what 'controls' this - 1st. try removing the dupe Icon= line (you also don't need 2 Name= lines
Any changes to a .desktop that is in the unity launcher require restarting unity to take effect, a log out/in will do

```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Exec="/home/philcb/Ubuntu One/Scripts/chroot.sh"
Name=Chroot
Icon=/usr/share/pixmaps/gnome-term.png
```

side note:
if you move the location of a .desktop after adding to unity launcher it will disappear, best place to store .desktops that   are to be added is ~/.local/share/applications or /usr/local/share/applications **before** adding to unity launcher

I'd probably add this chroot as a quicklist to a utilies unity icon rather than a standalone, no matter

**gsettings get com.canonical.Unity.Launcher favorites**
Marvellous. I removed the dock launcher edited the desktop file and dropped it back on and now I get the correct icon. All clear now cheers. Is there a gui way to see favourites.

---

### Post by mc4man on 2011-09-26
> Is there a gui way to see favourites.
Yes - in dconf-editor, though it can sometimes be a real pita to use
When making changes to a string in dconf-editor you need to click in till the area turns 'white;, make your change & then press enter on the keyboard while the cursor is still in the edit area
In other words don't click out

Some dconf-editor keys will only come up as a small slit - as said can be a pita
In the case of the launcher - if you have several 'custom' items it's possible the dconf window will extend off the screen

I use a gsettings set command if ever needing to restore - any .desktop that _resides in an applications dir._ can be set by just using it's name, full path isn't needed, gsettings will add the path if not in /usr/share/applications
Non standard locations must be set with full path
(A bit messy any which way

---

### Post by philinux on 2011-09-26
> **mc4man said:**
> Yes - in dconf-editor, though it can sometimes be a real pita to use
When making changes to a string in dconf-editor you need to click in till the area turns 'white;, make your change & then press enter on the keyboard while the cursor is still in the edit area
In other words don't click out

Some dconf-editor keys will only come up as a small slit - as said can be a pita
In the case of the launcher - if you have several 'custom' items it's possible the dconf window will extend off the screen

I use a gsettings set command if ever needing to restore - any .desktop that _resides in an applications dir._ can be set by just using it's name, full path isn't needed, gsettings will add the path if not in /usr/share/applications
Non standard locations must be set with full path
(A bit messy any which way

Gotcha. Installed dconf-tools and all is clear now.

---

### Post by mc4man on 2011-09-26
If you get a 'small slit' key it can be expanded by some careful scroll and click action - the danger is if one happens to click on a setting that is changed from a click, must be careful and change back if that happens

---

### Post by philinux on 2011-09-26
> **mc4man said:**
> If you get a 'small slit' key it can be expanded by some careful scroll and click action - the danger is if one happens to click on a setting that is changed from a click, must be careful and change back if that happens

Cheers. Which .folder is all this stuff for unity located. Been poking around and I cant quite see it.

---

### Post by mc4man on 2011-09-26
I believe..? that per user gsettings' are stored in ~/.config/dconf/user which is basically 'unreadable'

unity also still uses gconf for compiz/unityshell plugin related settings

---

### Post by philinux on 2011-09-26
> **mc4man said:**
> I believe..? that per user gsettings' are stored in ~/.config/dconf/user which is basically 'unreadable'

unity also still uses gconf for compiz/unityshell plugin related settings

Ah that explains a lot then. ;)

---

