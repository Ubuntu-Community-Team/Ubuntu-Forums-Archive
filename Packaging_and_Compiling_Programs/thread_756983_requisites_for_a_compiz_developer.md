---
title: "requisites for a compiz developer"
date: 2008-04-16
forum: Packaging and Compiling Programs
---

### Post by dexter.deepak on 2008-04-16
i have been fascinated for long by the 3d looks and animation courtesy compiz.
now i feel that i should also develop my own effects ..but i dont know where to start. i have a hold over c ,c++ and java . are these things of any help ??
how much time will it take to get my hands over such designing ??
what are qt and gtk ...are these things of any importance??

i hope you people will encourage my enthusiasm to be a better developer...and guide me to some good directions.

thanks in anticipation.

---

### Post by andrewsomething on 2008-04-17
You might want to check out: [http://forum.compiz-fusion.org/](http://forum.compiz-fusion.org/)

---

### Post by PypeBros on 2008-04-17
Qt and GTK are what we call "widget toolkits". That is, libraries that know how to deal with buttons, textboxes, popup menues, etc.
When i say "deal with", i mean draw them, react to user input (redraw the button when you click it), but also internally route generated events (and when you come to a tree-structure browsing, you surely don't want to handle all those events in your application. ;) )

Afaik, compiz stands at another level. It is a window manager and therefore won't worry about *what* is inside windows (thus those widgets Qt and GTK care about). It merely get snapshots of areas in the windows (through X' "expose" events, most likely) and use them as textures while rendering the whole screen.

Btw, i'm in no way someone comfortable with compiz programming, so if anyone with a more "authoritative" information want to complete/correct me, go ahead ;)

---

