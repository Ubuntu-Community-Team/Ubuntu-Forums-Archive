---
title: "Start a program based on file's mimetype"
date: 2008-05-07
forum: Programming Talk
---

### Post by NormR2 on 2008-05-07
What command/program can I execute in a script to call the application associated with a mimetype/file extension?  Like when you are in a File browser and you "open" a file.
The syntax in a script file would be: <start-app> <a-file>
The coding would be: <start-app> $1

For example, if <a-file> were: Something.html
then <start-app> would start a browser and have it open Something.html

Another example, if <a-file> were: Picture.jpg
then <start-app> would start an image program and have it open Picture.jpg

Thanks,
Norm

---

### Post by WW on 2008-05-07
If you are using gnome, you can try [gnome-open](http://ubuntu.wordpress.com/2006/12/16/gnome-open-open-anything-from-the-command-line/).

---

### Post by stroyan on 2008-05-07
You can use the 'see' command to open a file based on mimetype and mailcap.

---

### Post by Awalton on 2008-05-07
xdg-open will work on any system with the FreeDesktop Portland Utilities installed (it's a portable version of gnome-open; will work for GNOME, KDE, XFCE, etc).

[http://portland.freedesktop.org/xdg-utils-1.0/xdg-open.html](http://portland.freedesktop.org/xdg-utils-1.0/xdg-open.html)

---

### Post by NormR2 on 2008-05-08
gnome-open and xdg-open both worked as expected. For example;
  gnome-open testing.html  opened my browser formating the html
  gnome-open testing.jgp   opened eog showing the image
  xdg-open testing.html    worked same as gnome-open above

Couldn't get see to do that.
  see testing.html   opened a viewer/editor (w3m?) of the html file

---

### Post by WitchCraft on 2008-05-08
> **WW said:**
> If you are using gnome, you can try [gnome-open](http://ubuntu.wordpress.com/2006/12/16/gnome-open-open-anything-from-the-command-line/).

just use 'open', not 'gnome-open', it does work on gnome & kde & unix.

---

### Post by stroyan on 2008-05-08
> **NormR2 said:**
> 
Couldn't get see to do that.
  see testing.html   opened a viewer/editor (w3m?) of the html file

w3m is actually a text based web browser.  I don't know why the mailcap
entry pointed to that.  I would only expect that to be used if the
DISPLAY environment variable was not set.

---

