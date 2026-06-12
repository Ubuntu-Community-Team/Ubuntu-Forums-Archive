---
title: "what is the equivalent of windowAPI ?"
date: 2013-02-08
forum: Programming Talk
---

### Post by fdrake on 2013-02-08
I just recently jumped into C++ programming and I came across the different king of C++ programming in the windows environment(windows API sets). It looks like it is divided into a dozen of branches, among whom we find win32-kervel, dll-registry, NET and so on . What is the equivalent windows-API (libraries) in the Linux environment?

Maybe I am asking the question in the wrong way?

What I mean is : how can I linux software developer in C++ finds the libraries/components needed to create gui/mouse/network.control etc... for his program?

---

### Post by zombifier25 on 2013-02-08
Looks like you're looking for a GUI toolkit. Linux uses a lot of GUI toolkits, the two most popular of them being [GTK](http://www.gtk.org/) (since you code in C++, use [gtkmm](http://www.gtkmm.org/en/)) and [Qt](http://qt.digia.com/) (already built upon C++). And then there's WxWidgets, FLTK, ... but if you're using a Linux systems, most of the apps you are using right now are written using either of those toolkits.

ALso, these toolkits are cross-platform, so you can port your apps to Windows or Mac.

(personally I recommend Qt, since it's easier to learn, has more documentation, and it's not just a GUI toolkits, it's an entire application framework, like Windows' API.

---

### Post by fdrake on 2013-02-08
> **zombifier25 said:**
> Looks like you're looking for a GUI toolkit. Linux uses a lot of GUI toolkits, the two most popular of them being [GTK](http://www.gtk.org/) (since you code in C++, use [gtkmm](http://www.gtkmm.org/en/)) and [Qt](http://qt.digia.com/) (already built upon C++). And then there's WxWidgets, FLTK, ... but if you're using a Linux systems, most of the apps you are using right now are written using either of those toolkits.

ALso, these toolkits are cross-platform, so you can port your apps to Windows or Mac.

(personally I recommend Qt, since it's easier to learn, has more documentation, and it's not just a GUI toolkits, it's an entire application framework, like Windows' API.
zombifier25 thank you very much. What you said is more than I was expecting to be possible . So you thing should I start with qt and its documentation?  can you suggest any link/ book or site where I can get started ...

much appreciated.

---

### Post by zombifier25 on 2013-02-08
First, install the meta-package qt-sdk to install everything you need to develop Qt apps.

Qt has a lot of documentation scattered across the Internet, so Google for Qt tutorials or documentations, and choose one that fits you. I'm currently using the book "C++ GUI programming with Qt4", which is pretty good in explaining the basics.

---

### Post by fdrake on 2013-02-08
that seems like a good book I'll start from there. Just downloaded now and it seems pretty easy to follow. 560 pages is not that bad if it wasn't that I could only find *.chm file not *.pdf. I'll try to get a better reader than hh in wine.

thank you very much , you opened me the door to a new path to follow.

:guitar:

---

### Post by Habitual on 2013-02-08
[try this]("http://www.google.com/search?q=qt+programming+tutorials+filetype:pdf")[URL="http://www.google.com/search?q=qt+programming+tutorials+filetype:pdf"]
[/URL]

---

### Post by fdrake on 2013-02-08
> **Habitual said:**
> [try this]("http://www.google.com/search?q=qt+programming+tutorials+filetype:pdf")[URL="http://www.google.com/search?q=qt+programming+tutorials+filetype:pdf"]
[/URL]
 thank you Habitual, interesting pdfs

---

