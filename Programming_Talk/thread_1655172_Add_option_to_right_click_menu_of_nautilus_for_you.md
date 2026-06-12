---
title: "Add option to right click menu of nautilus for your own program!?"
date: 2010-12-29
forum: Programming Talk
---

### Post by hakermania on 2010-12-29
Hello :D

I've made a program, and I want it to have an option to open with... at the right click menu of nautilus for specific files (e.g. *txt or *(for all files))
Example of Subtitle Editor program(which has this options only when right-clicking on *srt or *sub files):
[CENTER][IMG]http://i55.tinypic.com/vgljj9.png[/IMG]
[LEFT]I've heard about nautilus-actions package, but I don't think I need it, because Subtitle Editor has done this without installing this package.
So the question is How Do I do it? :)

Thx in advance for any answers!
[/LEFT]
[/CENTER]

---

### Post by odyniec on 2010-12-29
AFAIK you need to associate your application with that file's MIME type, by creating a .desktop file and putting it in /usr/share/applications.

This document should be of some help: [http://library.gnome.org/devel/integration-guide/stable/desktop-files.html.en](http://library.gnome.org/devel/integration-guide/stable/desktop-files.html.en)

---

### Post by hakermania on 2010-12-29
Thank you, this helped, but I cannot get it work :/ This is the file wallch.xml:
```

<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
   <mime-type type="application/x-wallch">
     <comment>Wallpaper Changer</comment>
     <magic priority="50">
       <match value="search-string" type="string" offset="10:140"/>
     </magic>
     <glob pattern="*.png"/>
   </mime-type>
</mime-info>
```
I placed it at /usr/share/mime/packages/ and run update-mime-database /usr/share/mime but I see nowhere the option to png files: "Open With.. Wallpaper Changer"
What's wrong?

---

### Post by odyniec on 2010-12-30
The XML file that you posted adds a MIME type, which is probably not what you want. I guess you just need the .desktop file for Wallpaper Changer -- this is described in the document at the URL that I gave you.

---

### Post by hakermania on 2011-01-21
I still can't find anything.... I've tried many ways.... *BUMP*

---

### Post by hakermania on 2011-01-29
BUMP or &#924;&#960;&#940;&#956;&#960;!

---

