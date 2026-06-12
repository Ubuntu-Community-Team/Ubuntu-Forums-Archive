---
title: "getting error .. (software-properties-gtk:22375): Gtk-WARNING **: Theme parsing error"
date: 2013-10-15
forum: New to Ubuntu
---

### Post by nagarjuna-lingala on 2013-10-15
Hi All, 

I am getting below errors while launching any application like gedit , software-properties-gtk..etc

(software-properties-gtk:22375): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:885:28: 'px' is not a valid color name ----> for software-properties-gtk

(gedit:17964): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:885:28: 'px' is not a valid color name ----> for gedit

help me to resolve this problem

---

### Post by heir4c on 2013-10-15
That are graphics applications, so you do not run that from the terminal. Except when you run it with root privileges.(if you want to change a file that needs root privileges). Than you use: gksudo gedit ... Than you get no errors.
Why you want that run from terminal?
(Software-properites-gtk=Software&Updates (via Dash))

---

