---
title: "Icon edit"
date: 2011-11-25
forum: New to Ubuntu
---

### Post by doppel.ganger on 2011-11-25
I want to edit the look of a single icon. Where are the icons stored?

---

### Post by Rex Bouwense on 2011-11-25
I believe that they are stored in /user/share/icons

---

### Post by doppel.ganger on 2011-11-25
Nothing interesting there. Just system icons and one skype icon.

---

### Post by Rex Bouwense on 2011-11-25
What exactly are you looking for?

Try /user/share/icons/hicolor/apps

That is where mine are.

---

### Post by doppel.ganger on 2011-11-25
The icon for Nuvola Player (previously google music frame)

---

### Post by doppel.ganger on 2011-11-25
Sorry, forgot to mention this. I'm running Fedora 16 Gnome.

---

### Post by Frogs Hair on 2011-11-25
Application icons are often found in file system /usr/share/pixmaps . To find the icon location open the main menu , select the category where the application appears , right click on the line displaying the application , and  enter the applications properties .  Select the icon image on the left side of the dialog box and the location of the icon will open . Sorry I wrote this before your last comment , so try pixmaps .

---

### Post by bodhi.zazen on 2011-11-25
> **doppel.ganger said:**
> Sorry, forgot to mention this. I'm running Fedora 16 Gnome.

If you want to change the icon, either install alacarte or manually edit the .desktop file in in /usr/share/applications.

The general syntax is listed here:

[http://standards.freedesktop.org/desktop-entry-spec/latest/apa.html](http://standards.freedesktop.org/desktop-entry-spec/latest/apa.html)

If you want edit the actual icon file, you need to fine it first. Either use locate or look at the .desktop file in /usr/share/applications to identify the location of the icon you are using.

---

### Post by doppel.ganger on 2011-11-25
Thanks for pointing out /usr/share/applications, except that Nuvola Player isn't listed there! I'll try alacarte. What exactly is it?

---

### Post by doppel.ganger on 2011-11-25
Uh oh, alacarte won't launch. Is there anything I can do?

---

### Post by bodhi.zazen on 2011-11-25
> **doppel.ganger said:**
> Uh oh, alacarte won't launch. Is there anything I can do?

1. Find the .desktop file, use "locate"

2. Post the error message you are getting with alacarte.

---

### Post by doppel.ganger on 2011-11-25
```
[kathryn@Kathryn-Fedora ~]$ alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
  File "/usr/lib/python2.7/site-packages/Alacarte/MainWindow.py", line 19, in <module>
    import gtk, gmenu, gobject, gio
ImportError: No module named gmenu
[kathryn@Kathryn-Fedora ~]$ 

```
Anyway, would Alacarte be any help with Gnome 3 and Fedora?

---

### Post by bodhi.zazen on 2011-11-25
> **doppel.ganger said:**
> ```
[kathryn@Kathryn-Fedora ~]$ alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
  File "/usr/lib/python2.7/site-packages/Alacarte/MainWindow.py", line 19, in <module>
    import gtk, gmenu, gobject, gio
ImportError: No module named gmenu
[kathryn@Kathryn-Fedora ~]$ 

```
Anyway, would Alacarte be any help with Gnome 3 and Fedora?

There is a bug report with a work around here :

[https://bugzilla.redhat.com/show_bug.cgi?id=734442](https://bugzilla.redhat.com/show_bug.cgi?id=734442)

Other then what looks like a packaging issue, alacarte works fine in fedora 16 with gnome3

---

