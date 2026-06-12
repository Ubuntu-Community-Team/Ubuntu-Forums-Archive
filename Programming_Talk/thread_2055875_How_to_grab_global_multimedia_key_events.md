---
title: "How to grab global multimedia key events?"
date: 2012-09-10
forum: Programming Talk
---

### Post by bird1500 on 2012-09-10
Hi,
I'm using Gtk,
can anyone please point to a tutorial which I can use to make my gtk app capture global multimedia key events such as "play", "stop", "next"? Such keys are present on many keyboards.

If Gtk can't do that, I'd be OK with an X11 tutorial on capturing global key events.

Google only shows up tutorials with non-global events.

---

### Post by conradin on 2012-09-10
[http://freedesktop.org/wiki/Software/XEvIE](http://freedesktop.org/wiki/Software/XEvIE)
for that key logging bit. Its an X extension, in GTK I have no idea how to do it. 
This looks interesting too:
[http://securitytube-tools.net/index.php?title=X11_keylogger](http://securitytube-tools.net/index.php?title=X11_keylogger)


something I was working with a few months ago was a C library, allegro.h that gave you the option to working raw vs cooked mode. I bets oemthing similar exists in X11. like this: 
[http://www.xfree86.org/4.1.0/OpenBSD5.html](http://www.xfree86.org/4.1.0/OpenBSD5.html)

I hope this is a start.

---

### Post by conradin on 2012-09-10
these also might be of more help:

[http://tldp.org/HOWTO/Keyboard-and-Console-HOWTO-14.html#ss14.1](http://tldp.org/HOWTO/Keyboard-and-Console-HOWTO-14.html#ss14.1)

[http://rick.vanrein.org/linux/funkey/#impl](http://rick.vanrein.org/linux/funkey/#impl)

---

### Post by bird1500 on 2012-09-12
Thanks, they don't do it for me,
I looked at the Totem source code and it seems it uses a plugin which uses dbus to query stuff from gnome settings or so.

I'm doing an audio player (screenshot), pretty much complete, it has all the stuff I've been looking for which no other player does it: quick startup, good built-in file browser, native Ubuntu system tray support, no-bullsh#t  and no fancy widgets, just playing the stuff I got on my pc.
The closest to this ideal is the decibel-music-player but it sometimes crashes, is written in Python and doesn't support Ubuntu's native system tray.

Anyway, the last big must-have feature for my player is to react to global key presses on multimedia keys which I'll hopefully find a solution for.

---

### Post by bird1500 on 2012-09-15
Done!
keybinder 0.3 helped.
The examples that ship with it don't compile, so I used the source code directly in my app, which is good too since I don't have to depend on keybinder being installed.

 For media key shortcuts I used:
"XF86AudioNext"
"XF86AudioPlay"
"XF86AudioPrev"
"XF86AudioStop"

---

