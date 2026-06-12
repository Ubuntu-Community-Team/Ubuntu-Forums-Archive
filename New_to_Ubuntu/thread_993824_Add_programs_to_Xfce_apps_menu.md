---
title: "Add programs to Xfce apps menu"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by racer x on 2008-11-26
I installed Nautilus and it did not get added to the applications menu. I was wondering how i would go about adding it. I created an entry in /usr/share/applications and when i click on it it opens Nautilus but it still did not get added to the applications menu. This is what the code looks like in mousepad:

[Desktop Entry]
Version=1.0
Type=Application
Encoding=UTF-8
Name=Nautilus
Exec=nautilus
Icon=nautilus
Type=Application
Categories=System;Accessories;

I'm not sure if your even meant to make an entry in /usr/share/applications to add to the applications menu but it was just a tutorial i found on a Xfce help website. This is my first day using linux so dumbed down explanations would be appreciated. 

Also rather than make a couple of new threads for these things, does anyone know how to make chat sessions in pidgin flash when a message is received like in windows? It's just I'm normally listening to music and don't hear the new message sounds. Also, whats a good text editor similar to notepad2 in windows? mousepad seems rather basic.

thanks for your help

---

### Post by kerry_s on 2008-11-26
did you ever think your using the wrong os, you should be using the standard ubuntu instead of trying to turn xfce4 into something it's not.

right click the menu button> edit menu
mousepad = try gedit, since your already using nautilus you might as well have the gnome editor.

for the launcher it should be> nautilus --nodesktop
if you don't want it taking over the desktop.

---

### Post by racer x on 2008-11-26
Thanks for the help, working good now. I tried the standard ubuntu and i had some troubles getting flash to work properly (tried gnash, swfdec and adobe), then i tried kubuntu and although i like kde's look, it ran a bit clunky. Really enjoying Xubuntu's simplicity and speed.

edit: got pidgin notification working, seems the plugin isn't on by default.

---

### Post by gn2 on 2008-11-26
> **racer x said:**
> I installed Nautilus 

Why? Thunar is a better option for Xubuntu.

---

### Post by kerry_s on 2008-11-26
> **racer x said:**
> Thanks for the help, working good now. I tried the standard ubuntu and i had some troubles getting flash to work properly (tried gnash, swfdec and adobe), then i tried kubuntu and although i like kde's look, it ran a bit clunky. Really enjoying Xubuntu's simplicity and speed.

edit: got pidgin notification working, seems the plugin isn't on by default.

weird, flash is the same no matter what ubuntu version your using.

---

### Post by kerry_s on 2008-11-26
> **gn2 said:**
> Why? Thunar is a better option for Xubuntu.

it is what it is, everyone has a different preference. just because it's the default file manager doesn't mean people will use it.

---

### Post by gn2 on 2008-11-27
> **kerry_s said:**
> it is what it is, everyone has a different preference. just because it's the default file manager doesn't mean people will use it.

Indeed, but why would anyone choose Nautilus over Thunar for Xubuntu?
What possible advantage is there as a reason for that particular choice?

---

### Post by kerry_s on 2008-11-27
> **gn2 said:**
> Indeed, but why would anyone choose Nautilus over Thunar for Xubuntu?
What possible advantage is there as a reason for that particular choice?

i haven't used thunar in a while, but on occasion's it use to just act up or get slow maybe even crash. it's like the logout option, sometimes it works and sometimes not. :lolflag:

---

