---
title: "[Python] A little app: Copybox"
date: 2008-06-23
forum: Programming Talk
---

### Post by Can+~ on 2008-06-23
It's not meant to be a full application (unless anyone wants to), it could be used as a plugin for other app.

I wanted to build an application that could keep a list of elements that have been copied recently, using the gtk.Clipboard. Any suggestion, tip, critic, insult, love declaration, threat,... is welcome.

Screenshot(s):
> 
[IMG]http://img.photobucket.com/albums/v517/CanXp/screenshot1-3.png[/IMG]

Usage:
-Copy anything (Ctrl+C), anywhere on your gnome environment (dunno if it works on windows or KDE...)
-Just clicking over a row copies the content of it.
-The application refreshes each 3 seconds (adjustable in the source code).

Source code (.py) and interface (.glade) attached

---

### Post by Wybiral on 2008-06-23
I haven't tried it yet, but it seems like after a while it would get very hard to go back and find anything on it. Perhaps making it searchable would be an interesting feature.

---

### Post by Can+~ on 2008-06-23
> **Wybiral said:**
> I haven't tried it yet, but it seems like after a while it would get very hard to go back and find anything on it. Perhaps making it searchable would be an interesting feature.

It actually stores 20 strings, after that, the last ones are removed. But I do agree with the search.

---

### Post by Tomosaur on 2008-06-24
> **Can+~ said:**
> It actually stores 20 strings, after that, the last ones are removed. But I do agree with the search.

Maybe make it optional? 20 strings seems like a sensible limit, but I can imagine some people might need more than that. 20 is a good default, but maybe including an option to set the limit yourself would be a good idea.

---

