---
title: "Where do apps usually keep their settings ?"
date: 2012-02-12
forum: New to Ubuntu
---

### Post by chickenPie4breakfast on 2012-02-12
I am new to linux and finding where stuff is - well it's taking time!
Whats the equivalent of windows  Application Data folder?
It seems that a lot of my apps are in /usr/share   but not their settings files

---

### Post by nothingspecial on 2012-02-12
Your settings are in your home folder. They are in hidden files and folders starting with a . (full stop/period).

You can view them by pressing Ctrl-H

For example your firefox settings are in a folder /home/$USER/.mozilla

System wide settings for applications are usually kept in /etc

---

### Post by chickenPie4breakfast on 2012-02-12
Thanks for the helpful reply, and I dig your crazy sig animation!

---

### Post by savanna on 2012-02-12
System settings in /etc.

Personal settings in "dot" files/dirs in your home directory eg /home/foo/.vimrc, /home/foo/.ssh

---

### Post by The Cog on 2012-02-12
A lot of config stuff seems to be put in /home/username/.config/appname these days, such as /home/steve/.config/evince . I suspect this is a new standard, and I think it makes more sense than littering hidden files all over your home directory.

---

