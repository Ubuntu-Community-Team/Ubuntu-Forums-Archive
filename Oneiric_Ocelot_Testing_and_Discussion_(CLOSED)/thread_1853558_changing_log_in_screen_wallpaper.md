---
title: "changing log in screen wallpaper"
date: 2011-10-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by flipper T on 2011-10-02
courtesy of omg ubuntu, i have changed the wallpaper on the log in screen by editing etc/lightdm/unity-greeter config. see original file below:

#
# background = Background file to use, either an image path or a color (e.g. #772953)
# logo = Logo file to use
# theme-name = GTK+ theme to use
# font-name = Font to use
# xft-antialias = Whether to antialias Xft fonts (true or false)
# xft-dpi = Resolution for Xft in dots per inch (e.g. 96)
# xft-hintstyle = What degree of hinting to use (hintnone, hintslight, hintmedium, or hintfull)
# xft-rgba = Type of subpixel antialiasing (none, rgb, bgr, vrgb or vbgr)
#
[greeter]
background=/usr/share/backgrounds/warty-final-ubuntu.png
logo=/usr/share/unity-greeter/logo.png
theme-name=Ambiance
icon-theme-name=ubuntu-mono-dark
font-name=Ubuntu 11
xft-antialias=true
xft-dpi=96
xft-hintstyle=hintslight
xft-rgba=rgb


simply change background to the image i wanted & works fine.

however, you know those feint polka dots that are on the original log in screen ? well they are still there. ie my new wallpaper plus damn polka dots !

i thought it might be hintsyle, so changed this to hintnone.

no luck.

any suggestions?

ps the question has been asked on omg's site with no response

---

### Post by cariboo on 2011-10-02
There is an earlier thread on the dots on the login screen, if I remember correctly, they are hard coded. I personally think it's so you can differentiate between the login screen and the desktop, if you use the same wallpaper, as I do.

---

