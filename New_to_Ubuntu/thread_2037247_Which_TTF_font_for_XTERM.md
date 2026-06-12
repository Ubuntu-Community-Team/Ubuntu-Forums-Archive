---
title: "Which TTF font for XTERM?"
date: 2012-08-04
forum: New to Ubuntu
---

### Post by honeybear on 2012-08-04
Hi, 

to change the font of xterm, how to list the name to enter to xterm from fonts ttf into .fonts?

thank you

---

### Post by itcotbtoemik on 2012-08-04
> **honeybear said:**
> Hi, 

to change the font of xterm, how to list the name to enter to xterm from fonts ttf into .fonts?

thank you

man xterm
[http://invisible-island.net/xterm/manpage/xterm.html](http://invisible-island.net/xterm/manpage/xterm.html)

for instance the "*-fa*" option and the corresponding "*faceName*" resource

---

### Post by honeybear on 2012-08-04
> **itcotbtoemik said:**
> man xterm
[http://invisible-island.net/xterm/manpage/xterm.html](http://invisible-island.net/xterm/manpage/xterm.html)

for instance the "*-fa*" option and the corresponding "*faceName*" resource

Thank you.I knew -fa, but how would you determine the name of the font in practice and its settings to paste to xterm?

---

### Post by itcotbtoemik on 2012-08-04
> **honeybear said:**
> Thank you.I knew -fa, but how would you determine the name of the font in practice and its settings to paste to xterm?

fc-list helps; xfd's "-fa" option as well:
[http://ftp.x.org/pub/X11R7.0/doc/html/fc-list.1.html](http://ftp.x.org/pub/X11R7.0/doc/html/fc-list.1.html)
[http://ftp.x.org/pub/X11R7.0/doc/html/xfd.1.html](http://ftp.x.org/pub/X11R7.0/doc/html/xfd.1.html)

---

### Post by honeybear on 2012-08-05
> **itcotbtoemik said:**
> fc-list helps; xfd's "-fa" option as well:
[http://ftp.x.org/pub/X11R7.0/doc/html/fc-list.1.html](http://ftp.x.org/pub/X11R7.0/doc/html/fc-list.1.html)
[http://ftp.x.org/pub/X11R7.0/doc/html/xfd.1.html](http://ftp.x.org/pub/X11R7.0/doc/html/xfd.1.html)

I have found xfontsel to get their names.

But why TTF fonts of ~/.fonts are not listed?



fc-list lists a lot of lines, that are difficult to read or understand. Isnt there a frontend, bit like xfontsel to select the given font size, ...

---

### Post by itcotbtoemik on 2012-08-05
> **honeybear said:**
> I have found xfontsel to get their names.

But why TTF fonts of ~/.fonts are not listed?



**fc-list** lists a lot of lines, that are difficult to read or understand. Isnt there a frontend, bit like xfontsel to select the given font size, ...

**xfontsel** only looks at XLFD fonts (those reported by xlsfonts).  There's no technical reason why it couldn't have been modified as was xfd and xterm to look at a listing from fontconfig, but rather *not-invented-here syndrome*, combined with xfontsel being deemed less critical.

From fc-list, the main thing you need for xterm is the *"faceName"*, which a quick check shows is the first string after the filename (ending with ": " here).  If you guess wrong, fontconfig's user-friendly aspect makes it use a system-default without giving any warning messages (or error codes) :P

---

### Post by honeybear on 2012-08-05
> **itcotbtoemik said:**
> **xfontsel** only looks at XLFD fonts (those reported by xlsfonts).  There's no technical reason why it couldn't have been modified as was xfd and xterm to look at a listing from fontconfig, but rather *not-invented-here syndrome*, combined with xfontsel being deemed less critical.

From fc-list, the main thing you need for xterm is the *"faceName"*, which a quick check shows is the first string after the filename (ending with ": " here).  If you guess wrong, fontconfig's user-friendly aspect makes it use a system-default without giving any warning messages (or error codes) :P

thank you for so much information. 

A question. Isnt it a GTK frontend for seeing the possible fonts?

---

