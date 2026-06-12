---
title: "Where to get the icons used in Ubuntu ??"
date: 2010-02-06
forum: Programming Talk
---

### Post by arunb on 2010-02-06
Hi,

I am developing a linux based program, I would like to use the icons used in linux or in Ubuntu, where do i get similar icons ??

Windows Xp and Windows Vista theme icons are commonly available, are there similar such themes / styles for Ubuntu or Linux ??

thanks in advance
br

---

### Post by howefield on 2010-02-06
> **arunb said:**
> I would like to use the icons used in linux or in Ubuntu, where do i get similar icons ??

Any icons in particular ?

The most seem to be stored in /usr/shared

You'll find some in /icons and some in /pixmaps

---

### Post by kahumba on 2010-02-06
The icons in Ubuntu are stored in the locations specified by the XDG "standard".
You can't directly grab an icon from your app by writing a few lines of code, instead you either ask the system for it (by telling its name and desired size) or implement the XDG specification by hand in your application.
Themes usually use icons from their parents as well (for example to avoid duplicate work). For example, the current theme "Humanity" inherits icons from 2 other themes called "gnome" and "hicolor".
For more info try this
[http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html](http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html)
and this
[http://standards.freedesktop.org/icon-naming-spec/icon-naming-spec-latest.html](http://standards.freedesktop.org/icon-naming-spec/icon-naming-spec-latest.html)

The whole bunch of desktop standards by which Gnome/Ubuntu lives is here:
[http://www.freedesktop.org/wiki/Specifications](http://www.freedesktop.org/wiki/Specifications)

---

### Post by nvteighen on 2010-02-06
If you're writing a GTK+ application, you should also be aware of the GTK_STOCK_* icons, which are accessible through the GTK+ API.

---

### Post by lidex on 2010-02-06
> **arunb said:**
> Hi,
I am developing a linux based program, I would like to use the icons used in linux or in Ubuntu, where do i get similar icons ??


[http://www.gnome-look.org/index.php?xcontentmode=120x121&PHPSESSID=427e2f0e8338e14fc67cfd6c33a4a836]("http://www.gnome-look.org/index.php?xcontentmode=120x121&PHPSESSID=427e2f0e8338e14fc67cfd6c33a4a836")

---

