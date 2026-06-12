---
title: "GUI toolkit for C++"
date: 2014-05-19
forum: Programming Talk
---

### Post by veddox on 2014-05-19
I'm just starting off learning C++ after two years Java/Python experience. I'd like to be able to create GUIs, but am not sure which toolkit I should use. Nor do I know what is available; currently I am aware of wxWidgets, GTK+, and Qt. I need something that is platform independent (i.e. will also work on Windows), and preferably uses the OS standard look and feel. What would you recommend, and what are the pros and cons of each of the above?

---

### Post by spjackson on 2014-05-20
I don't have personal experience with GTK+. I have some with wxWidgets (v2.x, not 3.0) and quite a lot with Qt (mainly 4.x, not 5). This has mainly been with C++, but also a little Python. In my opinion Qt is much easier to learn and "nicer" to use than wxWidgets. However, I think that the wxWidgets licence is far more programmer friendly. 

In terms of look and feel, I suggest you compare some programs that use each toolkit on the different platforms. [Audacity]("http://audacity.sourceforge.net/") is a good example of wxWdgets (2.8), Gimp (obviously) for GTK+. I can't think of a Qt program that's easily to install on Windows, but you can probably Google for some; alternatively, run the Qt demo & examples.

---

### Post by oldfred on 2014-05-20
I created a tiny app in gtk with MVC and python. I then converted to qt and fortunately had used MVC so it was easier.

I just watched this a few minutes ago. Discusses some of the same issues I went thru and why they were converting from gtk to qt. Linus was one of the programers, but it is a personal project for a few who scuba dive.

gtk to qt Dive program 45 Min
[http://www.youtube.com/watch?v=ON0A1dsQOV0](http://www.youtube.com/watch?v=ON0A1dsQOV0)
[http://subsurface.hohndel.org/documentation/building/](http://subsurface.hohndel.org/documentation/building/)

I think he mentions he used qt creator as his gui.

---

