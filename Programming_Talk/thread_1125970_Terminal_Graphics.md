---
title: "Terminal Graphics"
date: 2009-04-14
forum: Programming Talk
---

### Post by schmidtbag on 2009-04-14
Hey I'm really into shell scripting - I think its fun and I like to make advanced wizards to make non-graphical programs easier.

I was just wondering if theres a way to draw an image in terminal.  I don't care if its only 256 colors, as long as I can have some sort of picture.  I feel this is possible because for example, when you boot Knoppix, it shows 2 Tuxs sitting at the top, and they clearly aren't just text.  I'm aware terminal allows colored text but is there any way I can go about using a picture?

Much thanks in advanced.

---

### Post by benj1 on 2009-04-15
i think youll have some problems trying to do what you want.

everything like feh etc open up pictures in new windows.

i found [this]("http://www.earth.li/projectpurple/progs/ncpicview.html") which could be of some use.

if you want graphics i suppose you could use ncurses and the alternate char set.(perhaps create your own font to create the picture)

you could always look at the knoppix source.

---

### Post by schmidtbag on 2009-04-15
this seems like what I want but I can't compile it, it seems like compile script has an error in it or something.  I figured I may be missine one of its packages so I searched for libppm, and try compiling that and it claimed I was missing this .conf file and I don't know what to do about that

---

### Post by NathanB on 2009-04-15
You will want to interface with graphics at the lowest level.  In the *nix world, this is Xlib.  Using Xlib, you can put your pictures just about anywhere you want -- even on a terminal screen.

[http://www.sbin.org/doc/Xlib/](http://www.sbin.org/doc/Xlib/)

---

### Post by benj1 on 2009-04-15
well im getting different errors to you (perhaps relies used an older version of libnetpbm?). its something i used a while ago. it wasn't that good, i was thinking of it more for inspiration. 
i had to install the libnetpbm10 library i would try looking around for documentation for that and looking at the source of ncpicview.
sorry i can't be more helpful but nearly everything ive come across opens a window for drawing graphics, im fairly certain any solution would probably involve ncurses although i havent seen anything specific to displaying pictures.

or just go with NathanB's idea

---

### Post by schmidtbag on 2009-04-15
its ok, thanks anyway benj1.

i was looking into what nathan said and it looks like its for C or C++, and i'm looking into just shell scripting

---

