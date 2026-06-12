---
title: "Theming engine 'adwaita' not found"
date: 2014-12-15
forum: New to Ubuntu
---

### Post by Roberto_Hernndez on 2014-12-15
hello ):P I'm a Linux noobster and I am tryig to learn how to use the "gedit" command for programming purposes, but I have this issue after I open a new document 

rob@Satellite:~$ gedit program.c

(gedit:11872): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:2:16: Theming engine 'adwaita' not found

(gedit:11872): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1443:2: Missing name of pseudo-class

I want to know, what does that means? and what am I doing wrong here? :confused:

thanks for everything :KS

---

### Post by vasa1 on 2014-12-15
Which theme are you using? Is it a theme compatible with the GNOME version on your computer?

**gtk-widgets.css:2:16** means that there is something off about the second line of code in gtk-widgets.css starting at the 16th character.

Many gtk errors can be ignored. Many can be fixed by editing the file in which the errors are reported. The main concern is whether your program runs as it should. For errors in the terminal read [http://askubuntu.com/a/422400](http://askubuntu.com/a/422400)

---

