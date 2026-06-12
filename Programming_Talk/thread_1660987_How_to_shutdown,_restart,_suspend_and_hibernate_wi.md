---
title: "How to shutdown, restart, suspend and hibernate without being root ?"
date: 2011-01-06
forum: Programming Talk
---

### Post by leon.vitanos on 2011-01-06
Hi! How to shutdown,restart,suspend and hibernate your pc  from a terminal or a shell prompt without being root... (so without a sudo before the command ) .... :-k

---

### Post by nvteighen on 2011-01-06
Impossible with a default system setup. Shutting down is done through setting a particular runlevel and that's done by root.

Now you may ask why you can shut down on GNOME or KDE not being root. Well, because what GNOME or KDE do is call the underlying gdm or kdm, which are run by root. You know, the whole desktop is like a big su-like (not sudo) login in which a process owned by root lets you enter into your non-privileged user account.

---

### Post by leon.vitanos on 2011-01-06
ok so how is it possible from a program like GShutdown to shutdown the pc on the time you say? There must be a command that let's you do that.. :/

---

### Post by MadCow108 on 2011-01-06
you could use dbus:
dbus-send --print-reply --dest=org.gnome.SessionManager /org/gnome/SessionManager org.gnome.SessionManager.RequestShutdown

you could probably also use setuid
[http://en.wikipedia.org/wiki/Setuid](http://en.wikipedia.org/wiki/Setuid)

---

### Post by leon.vitanos on 2011-01-06
> **MadCow108 said:**
> you could use dbus:
dbus-send --print-reply --dest=org.gnome.SessionManager /org/gnome/SessionManager org.gnome.SessionManager.RequestShutdown

you could probably also use setuid
[http://en.wikipedia.org/wiki/Setuid](http://en.wikipedia.org/wiki/Setuid)

Nice the shutdown command you said works! But this is only for shutdown.. For hibernate(halt), suspend(sleep), and lock screen?:-k

---

### Post by kerry_s on 2011-01-06
gnome-session-save --help
&
gtk-session-logout --help

only works in gnome though.

---

### Post by MadCow108 on 2011-01-06
> **Bong.Da.City said:**
> Nice the shutdown command you said works! But this is only for shutdown.. For hibernate(halt), suspend(sleep), and lock screen?:-k

lock screen would be
dbus-send --type=method_call --dest=org.gnome.ScreenSaver /org/gnome/ScreenSaver org.gnome.ScreenSaver.Lock

PowerManager should have Suspend and Hibernate, but for some reason they are not present on my system :/

---

### Post by leon.vitanos on 2011-01-06
> **MadCow108 said:**
> lock screen would be
dbus-send --type=method_call --dest=org.gnome.ScreenSaver /org/gnome/ScreenSaver org.gnome.ScreenSaver.Lock

PowerManager should have Suspend and Hibernate, but for some reason they are not present on my system :/

Thanks again.. Lock also works! 

But these:
dbus-send --session --dest=org.gnome.PowerManager --type=method_call --print-reply --reply-timeout=2000 /org/gnome/PowerManager org.gnome.PowerManager.Hibernate
dbus-send --session --dest=org.gnome.PowerManager --type=method_call --print-reply --reply-timeout=2000 /org/gnome/PowerManager org.gnome.PowerManager.Suspend

Gives an error
Error org.freedesktop.DBus.Error.UnknownMethod: Method "Suspend" with signature "" on interface "org.gnome.PowerManager" doesn't exist

Weird i have to say .. So any ideas ? I am searching at google but i can't find it :/ #-o

---

### Post by leon.vitanos on 2011-01-07
Anyone? :/

---

### Post by MadCow108 on 2011-01-07
if all fails use a helper program with setuid or capabilities [http://linux.die.net/man/7/capabilities](http://linux.die.net/man/7/capabilities)

---

### Post by leon.vitanos on 2011-01-07
i will send an email to the programmer of gshutdown to tell me what is the commands :) thanks anyway MadCow :D

---

### Post by MadCow108 on 2011-01-07
gshutdown communicates with gdm as already mentioned by nvteighen in the first reply ...

---

### Post by nova47 on 2011-01-07
You could always just ask the administrator to give you the ability to use the shutdown command.

---

### Post by bilkay on 2011-01-15
I can get my laptop to hibernate but only with the command "sudo hibernate". When I do so, the screen shows the progress of the image being saved, then it shuts down. On restart, the previous condition is resumed as expected. Great so far!

However, that's the only way hibernate works. Selecting "Hibernate" from the Shutdown applet brings up a blank gray screen which remains for a minute or so, then the computer shuts down. Restart then goes through normal boot *except* that when I log in to the account I "hibernated" from, networking is disabled! The previous condition is not restored.

Also, there is no "Hibernate" option from the login screen. This means that "resume" always returns without password protection.

Specifics:

10.04 on HP G62 migrated from WUBI with swap file.

---

