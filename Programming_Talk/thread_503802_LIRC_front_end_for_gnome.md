---
title: "LIRC front end for gnome"
date: 2007-07-18
forum: Programming Talk
---

### Post by DeusEx on 2007-07-18
Since there's nothing like it, I am considering writing a front end or perhaps porting IRKick to a gnome compatible version.
I've been looking for decent IR Remote Control support for gnome for hours now, but it seems such tools only exist for the KDE environment.

My goal:
-have a LIRC manager that couples events to IR signals.

Functionality:
-The program finds the available LIRC events (eg. remote control buttons) in lircd.conf
-The program creates a LIRC config that sends all LIRC events to the program
-The user can easily add a dcop event or a script to a LIRC event or a combination of LIRC events.
-Some system events should be available: shutdown, reboot, master volume up/down, tone volume, surround volume, mute, open/close cd tray, autoplay cd, screensaver.
-Instead of an action, the program can enter a mode
-In each mode every LIRC event can trigger a different action
-An OSD clearifies the mode the program is in, this should show up every time a LIRC event is received.

Any thoughts on this would be appreciated!

---

### Post by menace82 on 2007-11-04
That would be great!

---

### Post by tacone on 2007-12-11
Did you begin workin on it ?

---

### Post by loeppel on 2008-05-08
Nice, something would be great!
But instead of dcop we should use DBus, because its the "new dcop".

I would be help to write somthing like this? Anyone started?

greets,
loeppel

---

### Post by mattydee on 2008-06-14
I may switch to Gnome from KDE when this happens :)

---

### Post by wasutton3 on 2008-06-16
this project seems to have died, and i think this would be a fantastic idea. i love kde, but it doesnt play nice with some of the applications i have so i use gnome. i would like to see this happen or at least find a way to run gnome applications from kde's irkick (which works fine)

---

