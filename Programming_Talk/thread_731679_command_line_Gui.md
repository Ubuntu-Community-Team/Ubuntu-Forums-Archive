---
title: "command line Gui"
date: 2008-03-22
forum: Programming Talk
---

### Post by chaichy on 2008-03-22
hi there,
i want to programm some tools which make administrating my ubuntu server easier. 
i want to develop these with an command line gui like yast or the license agreement at installing java on a box. but i wasn't able to find a framework or what ever which makes me able to programm something like that and i don't know what exactly to google.. "command line gui" didn't bring results nor did other requests

perhaps has someone of you a link for me or something like that
thanks in advance chaichy

---

### Post by LaRoza on 2008-03-22
Ncurses is what you want.

See my wiki ([http://laroza.pbwiki.com/Specific](http://laroza.pbwiki.com/Specific))

---

### Post by chaichy on 2008-03-22
thank you
exactly what i needed

---

### Post by supirman on 2008-03-22
Using ncurses directly will be quite tedious.  I suggest using the Curses Development Kit (CDK) or dialog, which are libraries written on top of ncurses that provide common widgets (scrolling lists, selection items, calendar, data entry fields, etc).  Using CDK will greatly reduce the amount of time/code it will take to implement such an application.


CDK:
[http://invisible-island.net/cdk/](http://invisible-island.net/cdk/)

dialog:
[http://invisible-island.net/dialog/dialog.html](http://invisible-island.net/dialog/dialog.html)

---

