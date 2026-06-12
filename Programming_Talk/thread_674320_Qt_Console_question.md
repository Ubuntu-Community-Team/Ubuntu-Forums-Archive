---
title: "Qt Console question"
date: 2008-01-21
forum: Programming Talk
---

### Post by igjurisk on 2008-01-21
I have installed on my Kubuntu 7.10 Qt 4.3 Open Source but its for GUI 
app development.(I think so)
But what i really want to now is there posibility to develop console 
apps with Qt, if there is, can you point me to right direction? 

I have read some articles about Qt Console but I just can't figure it out.

Do I use classes from Qt 4.3? :confused:

I programmed with C++ for about an year now and i think that's enough for starting with Qt.

Thanks for your time in advance.

IggI

---

### Post by aks44 on 2008-01-21
The Qt library is composed of several sub-modules.

Some of them can be used both in console and GUI mode, a few of them are exclusively GUI-oriented. [This list]("http://doc.trolltech.com/4.3/modules.html") should allow you to figure it out by yourself. :)

---

### Post by Lord Illidan on 2008-01-21
EDIT : 
> **aks44 said:**
> The Qt library is composed of several sub-modules.

Some of them can be used both in console and GUI mode, a few of them are exclusively GUI-oriented. [This list]("http://doc.trolltech.com/4.3/modules.html") should allow you to figure it out by yourself. :)

Ah...I wasn't aware of this. Thanks for the link!


Qt-console was an april fool's joke : [http://dot.kde.org/1017629736/](http://dot.kde.org/1017629736/)

To program for the console, use c++, perhaps with ncurses to make more effective user interfaces.

---

### Post by aks44 on 2008-01-21
> **Lord Illidan said:**
> QT is a graphical toolkit, you can't develop console applications for it.

Qt-console was an april fool's joke : [http://dot.kde.org/1017629736/](http://dot.kde.org/1017629736/)

I guess that's why the QtGui module is separated from eg. QtCore, QtNetwork, QtSql, QtXml, ... ;)

Well... your link is almost 6 years old... :)

NOTE: I'm not implying you can actually write "console GUIs" (which is the goal of ncurses, and the subject of that April's fool you mentioned). But you can definitely use (big parts of) the Qt library even in console mode.

---

### Post by igjurisk on 2008-01-21
But then can somebody explain me this:  [http://doc.trolltech.com/4.3/console-edition-classes.html]("http://doc.trolltech.com/4.3/console-edition-classes.html")

Well if there is no way to write console apps with Qt is there anything similar for console?

Thanks again.

Edit: and this article at wiki: [http://en.wikibooks.org/wiki/X_Windows_Programming/Qt]("http://en.wikibooks.org/wiki/X_Windows_Programming/Qt")

---

### Post by aks44 on 2008-01-21
> **igjurisk said:**
> But then can somebody explain me this:  [http://doc.trolltech.com/4.3/console-edition-classes.html]("http://doc.trolltech.com/4.3/console-edition-classes.html")

Well if there is no way to write console apps with Qt is there anything similar for console?

Granted, this is the Commercial Editions page, but this also applies to the Open Source Edition:
[http://doc.trolltech.com/4.3/commercialeditions.html](http://doc.trolltech.com/4.3/commercialeditions.html)



> **igjurisk said:**
> Edit: and this article at wiki: [http://en.wikibooks.org/wiki/X_Windows_Programming/Qt]("http://en.wikibooks.org/wiki/X_Windows_Programming/Qt")
As far as I can tell, this article mentions the possibility of writing console apps with Qt. :-\" FWIW the commercial "Console edition" is also included in the "Open Source edition" along with many other modules.

---

### Post by igjurisk on 2008-01-21
Thanks for your replies, my confusion is gone now.

:popcorn:

---

