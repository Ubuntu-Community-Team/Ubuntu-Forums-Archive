---
title: "GUI Programming for Ubuntu"
date: 2008-04-27
forum: Programming Talk
---

### Post by darkwing_duck on 2008-04-27
I'm writing a simple program which requires a GUI front-end for some simple shape drawing (boxes, lines, etc), file management, etc.  I program the back-end using C++.  

However, I've just recently converted to Ubuntu and I'm not familiar with my options.  I'm developing for my own Ubuntu/Linux environment, but I'd like to be in a position to port the GUI to Windows if requested.  I'd really like something similar to the Visual Studio suite.

Any positive advice is greatly appreciated.  T.I.A.
:popcorn:

---

### Post by tamoneya on 2008-04-27
[http://www.gtk.org/](http://www.gtk.org/)

---

### Post by mssever on 2008-04-27
Also check out glade.

---

### Post by moephan on 2008-04-27
++glade

Glade is a great tool for creating non-trivial user interfaces, and it keeps presentation totally separate from code. It's very useful.

---

### Post by JupiterV2 on 2008-04-28
While I use Glade and GTK+ myself, there is also Qt from TrollTech and wxWidgets.

GTK+ - written in C with bindings for many languages(python, C++, etc); the native "Gnome" look (GTK = Gnome [UI] Tool Kit). LGPL license. Not all features "look right" in KDE desktop.

Qt - written in C++; GPL license; provides native looks for several OS's 
including, but not limited to, Windows and MacOS.

wxWidgets - written in C++; LGPL license; provides native looks for several OS's including, but not limited to, Windows and MacOS.

If there isn't one already, could we not have a sticky with this information on GUI interfaces?

---

### Post by LaRoza on 2008-04-28
> **JupiterV2 said:**
> 
wxWidgets - written in C++; LGPL license; provides native looks for several OS's including, but not limited to, Windows and MacOS.

If there isn't one already, could we not have a sticky with this information on GUI interfaces?

And on Linux, it is uses GTK one Linux.

Ok, I will work on the FAQ.

(Post more suggests here in the meantime everyone)

---

### Post by StOoZ on 2008-04-28
@Laroza , by the way, I eventually decided to learn GTK+ (gtkmm since im using C++)

:guitar:

---

### Post by darkwing_duck on 2008-05-01
Thanks all!

I've finished my first, very simple, tutorial on using Glade and GTK+.  I'm impressed.  I'll check out the other suggested stuff soon (took me a while to figure out how to compile the darned thing).  

My only concern is that I will one day want to port my App to Windows and/or Mac.
:lolflag:

---

### Post by LaRoza on 2008-05-01
> **darkwing_duck said:**
> Thanks all!

I've finished my first, very simple, tutorial on using Glade and GTK+.  I'm impressed.  I'll check out the other suggested stuff soon (took me a while to figure out how to compile the darned thing).  

My only concern is that I will one day want to port my App to Windows and/or Mac.


Just make sure they have the libraries needed. Open Source does wonders for this.

---

### Post by ZuLuuuuuu on 2008-05-02
> **darkwing_duck said:**
> My only concern is that I will one day want to port my App to Windows and/or Mac.

You can port your app to Windows since GTK supports Windows and AFAIK MacOS. There are several popular Windows programs which uses GTK, like GIMP, Inkscape, Sylpheed etc.

---

### Post by scourge on 2008-05-02
> **darkwing_duck said:**
> My only concern is that I will one day want to port my App to Windows and/or Mac.
:lolflag:

In that case I recommend wxWidgets. It uses the native gui elements on every platform, so your application won't look like crap in Windows or Mac OS 10. And it's a lot more than just a GUI toolkit. I have one project which has a GUI, runs several threads, manages processes, etc. Thanks to wxWidgets I have no platform-specific code anywhere.

---

### Post by tseliot on 2008-05-02
> **darkwing_duck said:**
> My only concern is that I will one day want to port my App to Windows and/or Mac.
:lolflag:
Use QT4 then

---

### Post by Lau_of_DK on 2008-05-02
> **tseliot said:**
> Use QT4 then

Let me just emphasize that statement! Qt4 is a really well crafted cross-platform library. Simply copy your source to Windows and type 

[PHP]
qmake
mingw-32
[/PHP]

And youve got the exact same program running on Windows. Troll-tech has provided all cross-platform libraries needed for OpenGL, networking (FTP, sockets, streams etc.) and some nice extensions on C++'s types. So Qt4 gets a big thumbs up :)

/Lau

---

### Post by darkwing_duck on 2008-05-02
I like the wxWidgets concept of using the native platform GUI.  I just finished a 'hello world' app with wxWidgets.  Not too bad, although I really liked the ease of the Glade3 tool.  

I'll start on a Qt4 'hello world' app now (any good tutorial suggestions?).

I wonder if theres a visual forms editor for wxWidgets?

---

### Post by tseliot on 2008-05-03
I bought 2 books about QT4 but I think these 2 tutorials can help you:
[tutorial1]("http://www.clivecooper.co.uk/tutorial/index.html"), [tutorial2]("http://sector.ynet.sk/qt4-tutorial/")

Here are the [class reference]("http://doc.trolltech.com/4.3/classes.html") and the [qt forum]("http://www.qtforum.org/index.html").

---

### Post by ecs_pf5 on 2008-05-03
Not to knock any others (I haven't tried any) but I've been trying Python & GTK2. I wrote a small GUI app on Kubuntu & ran it in the python interpreter, & ran through the process of making a .deb installer. All good

Then I tried building it on Windows XP 32-bit using Py2exe & packaging it with NSIS. Ran perfect with zero modification to the python source code.

Then I built it on Windows Vista 64-bit. No prob, no source modifications needed.

You seem to need the following installed on the windows machine for the python/gtk/py2exe method:

Python for Windows
[http://www.python.org/download/](http://www.python.org/download/)

Pango
[http://www.pango.org/](http://www.pango.org/)
[http://ftp.gnome.org/pub/GNOME/binaries/win32/pango/1.20/](http://ftp.gnome.org/pub/GNOME/binaries/win32/pango/1.20/)
Pango renders text.

Cairo
[http://ftp.gnome.org/pub/GNOME/binaries/win32/pycairo/1.4/](http://ftp.gnome.org/pub/GNOME/binaries/win32/pycairo/1.4/)
Cairo is a graphics rendering engine

GTK+ 2
[http://ftp.gnome.org/pub/GNOME/binaries/win32/gtk+/2.12/](http://ftp.gnome.org/pub/GNOME/binaries/win32/gtk+/2.12/)
The Gnome Tool Kit (widget kit) itself

PyGTK2
[http://www.pygtk.org/](http://www.pygtk.org/)
[http://ftp.gnome.org/pub/GNOME/binaries/win32/pygtk/2.12/](http://ftp.gnome.org/pub/GNOME/binaries/win32/pygtk/2.12/)

PyGObject
[http://ftp.gnome.org/pub/GNOME/binaries/win32/pygobject/2.14/](http://ftp.gnome.org/pub/GNOME/binaries/win32/pygobject/2.14/)
The GLib Object System, or GObject, is a free software library (covered by the LGPL) that provides a portable object system and transparent cross-language interoperability. PyGObject is the python version.

Py2exe
[http://www.py2exe.org/](http://www.py2exe.org/)
Reads your python program, then grabs together all dependencies & compiles it to a Windows .exe

py2exe will create a distribution folder in e.g. c:/python25/dist/, it contains an .exe, to distribute you can copy the /dist/ folder to /program files/yourprog/ & link the .exe into a desktop shortcut / start menu link / etc. (inno setup or NSIS are good packagers for win)

there were only 2 slightly sticky points, you need a small file 'setup.py' to control how py2exe works; and at some point during the process pango failed to copy a file into /dist/etc/pango/pango.modules so I had to do that manually. 

setup.py: something like:

```

from distutils.core import setup
import py2exe

setup(windows=['hello.py'])


```run it with something like:C:\Python25\>setup.py py2exe

this windows batch script fixes the pango thing if you run into it:

```

cd\
C:
md Python25\dist\etc\pango\
cd GTK
cd bin\
pango-querymodules.exe > C:\Python25\dist\etc\pango\pango.modules

```





I haven't looked at wxWidgets yet, or any others, so they might be even better & I wouldn't know..

---

### Post by days_of_ruin on 2008-05-03
> **JupiterV2 said:**
> While I use Glade and GTK+ myself, there is also Qt from TrollTech and wxWidgets.

GTK+ - written in C with bindings for many languages(python, C++, etc); the native "Gnome" look **(GTK = Gnome [UI] Tool Kit)**. LGPL license. Not all features "look right" in KDE desktop.

Qt - written in C++; GPL license; provides native looks for several OS's 
including, but not limited to, Windows and MacOS.

wxWidgets - written in C++; LGPL license; provides native looks for several OS's including, but not limited to, Windows and MacOS.

If there isn't one already, could we not have a sticky with this information on GUI interfaces?

Actually it stands for "Gimp Tool Kit".

---

### Post by Steveway on 2008-05-03
There is wxGlade. It's basically like Glade only for wxWidgets.
It's also nicely integrated into SPE (Stani's Python Editor).

---

### Post by jespdj on 2008-05-03
I don't think anybody mentioned it yet:

GTK+ is the native GUI toolkit for the GNOME desktop (Ubuntu).
Qt is the native GUI toolkit for the KDE desktop (Kubuntu).

Ofcourse you can run GTK+ programs on KDE and Qt programs on GNOME, but they will look less integrated into the desktop.

---

### Post by Mr. Picklesworth on 2008-05-03
Choosing a GUI lib is really quite a critical detail, and I think it should come down to which platform you are mainly targetting. If you are running this in GNOME (Ubuntu), GTK is the best choice because it will allow your program some nice integration technologies and a look & feel matching other programs on the desktop. If you are running this in KDE (Kubuntu), Qt is the best choice for the same reason.
Using a UI toolkit that does not fit the target desktop environment is recipe for disaster.

As for porting the program, GTK also has a Windows / Mac port. However, I think it is important to target the environment closely even for those ports, unless they are intended as mere quickies. Try to seperate your GUI code from everything else via a layer of abstraction in your own program. In that way, changing to another GUI library for a different platform is dead easy.

I should add: GTK's name is awesome. ((GNU's Not Unix) Image Manipulation Program) Tool Kit. It's also a really nice toolkit; poke around with Glade if you haven't already. Even if you don't plan to use Glade, it should give you a good feel for how GTK behaves and what it has to offer. Qt also has a nice form designer called Qt Designer.

---

### Post by LaRoza on 2008-05-03
> **Mr. Picklesworth said:**
> Choosing a GUI lib is really quite a critical detail, and I think it should come down to which platform you are mainly targetting. If you are running this in GNOME (Ubuntu), GTK is a good choice because it will allow your program some nice integration technologies and a look & feel matching other programs on the desktop. If you are running this in KDE (Kubuntu), Qt is the best choice for the same reason.
Using a UI toolkit that does not fit the target desktop environment is recipe for disaster.

As for porting the program, GTK also has a Windows / Mac port. However, I think it is important to target the environment closely even for those ports, unless they are intended as mere quickies. Try to seperate your GUI code from everything else via a layer of abstraction in your own program. In that way, changing to another GUI library for a different platform is dead easy.

I should add: GTK's name is awesome. ((GNU's Not Unix) Image Manipulation Program) Tool Kit.

QT is also cross platform. wxWidgets is designed to be cross platform, and uses GTK on Linux.

---

