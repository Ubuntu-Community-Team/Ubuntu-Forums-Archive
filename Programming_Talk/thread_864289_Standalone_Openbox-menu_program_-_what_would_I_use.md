---
title: "Standalone Openbox-menu program - what would I use to make that?"
date: 2008-07-19
forum: Programming Talk
---

### Post by Yes on 2008-07-19
I'd like to make a standalone version of the Openbox menu, but I'm not sure what I would use to make it?  Is there any library that you would use to draw like that, or what?

Thanks.

---

### Post by urukrama on 2008-07-19
I'm far from a programmer, but have a look at something like 9menu or deskmenu (or even dzen2) and see what it uses. Perhaps that will give you some ideas.

---

### Post by shifty2 on 2008-07-19
You could even do it in gtk if you wanted. Maybe have a look at the openbox source - that may give you some ideas.

---

### Post by Yes on 2008-07-19
Well I know of one standalone menu that does it with GTK, but I think I would rather do it how 9menu does, which is just directly with X.  Are there any tutorials out there for programming with X?

---

### Post by LaRoza on 2008-07-19
> **Yes said:**
> Are there any tutorials out there for programming with X?

[http://www.unix-manuals.com/tutorials/xlib/xlib.html](http://www.unix-manuals.com/tutorials/xlib/xlib.html)

Google for more ;)

---

### Post by Yes on 2008-07-19
Heh, that's the one I've been using.  Do I want Xlib tutorials, or is that something different?

---

### Post by gotmor on 2008-07-19
> **Yes said:**
> I'd like to make a standalone version of the Openbox menu, but I'm not sure what I would use to make it?  Is there any library that you would use to draw like that, or what?

Thanks.

You could have look into this: 
[http://dzen.geekmode.org/dwikidoku.php?id=dzen:dz9menu](http://dzen.geekmode.org/dwikidoku.php?id=dzen:dz9menu)

It interpretes 9menu input files but will aditionally let you use any dzen formating commads, e.g. coloring your menu entries, adding icons, drawing graphical separators, etc.

---

### Post by urukrama on 2008-07-19
> **gotmor said:**
> You could have look into this: 
[url]http://dzen.geekmode.org/dwikidoku.php?id=dzen:dz9menu
[/url]

Thank you for that link. Very interesting!


The link gives a 404, though. It should be this: [http://dzen.geekmode.org/dwiki/doku.php?id=dzen:dz9menu]("http://dzen.geekmode.org/dwiki/doku.php?id=dzen:dz9menu")

---

