---
title: "Compiling a Qt app fully static"
date: 2009-04-28
forum: Packaging and Compiling Programs
---

### Post by dennis123123 on 2009-04-28
Can anyone tell me how to compile an application that requires the Qt libraries into a static version where the libraries are compiled into the application?

As to why: I'm creating a slim installation of linux for my netbook, and all of the applications I use are GTK - but for linux I am yet to find a GTK substitute for MSPaint! There just isnt one that can compete with its simplicity yet useful feature set (ive tried them all; mtpaint, tuxpaint, xpaint...etc etc) I have found **Kolourpaint** which is an almost identical clone of MSPaint, but it is Qt based (grrr!) and rather than installing the like 100MB of Qt bloat for a single app, I was hoping to link the bits it needs statically and end up with a large binary that will run on a Qt-less system (I think Skype do this).

(I know MSPaint runs under Wine, and thats what i'm using at the moment because I need Wine for Office 2007 and WinHex anyway, so it adds next to zero overhead. the problem is its not a "proper" linux solution imho, and a native app would be much better)

---

### Post by dennis123123 on 2009-05-11
bump...

---

### Post by Lawand on 2009-09-13
If you're still interested:
[http://doc.trolltech.com/4.5/deployment-windows.html#building-qt-statically](http://doc.trolltech.com/4.5/deployment-windows.html#building-qt-statically)

I belive that you should performa a full Qt build to get a static version of Qt modules, then link you application to them.

---

### Post by yodasoda on 2010-03-18
you just gave a link to deploy with windows not X11

---

