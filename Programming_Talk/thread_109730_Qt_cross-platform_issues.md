---
title: "Qt cross-platform issues"
date: 2005-12-29
forum: Programming Talk
---

### Post by exhuma.twn on 2005-12-29
For the past months I am working on a small project written entirely in Python. As along the way, I needed to use a GUI Toolkit I boneheadedly jumped into the cold water and used Qt. The integration of Qt3 with Python is fairly well done, however the project also needs to run on Windows. But Qt3 is not free for Windows. So I made the decision to port to Qt4, where you can get an Open-Source license for free.

Then the problems start. There are [bindings to Qt4](http://www.riverbankcomputing.co.uk/pyqt/) available for Python as [development snapshots]("http://www.river-bank.demon.co.uk/download/snapshots/PyQt4/"). Unfortunately these bindings require at least Qt4.1

Now, The latest release of Qt in the packages I found in Ubuntu are 4.0.0 in breezy and 4.0.1 in dapper. As I am usnig KDE as WM I suppose removing the currently installed Qt libs alltogether and installnig Qt 4.1 from source is not such a good idea as it seems that Ubuntu uses different locations for these.

Does anyone have any advice on how I could install qt4.1 on ubuntu without breaking everything I use?

---

### Post by asimon on 2005-12-29
[QUOTE=exhuma.twn]
Now, The latest release of Qt in the packages I found in Ubuntu are 4.0.0 in breezy and 4.0.1 in dapper. As I am usnig KDE as WM I suppose removing the currently installed Qt libs alltogether and installnig Qt 4.1 from source is not such a good idea as it seems that Ubuntu uses different locations for these.
[/quote]
You don't have to remove any qt3 packages at all to install Qt 4.1 from source (Qt 4 has btw other library names then Qt 3, therefore there is no conflict between qt3 and qt4 libs). I for example have nearly most qt3 packages from Ubuntu installed (including -dev packages) and have qt 4.1 in some /mnt/scracht/qt folder. If I want to use this Qt 4.1 I just set PATH (so that moc for example is taken from /mnt/scratch/qt/bin and not from /usr/bin) and QTDIR accordingly. Just install no qt4 packages from Breezy/Dapper (KDE is using Qt 3, and this will not change before KDE4 end of 2006).

---

### Post by exhuma.twn on 2005-12-29
Thanks for the quick reply. I'm currently building ... After that I'll have to see if pyqt4 does my bidding and builds properly. If so, I'll be a happier person :D

---

### Post by asimon on 2005-12-29
[QUOTE=exhuma.twn]I'm currently building ... After that I'll have to see if pyqt4 does my bidding and builds properly. If so, I'll be a happier person :D[/QUOTE]
Good luck, I had none with the ruby binding. Works great with Qt3, but I want to use Qt4 for the same reasons as you. I am eagerly waiting for a QtRuby 4 release ...

---

### Post by exhuma.twn on 2005-12-29
Seems I was lucky to chose Python then. I was looking at Ruby too at the very beginning of the project. And I am supposed to finish it by the end of the year. Seems my boss will have to wait a little bit longer. Good that it's nothing of high priority ;)

phew... compiling qt sure takes it's time...

---

### Post by exhuma.twn on 2005-12-30
Hmpf.... after leaving Qt compiling over night, I am stuck again.... the Python bindings have compile-time errors... :(

As a recap of things I've done so far:

[LIST]
[*]Downloaded [Qt 4.1](http://www.trolltech.com/download/qt/x11.html)
[*]Downloaded and installed **latest snapshot** of [Sip](http://www.river-bank.demon.co.uk/download/snapshots/sip/) (This is required to build PyQt).
[*]I got the latest PyQt [snapshot](http://www.river-bank.demon.co.uk/download/snapshots/PyQt4/)
[*] compiled Qt with: ```
./configure --prefix="/data/optlib" && make && make install
```
[*]Added [COLOR="Blue"]export PATH="/data/optlib/bin:${PATH}"[/COLOR] to my ~/.bashrc
[*]configured pyqt with ```
python configure.py -q /data/optlib -b /data/optlib/bin
```
[*]ran "make" and it failed
[*]Right now I am digging through the code to find the culprit. Dunno yet if it comes from Sip or PyQt...
[/LIST]

If I have any more news, I let you guys know


[edit]
Here's the error message for interested people:
```
g++ -c -pipe -fPIC -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_CORE_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_OPENGL_LIB -DQT_SQL_LIB -DQT_XML_LIB -I. -I/usr/include/python2.4 -I/data/optlib/include -I/data/optlib/include/QtCore -I/data/optlib/include/QtGui -I/data/optlib/include/QtNetwork -I/data/optlib/include/QtOpenGL -I/data/optlib/include/QtSql -I/data/optlib/include/QtSvg -I/data/optlib/include/QtXml -I/data/optlib/mkspecs/default -I/usr/X11R6/include -o sipQtCoreQPersistentModelIndex.o sipQtCoreQPersistentModelIndex.cpp
sipQtCoreQPersistentModelIndex.cpp: In function &#8216;PyObject* meth_QPersistentModelIndex_data(PyObject*, PyObject*)&#8217;:
sipQtCoreQPersistentModelIndex.cpp:95: error: &#8216;class QPersistentModelIndex&#8217; has no member named &#8216;data&#8217;
make: *** [sipQtCoreQPersistentModelIndex.o] Error 1
```
[/edit]

---

### Post by asimon on 2005-12-30
> **exhuma.twn]
[edit]
Here's the error message for interested people:
```
g++ -c -pipe -fPIC -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_CORE_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_OPENGL_LIB -DQT_SQL_LIB -DQT_XML_LIB -I. -I/usr/include/python2.4 -I/data/optlib/include -I/data/optlib/include/QtCore -I/data/optlib/include/QtGui -I/data/optlib/include/QtNetwork -I/data/optlib/include/QtOpenGL -I/data/optlib/include/QtSql -I/data/optlib/include/QtSvg -I/data/optlib/include/QtXml -I/data/optlib/mkspecs/default -I/usr/X11R6/include -o sipQtCoreQPersistentModelIndex.o sipQtCoreQPersistentModelIndex.cpp
sipQtCoreQPersistentModelIndex.cpp: In function &#8216 said:**
>  Error 1
```
[/edit]
The [QPersistentModelIndex class](http://doc.trolltech.com/4.1/qpersistentmodelindex.html) definitely has an 'data' member, see line 97 of src/corelib/kernel/qabstractitemmodel.h. It could be a bug in the SIP snapshot.

Maybe you want to look at the [PyKDE Mailing List](http://mats.imk.fraunhofer.de/mailman/listinfo/pykde). I wouldn't wonder if you find there more PyQt expertise than on this forum. ;-)

---

### Post by exhuma.twn on 2006-01-04
Thanks, I'll look into that. Unfortunately something more important came up recently and I have to shift my priorities accordingly. This means putting this current project on ice for now.

My last finding though looks promising. I found [a way to get GPL'ed Qt for windows]("http://kscraft.sourceforge.net/convert_xhtml.php?doc=pyqt-windows-install.xhtml"). With that it might just be possible to use the well established PyQt3 bindings. However I have not yet had time to get that working.

---

### Post by Sanne on 2006-01-04
If you haven't seen this, there seems to be a [PyQtGPL Windows binary package]("http://pythonqt.vanrietpaap.nl/") including

Qt 3.3.4
Sip 4.1.1
QScintilla 1.62
PyQt 3.13

according to the [readme]("http://www.quadgames.com/download/pythonqt/PyQtGPL.README.txt").

I came across this link on the [link page of the Eric3 website]("http://www.die-offenbachs.de/detlev/eric3-links.html") (last link on page).

---

