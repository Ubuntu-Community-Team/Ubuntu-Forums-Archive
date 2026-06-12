---
title: "I want to develop a business application with a QT interface and some sort of SQL DB"
date: 2012-09-30
forum: Programming Talk
---

### Post by kio_http on 2012-09-30
Hi, I would like advice that 

[LIST=1]
[*]Points me out to tools needed and programming languages to learn
[*]Links to good resources to learn how to use those tools in a nutshell
[/LIST]

Basically I need to create an application that works similarly to one implemented with Visual Studio to do stuff like saving records in an SQL database, sorting and producing reports on that data. Organiser functions to give notifications about pending work etc.

I don't mind GTK but would really prefer it to use QT and have a good KDE integration.

Assume I have no programming experience I should be able to use these resources (although I have lots of experience on Windows and some on Linux).

For example I want links to tutorials equivalent to that at [learnvisualstudio.net about c#]("http://www.learnvisualstudio.net/series/visual_csharp_2010_express_edition_for_absolute_beginners/") but for Linux using QT.

I am considering a language like python or ruby to achieve this. I need to develop this fairly quickly so I don't want something with a really steep learning curve. It should be easy enough to link the code with whatever I am using to design the UI.

---

### Post by lisati on 2012-09-30
Have a look here: [http://ubuntuforums.org/showthread.php?t=1766253](http://ubuntuforums.org/showthread.php?t=1766253)

---

### Post by kio_http on 2012-09-30
> **lisati said:**
> Have a look here: [http://ubuntuforums.org/showthread.php?t=1766253](http://ubuntuforums.org/showthread.php?t=1766253)

I've already gone through those threads and I am familiar with OOP etc  concepts as I have a lot of experience with vb.net and c# on Windows.

I just want advice on the best tools to achieve what I want to do and what exactly I should learn. I asked for a complete beginner tutorial as I wouldn't mind going through concepts that I already know again.

---

### Post by squenson on 2012-09-30
[Gambas]("http://gambas.sourceforge.net/en/main.html") could be a valid solution for quick development. As you know vb.net, the syntax of the language should be easy to learn and the GUI has most of the controls you can think of. Gambas also has direct connectors to some DB engines.

---

### Post by kio_http on 2012-09-30
> **squenson said:**
> [Gambas]("http://gambas.sourceforge.net/en/main.html") could be a valid solution for quick development. As you know vb.net, the syntax of the language should be easy to learn and the GUI has most of the controls you can think of. Gambas also has direct connectors to some DB engines.

I don't mind a large learning curve than that and I tried Gambas and it doesn't exactly feel right and nor can it integrate very well with KDE libraries. I think python or ruby would work for me. C++ and QT would be great but I fear C++ might have a very large learning curve.

---

### Post by kalaharix on 2012-09-30
I don't think there is a finer front-end for SQLite, mySQL or Postgres on Linux than Gambas. Particularly if, like me, you have a VB background.

I don't understand the 'nor can it integrate very well with KDE libraries'. The prime developer of Gambas develops Gambas using KDE. QT/GTK in Gambas is a user choice no matter what distro he/she uses.

Where I would caution against Gambas is if you need to be cross-platform. Gambas does not and will not work on Windows. 

My personal feeling is also that gambas is better suited to user-developers rather than someone who is trying to distribute to a wide market. I suspect this is a criticism of Linux rather than Gambas itself, but Gambas is very dependent on external libraries and this can lead to library version problems from distro to distro.

---

### Post by kio_http on 2012-09-30
> **kalaharix said:**
> I don't think there is a finer front-end for SQLite, mySQL or Postgres on Linux than Gambas. Particularly if, like me, you have a VB background.

I don't understand the 'nor can it integrate very well with KDE libraries'. The prime developer of Gambas develops Gambas using KDE. QT/GTK in Gambas is a user choice no matter what distro he/she uses.

Where I would caution against Gambas is if you need to be cross-platform. Gambas does not and will not work on Windows. 

My personal feeling is also that gambas is better suited to user-developers rather than someone who is trying to distribute to a wide market. I suspect this is a criticism of Linux rather than Gambas itself, but Gambas is very dependent on external libraries and this can lead to library version problems from distro to distro.

Gambas has no bindings for KDE libraries. Also I'm not that familiar with VB compared to c#. I don't mind learning new stuff and I have a bit of python experience too.

---

### Post by oldfred on 2012-09-30
When working I used MS Access a lot. But not retired I wanted to learn how to do something like that in Linux. I am not a programmer but have had some classes many years ago.

I decided python was a good language to start with. First I tried gtk with glade, but now have changed my gui to qt with qt designer. I think I have had to learn python,python editor,  qt designer and qt, and more sql as I find that the way I want to use it. Many suggest builders like Django, but I wanted to understand the code  actually doing things (more for learning than doing), not some high level abstraction. 

I use geany, spyder, QT4 Designer for gui, and sqliteman or sqlite database browser to test sql statements. But everyone has their own preferences.

Too many choices but many are free so you can try them
[http://wiki.python.org/moin/PythonEditors](http://wiki.python.org/moin/PythonEditors)

[http://docs.python.org/library/sqlite3.html](http://docs.python.org/library/sqlite3.html)
[http://zetcode.com/db/sqlitepythontutorial/](http://zetcode.com/db/sqlitepythontutorial/)
[http://www.halfcooked.com/presentations/osdc2006/python_databases.html](http://www.halfcooked.com/presentations/osdc2006/python_databases.html)

Sample code:
[http://code.activestate.com/recipes/langs/python/?query_start=1](http://code.activestate.com/recipes/langs/python/?query_start=1)
[http://rosettacode.org/wiki/Python](http://rosettacode.org/wiki/Python)
[http://planet.python.org/](http://planet.python.org/)

HTML/CSS to PDF converter based on Python
[http://pypi.python.org/pypi/xhtml2pdf/](http://pypi.python.org/pypi/xhtml2pdf/)

GUI Programming with Python: QT Edition older 
[http://www.commandprompt.com/community/pyqt/book1](http://www.commandprompt.com/community/pyqt/book1)

[http://wiki.python.org/moin/PyQt](http://wiki.python.org/moin/PyQt)

Three tab database display
[http://www.python-forum.org/pythonforum/viewtopic.php?f=4&t=16781&p=76388](http://www.python-forum.org/pythonforum/viewtopic.php?f=4&t=16781&p=76388)

---

