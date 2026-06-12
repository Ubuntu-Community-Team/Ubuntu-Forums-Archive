---
title: "Creating icon to launch simple java app"
date: 2008-05-08
forum: Programming Talk
---

### Post by jonathanmotes on 2008-05-08
I have written a simple Java program and I need to create a icon to run the class file. Does anyone know how to do this?

I've been trying to write a bash script and creating a launcher to run it, but I've not had any luck so far. I guess a .desktop icon would be better but I would be happy for any method.

Thanks!

---

### Post by amohanty on 2008-05-09
The way to do it is via a .desktop file. Look in /usr/share/applications. You can use any file in there as a template, ignore all the Comment[...] or Name[...] parts (they are there for localization). At the very least this will do:

[Desktop Entry]
Version=1.0
Name=XXXX
GenericName=YYYYY
Comment=ZZZZZZZZZ
TryExec=app_name
Exec=full_path_to_app_name
Terminal=false
Icon=full_path_to_icon_name
Type=Application

More details about this file are at:
[http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/)

HTH
AM

---

