---
title: "Smoketesting wanted for a small project"
date: 2006-03-15
forum: Programming Talk
---

### Post by engla on 2006-03-15
Hello! The last weeks I've been coding at a small project I do for learning, but also because I'm trying to make up new tools that I need :)

Anyway, I've made a tool called **Dragbox**, which is simply this:
> Dragbox is a tool for connecting the commandline with the desktop environment. It summons a drag handle from nowhere when you are managing files or information in a shell, further empowering you in your workflow.

[Here is a screenshot]("http://www.student.lu.se/~cif04usv/images/dragbox-use.png")

It's a tool for the commandline, but you can use it, if you want, without touching the commandline! It enables you to do things like this:
```
$ cd /etc/init.d/
# I really want to copy/look at/do something with a file here
$ dragbox gdm

```
and then you get a window with the file /etc/init.d/gdm with it's icon, and you can drag it anywhere, to nautilus to copy it, to a text editor to look at it..

And you can do lots of other stuff.


**Edit: I've now released the stable version.**

It's a real debian package now, no checkinstall muck, so it should work very well with your system!
Source package: [dragbox_0.2.tar.gz]("http://www.student.lu.se/~cif04usv/publicfiles/dragbox_0.2.tar.gz")
Binary package for all architectures: [dragbox_0.2_all.deb]("http://www.student.lu.se/~cif04usv/publicfiles/dragbox_0.2_all.deb")
[COLOR="Gray"]

Anyway, I need some **smoketesting** before I let loose the first version at gnomefiles.org

I have basically four concerns
1. That it's possible to run this at all on other breezy and other ubuntu systems
2. That my source package works
3. That my universal .deb package works
4. That there are no outstanding bugs that make it just not work (smoketesting!)

Do you want to help?
Source package: [dragbox-0.2rc5.tar.gz]("http://www.student.lu.se/~cif04usv/publicfiles/dragbox-0.2rc5.tar.gz")
Binary package for all architectures: [dragbox_0.2rc5-1_all.deb]("http://www.student.lu.se/~cif04usv/publicfiles/dragbox_0.2rc5-1_all.deb")

Dependencies?
If you have the packages python2.4-gtk2, python2.4-gnome2, python2.4-glade2, python2.4-dbus (optional) it should work fine.

Thanks in advance

edit: Link to a newer version, just some small chages to dbus handling, but more features for drop-to for scripts.[/COLOR]

---

### Post by simplyw00x on 2006-03-15
This app looks amazingly useful. I'm downloading the binary package now, and I'll post again after some testing.

---

### Post by engla on 2006-03-15
[QUOTE=simplyw00x]This app looks amazingly useful. I'm downloading the binary package now, and I'll post again after some testing.[/QUOTE]
Thanks for the kind words!:KS  I think it's useful and I sought for a tool like this, but decided it didn't exist..

I love feedback, good or bad, just tell me whatever you think about it.

---

### Post by simplyw00x on 2006-03-15
Ok it installs fine from the deb, and runs fine with 'dragbox', but trying 'dragbox configure' (I wanted to drag a configure script somewhere) says 'Introspect error: The name app.dragbox.server was not provided by any .service files'. Any thoughts?

---

### Post by engla on 2006-03-15
[QUOTE=simplyw00x]Ok it installs fine from the deb, and runs fine with 'dragbox', but trying 'dragbox configure' (I wanted to drag a configure script somewhere) says 'Introspect error: The name app.dragbox.server was not provided by any .service files'. Any thoughts?[/QUOTE]
Hm... that's absolutely a dbus error. That's one of the first things I made, and since it worked for me, I just went on with the rest.. I have to research this.

I assume you have dbus installed and running, otherwise it should try, fail, and go on without dbus..

Thank you so much for testing this though.

If you can, tell me what version of dbus you have.  "dbus-launch --version" can tell you.

---

### Post by engla on 2006-03-15
I have now updated it to rc5, but I'm pretty sure that does **not** fix the error you got.. give it a try though, I might get lucky..

It's hard to find good docs on dbus, but it's a cool new thing and the basics are very easy (I followed the tutorial). But it seems that their api-may-change-at-any-time-disclaimer might be real, and a real problem.

Added some cool stuff in the new version, because I suddenly got the idea and couldn't resist.

So you can do... 'dragbox -n -0 | xargs -0 tar cfvz archive.tgz' and a window pops up, drag files to it. When you close the window, all the files are tarred.

---

### Post by simplyw00x on 2006-03-16
```
D-BUS Message Bus Launcher 0.60
Copyright (C) 2003 Red Hat, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

---

### Post by engla on 2006-03-16
[QUOTE=simplyw00x]```
D-BUS Message Bus Launcher 0.60
Copyright (C) 2003 Red Hat, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```[/QUOTE]

Thanks! I'll go on searching for this, but it's hard to find out. I've had one user with dbus 0.61 have it to work fine....
On breezy, it's still 0.36.2, and my main concern is to work with that.

---

### Post by 23meg on 2007-02-25
I'm getting the following error when I choose "Preferences" in Edgy:

```
(dragbox:11260): libglade-WARNING **: could not find glade file 'glade/preferences.glade'
Error: Failed to load UI file for preferences window!
Error: File: glade/preferences.glade
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/Dragbox/window.py", line 468, in cb_menu_preferences
    preferences_controller.shared.show_window()
  File "/usr/lib/python2.4/site-packages/Dragbox/preferences_controller.py", line 88, in show_window
    self.win.show_all()
AttributeError: 'preferences_controller' object has no attribute 'win'

```

I think you've addressed this in 0.2.3 (I infer that from the latest version info GnomeFiles page) but since your site is down, I can't get the binary package. I'd appreciate it if you posted an alternative link or the package itself here for the time being.

Dragbox is very well thought out and incredibly useful, by the way. I'm really into the idea of improving the interaction between the command line and graphical interfaces, and dragbox is nothing short of revolutionary in that regard. I have a some possible improvements and new features in mind that I'll get across to you in detail as a list soon.

---

### Post by engla on 2007-04-11
23meg, is that issue relieved in the latest version? My site should have been available for a while now, and is up now.

---

### Post by simplyw00x on 2007-04-11
Trying to test on Feisty but it depends on python 2.4 - Feisty's on 2.5.

---

### Post by engla on 2007-04-15
Right. I haven't had the chance to test it with python2.5 yet. I hope to do it sometime after the feisty release. Unfortunately my main machine, a ppc ibook, is going unsupported now for feisty.

---

