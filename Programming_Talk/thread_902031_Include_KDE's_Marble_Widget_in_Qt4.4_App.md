---
title: "Include KDE's Marble Widget in Qt4.4 App"
date: 2008-08-26
forum: Programming Talk
---

### Post by xolot1 on 2008-08-26
Im currently writing an application that keeps track of my training (specifically, running/track/cross country).  Ive been using Qt4.4, since I have recently been using Kubuntu but like the idea of writing cross platform programs.  While Ive already learned a bunch, and am quite happy with my progress (MySQL or SQLite to store the data, config file in XML format, etc.), Id really like to use KDE's Marble widget.  I think it would be awesome to be able to plot runs on a map, save the coordinates, and load them later.  Looking at the headers/API, I think I should be able to do this, however Im a little confused as to how to include the widget and its sources.

Is there a convenient release of just the MarbleWidget, or must I adapt the SVN sources to fit my project?  The KDE project uses CMake to generate some of the MOC files required for compilation, however I dont really have any experience with CMake.

Does anyone have any suggestions on how I should approach including this widget?
Thanks:)

---

### Post by henchman on 2008-08-26
Well...

[http://edu.kde.org/marble](http://edu.kde.org/marble)

> Marble is a light weight generic geographical map component for use in your own Qt 4.x / C++ application. It is provided as a library, a QWidget and a KDE 4 KPart and hence can easily get integrated with KDE 4 or Qt 4 applications.

There is also a compiling tutorial on this website :)

---

### Post by xolot1 on 2008-08-27
Thanks for that pointer.  I had read through that site pretty thoroughly, compiling Marble just as the tutorial suggested. I just didnt know how to include the widget in another program.

After some thinking and some digging, I realized I could use the packages libmarble4-kde4 and libmarble-dev-kde4 to provide the headers and packages.  This ended successfully, as I now have a Marble widget getting initialized in my app!

Thanks again

---

