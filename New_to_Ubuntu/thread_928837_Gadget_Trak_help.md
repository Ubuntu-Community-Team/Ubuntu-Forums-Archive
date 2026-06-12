---
title: "Gadget Trak help"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by esedizzle on 2008-09-24
Gadget Trak is this cool think that lets me track my stuff if it is stolen but, it only works for mac and windows with computers can anyone help me to get it on ubuntu. Check out the site [http://www.gadgettrak.com/](http://www.gadgettrak.com/)

---

### Post by MikeEvans on 2008-09-24
When you need to run windows programs on linux you need to look into wine, which is a windows compatibility layer.  Wine is not perfect and sometimes cannot run the program.  If that happens you can submit a bug or try a newer release to see if your program is supported.  The easy way to get going with wine is:
[LIST=1]
[*]Open Add/Remove programs from the Applications menu
[*]Search for and install wine
[*]Once the add/remove dialog is closed try installing your program as you would in windows (double click setup) or right click the setup file and select "run with wine"
[/LIST]

If your lucky it will install and put an icon on your desktop or on the Applications menu.  FYI: wine itself is installed to a hidden file in your home folder called .wine.  Within that folder is a windows like folder structure where your windows programs are installed.

If it doesn't work you can look into getting a newer version of wine or submitting a bug here [http://www.winehq.org/]("http://www.winehq.org/")

If you just cant get it to work you can look around to see if there is a linux program that does what you want.  If you must have that program running look into virtualizing windows or mac using virtual box.  Virtual Box has never failed me when I needed an stubborn program to run.

---

### Post by esedizzle on 2008-11-23
whats a virtual box

---

### Post by MikeEvans on 2008-11-24
Take a look:
[URL="http://www.virtualbox.org/"]
http://www.virtualbox.org/[/URL]

---

