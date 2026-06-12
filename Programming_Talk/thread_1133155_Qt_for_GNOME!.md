---
title: "Qt for GNOME?!"
date: 2009-04-22
forum: Programming Talk
---

### Post by MIH1406 on 2009-04-22
What if I used QtCreator (C++) to create my project in Ubuntu (GNOME) is there any problems? Does my progect works perfectly in GNOME as in the KDE?

Thanks,
Mohammad

---

### Post by sekinto on 2009-04-22
No problem there. As long as you have all the correct libraries installed you will be just fine.

Edit:
Although there is Glade which is similar to QtCreator but for GTK if you want to try that out.

---

### Post by OutOfReach on 2009-04-22
Yes it'll work with no problems.

---

### Post by samjh on 2009-04-22
> **MIH1406 said:**
> What if I used QtCreator (C++) to create my project in Ubuntu (GNOME) is there any problems? Does my progect works perfectly in GNOME as in the KDE?

Thanks,
Mohammad

I do exactly what you're asking (develop Qt applications on Gnome), and there are no problems.

---

### Post by hessiess on 2009-04-23
QT apps look ugly in gnome.

---

### Post by jacksaff on 2009-04-23
> **hessiess said:**
> QT apps look ugly in gnome.

I think you mean gnome looks ugly around a qt app :)

---

### Post by samjh on 2009-04-23
> **hessiess said:**
> QT apps look ugly in gnome.Yet another outdated opinion about Qt. ;)

Use [GtkStyle]("http://labs.trolltech.com/page/Projects/Styles/GtkStyle").  It works with all Qt 4.x versions.  It is integrated with Qt 4.5 onward (available in Jaunty Jackalope).

---

### Post by MIH1406 on 2009-04-23
Thanks you all

---

### Post by hessiess on 2009-04-23
> **samjh said:**
> Yet another outdated opinion about Qt. ;)

Use [GtkStyle]("http://labs.trolltech.com/page/Projects/Styles/GtkStyle").  It works with all Qt 4.x versions.  It is integrated with Qt 4.5 onward (available in Jaunty Jackalope).

Doesn't seem to work with Scribus ;).

---

### Post by nvteighen on 2009-04-23
I wonder why is there so much confusion about this topic... I mean, sometimes people think that GTK+ == GNOME and Qt == KDE... which is plainly wrong. GNOME is just a suit of applications which use GTK+ as their official toolkit... but nothing else... If you start an application which loads Qt (or whatever other library), it will be the system's responsability, not the DE's...

Of course, some details like font rendering and window managing will be managed by the DE, but not the application. That's the magic of GNU/Linux's modularity!

---

### Post by samjh on 2009-04-23
> **hessiess said:**
> Doesn't seem to work with Scribus ;).

Scribus is based on Qt 3. ;)

Scribus 1.3.5 development release is based on Qt 4 though.  So in time, it will blend in. :)

---

### Post by hessiess on 2009-04-24
> **samjh said:**
> Scribus is based on Qt 3. ;)

Scribus 1.3.5 development release is based on Qt 4 though.  So in time, it will blend in. :)

Fair enough:)

---

### Post by Vadi on 2009-04-24
GtkStyle is buggy and not perfect, so the apps still look ugly or even properly (ie color change buttons). I don't see can't you use Qt Creator to program a GTK+ app though.

---

### Post by samjh on 2009-04-24
I haven't had any problems with GtkStyle yet on the six Qt programs I've used regularly (VirtualBox, VLC, QtCreator, Qt Assistant, Linguist, and Qt Demo) and I've been using GtkStyle for a long time.

Perhaps because GtkStyle isn't yet integrated into most Qt installation and need to be hand-compiled, there might be some distro or installation-specific issues that aren't universal but affects particular users.

You can't really use Qt Creator to program GTK+ apps.  Qt Creator uses Qt's .pro files for project management.  It might be possible to use CMake with Qt Creator, but I don't know how that works.

---

### Post by Vadi on 2009-04-24
Sorry, but it *is* a universal issue, and you get this from the stock version that Ubuntu ships with along with a compile.

[http://www.ubuntu-pics.de/bild/12954/screenshot_47_N52r7P.png](http://www.ubuntu-pics.de/bild/12954/screenshot_47_N52r7P.png) <- buggy gtkstyle
[http://www.ubuntu-pics.de/bild/12955/screenshot_48_V564Vd.png](http://www.ubuntu-pics.de/bild/12955/screenshot_48_V564Vd.png) <- non-buggy cleanlooks

---

### Post by samjh on 2009-04-24
Someone should file a bug report: [http://code.google.com/p/qgtkstyle/issues/list](http://code.google.com/p/qgtkstyle/issues/list)

Which Ubuntu version ships GtkStyle by default?  Intrepid doesn't, so I'm assuming Jaunty.  I haven't got Jaunty installed on my system yet.

---

### Post by Vadi on 2009-04-24
Hard to tell because it has Qt 4.5 and the thing was integrated into it.

---

### Post by samjh on 2009-04-25
I can't reproduce the bug.  I've tried the colour change buttons in Qt Settings and in the Text Edit demo application.  They work just fine with Qt 4.3 and 4.5 and the latest GtkStyle svn checkout. :confused:

---

### Post by jensbw on 2009-04-25
Note that system themes/styles in Qt can not guarantee that a custom button color is respected because Qt is not actually drawing those buttons itself. The same problem applies on Mac and Windows XP where the theme is based on a set of predefined images. If your interface really requires a colored button you should use style sheets or explicitly set a non-native style such as cleanlooks on those buttons where Qt has complete control over its painting.

---

### Post by cb951303 on 2009-04-25
> **Vadi said:**
> Sorry, but it *is* a universal issue, and you get this from the stock version that Ubuntu ships with along with a compile.

[http://www.ubuntu-pics.de/bild/12954/screenshot_47_N52r7P.png](http://www.ubuntu-pics.de/bild/12954/screenshot_47_N52r7P.png) <- buggy gtkstyle
[http://www.ubuntu-pics.de/bild/12955/screenshot_48_V564Vd.png](http://www.ubuntu-pics.de/bild/12955/screenshot_48_V564Vd.png) <- non-buggy cleanlooks

I'm using qgtkstyle for a while now and I never had that bug, in fact I never had any bug with it.

---

### Post by pjalegria on 2009-04-25
There are no .deb for qgtkstyle???

---

### Post by Vadi on 2009-04-25
Er, well, get the Mudlet app and give it a try yourself!

Or if you're great at Qt, suggest a better way to draw them - naturally, Qt seems to be missing a "color button" that can be used for color selection.

---

### Post by samjh on 2009-04-25
> **Vadi said:**
> Or if you're great at Qt, suggest a better way to draw them - naturally, Qt seems to be missing a "color button" that can be used for color selection.

Except it's not Qt doing the drawing.  It's GTK+ (in the case of GtkStyle).

And Qt does have a button for selecting colours, but it's an add-on download.

I can confirm the bug with Mudlet, and have filed a bug report upstream.

---

### Post by samjh on 2009-05-26
UPDATE:

I received a reply from the QGtkStyle upstream developer.  The bug is invalid, and workarounds were suggested.  See: [http://code.google.com/p/qgtkstyle/issues/detail?id=84](http://code.google.com/p/qgtkstyle/issues/detail?id=84)

---

