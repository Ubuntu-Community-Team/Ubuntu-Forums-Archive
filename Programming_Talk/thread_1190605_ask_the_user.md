---
title: "ask the user"
date: 2009-06-18
forum: Programming Talk
---

### Post by cazz on 2009-06-18
Hi

I have a script that run partimage so it restore a backup

but I like to ask the user if that person is sure that person want to restore the backup.

maybe even have a number that random so that person have to write to make sure that person dont press Y by mistake

---

### Post by moma on 2009-06-18
If your script can have a GUI, then use [Zenity...]("http://live.gnome.org/Zenity") or [Dialog...]("http://www.linuxjournal.com/article/2460"). 
Zenity's manual: [http://library.gnome.org/users/zenity/stable/](http://library.gnome.org/users/zenity/stable/)
Zenity requires GNOME/GTK but I think the Dialog is much simpler, it only needs Xorg/Xlib GUI system.

If you cannot have a GUI then use the bash's **read** command.
[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_08_02.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_08_02.html)

---

### Post by cazz on 2009-06-18
Thanks :)

---

### Post by nvteighen on 2009-06-18
> **moma said:**
> 
...
Zenity requires GNOME/GTK but I think the Dialog is much simpler, it only needs Xorg/Xlib GUI system.


Dialog doesn't use Xlib, so you can use it even in console :)

---

