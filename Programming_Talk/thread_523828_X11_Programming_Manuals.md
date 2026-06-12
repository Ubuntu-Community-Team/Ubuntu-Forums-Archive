---
title: "X11 Programming Manuals"
date: 2007-08-12
forum: Programming Talk
---

### Post by joann on 2007-08-12
Hello all,

I am creating a very simple gui program using X11, but for some reason the manual pages are not installed. I would like to "man XCreateSimpleWindow", "man XCreateGC", ect... I looked in /usr/X11R6/ folder (this is where they have been on my other linux installations), but no man pages were found. Does any one know what I need to apt-get inorder to install the manual pages?

-Joann

---

### Post by moma on 2007-08-12
Hello,

The XLib reference manual:

The XLib manuals live in the "libx11-dev" package.  Have you installed that?
$ [COLOR="SeaGreen"]sudo apt-get install libx11-dev[/COLOR]

Which files does it carry, contain, have within?
$ [COLOR="SeaGreen"]dpkg -L libx11-dev[/COLOR]

/usr/lib
/usr/lib/libX11.a
/usr/lib/pkgconfig
/usr/lib/pkgconfig/x11.pc
/usr/share/man/man3/XParseColor.3.gz
....
/usr/share/man/man3/XPoint.3.gz
/usr/share/man/man3/XBell.3.gz
-----------------

Look in the manual section 3 
$ [COLOR="SeaGreen"]man 3 XCreateSimpleWidow[/COLOR]

I normally just paste the function name into Firefox and Google for it. It's the easiest and fastest method in my casa.
-----------------

Manuals for the XLib's extended functions (such as XShape* non rectangular windows) are in the libxext-dev package.
$ [COLOR="SeaGreen"]man 3 XShapeCombineMask[/COLOR]
-----------------

Reading:
A good introduction to XLib graphics
[http://users.actcom.co.il/%7Echoo/lupg/tutorials/xlib-programming/xlib-programming.html](http://users.actcom.co.il/%7Echoo/lupg/tutorials/xlib-programming/xlib-programming.html)
+
Other examples here: [http://tronche.com/gui/x/](http://tronche.com/gui/x/)

And general guides: [http://www.futuredesktop.org/opportunities.html](http://www.futuredesktop.org/opportunities.html)
------------------

[COLOR="Red"]EDIT:[/COLOR] GNOME has also a graphical GUI tool to show manual (man) pages. I just cannot  remember the name of it. Does anyone else know?

---

### Post by joann on 2007-08-12
Awsome!

I can now man and apropos to my X11 hearts content. :) Also, thanks for the website links, quite good.

Have a great day.

-Joann

---

