---
title: "win32 api corresponding"
date: 2006-10-06
forum: Programming Talk
---

### Post by nikosft on 2006-10-06
Hi,

When programming in Windows using C++ or VB I was using the win32 API to make various systems calls. What is the corresponding thing in Linux? The functionality I want to provide is handling opened windows, send keystrokes. I want to do it using C++ or even better Python. Any clue?

Thanks

---

### Post by PCSpectra.com on 2006-10-07
> **nikosft said:**
> Hi,

When programming in Windows using C++ or VB I was using the win32 API to make various systems calls. What is the corresponding thing in Linux? The functionality I want to provide is handling opened windows, send keystrokes. I want to do it using C++ or even better Python. Any clue?

Thanks

I've been trying to figure this out myself...and I don't think there is a 1:1 relationship...

My understanding goes like:

Windows provides the WIN32 API which is used for much of what you would want to do. Over the last several years new technologies have been introduced, such as COM which if you wanted to work with Shell functions, was pretty much the only way to do business.

Linux, because of it's modularity and "open" nature...things are better, but also more complicated.

x11 is a low level Windowing API which is more advanced than WIN32 in that I understand it allows remote Windowed access. Designed for a networked environment.

I'm not sure if it provides anything in the sense of Menus, listboxes, etc of just plain vanilla Windowing API (createWindow, setWindowForeGround, destroyWindow, etc)

X is the defacto standard so it's ubiquitous and cannot be avoided???

Ontop of X sit's your distro-specific Window theming, widgets library(s)?

GNome for instance has many layers each which resemble something of the Windows API (but as separate systems so to speak). GNome has the glib library, which is a wrapper around what under Windows one might call the crt (C runtime library). Windows API supersedes the CRT with it's own functions (HeapAlloc, etc).

So using the above analogy, one might say glib memory functions are analogous to Windows API in terms of memory management, as glib sort of extends and wraps the time tested crt library functions.

glib does alot more than Windows API though from what I can tell.

gdk appears to be a abstracted wrapper around the X windowing functions, which would sort of resemble the WIN32 API (CreateWindow as well as DeviceContext functions???)

GTK+ appears to be a Widgets library, which I assume likely uses a base X Window to construct all other specialized types of Windows (Listbox, etc).

Windows I believe has built-in support for a menuing system, as I've never been able to capture the Window handle for a menu :P I'm not sure if X also provides a Menuing system or if the GTK+ widgets library simulates a Menuing system by creating specialized Windows...???

So, using GNome as your Window manager, you have glib, gdk and GTK+ widgets library when put togather in addition to X you have something of a WIN32 API but more modular. I'm not sure what you have under KDE, but I Imagine something similar???

You can further abstract (for cross platform reasons) by using a widgets library such as wxWidgets, which under Windows would be analogous to MFC or OWL, etc. Thats likely the closest in similarity (wxWidgets = MFC) you find.

wxWidgets, from my understanding, provides an API to the native OS API. So when you create a Window and a Menu under Windows...it looks and feels like a Windows window and the menu is an actual Windows Menu, not a GTK+ widget simulating a Windows menu - using a Windows window.

I think thats why some applications feel so clunky under Windows, when they are written for cross platform support. A Windows window is way more expensive in terms of memory, etc on a Windows system that a Windows native menu is. The less Windows you have under Windows, the better off you are, it's why MFC applications are so bullky and clunky when compared to slender WTL or plain SDK applications.

I'm not sure how QT or other widgets libraries fit into the whole picture, but I assume that QT is analogous to wxWidgets, MFC, OWL, etc...

So in saying that, don't take my word for it 100% but I think I'm on the right track in making the above comparisons...and I'm quite confident there isn't a direct 1:1 relationship between the Windows API and any Linux API again because of the vast fundemental design differences between Windows and Linux.

PITA but extremely interesting as well :)

Cheers :)

---

### Post by DavidBell on 2006-10-08
I was wondering the same. I'm half interested in doing some cross platform things. 

As far as I can make out, similar to PCSpectra

* GTK is a bit like MFC for Gnome desktop (but apps run on KDE too). It's got windowing, controls, common dialogs and threads + ???. It's also cross-platform and draws it's own controls.

* Qt is a bit like MFC for KDE (but apps run in Gnome too). Is it windows and controls only? It draws it's own controls too (??)

* wxWidgets is a cross-platform library of controls, that uses the system's native controls instead of drawing them itself (so it looks a more like a native application on all platforms)

(BEGIN EDIT)

* Also forgot I think Mozilla and OpenOffice also provide cross-platform libriaries, don't know what they are like.

(EDIT EDIT)

I don't know what the equivalent of writing a raw Win32 GUI app is. I usually use WTL which is sort of templated Win32 that compiles down to raw Win32. I wonder what the linux equivalent is?

DB

---

### Post by Angry on 2006-10-08
If you are looking for a nice cross-platform gui api, you might be interested in [SDL]("http://www.libsdl.org").  I've been playing around with it (with OpenGL) and it seems to be pretty nice to work with.

---

### Post by hey_ian on 2006-10-09
In my opinion Qt4 is the best and most advanced multiplattform programming lib, it concentrates not only on GUI like others (e.g. FoxToolkit), but delivers a complete extension for C++ including a network lib, an OpenGL lib and others. Qt4 at this time not available at Dapper now, but you can use Qt3. Qt draws its own widgets and there are many plattform which use Qt as their native lib. To use Qt4 or Qt3 your prog MUST be Open Source GPL, else you have to pay license fees, which are very expensive.

GTK+ is the concurent of Qt, but less advanced. It uses a object oriented struct, but is written in C. Using C++ like syntax in C is not very clever. 

wxWidgets is based on Gtk+ on Linux (and newer version have also a Gtk2 port, a native X11 port is available and also a Qt port is in development). It is in my opinion the best way to develop commercial apps for Win and Lin without any license fees.

I am using both, wxWidgets and Qt4. Qt is easier and better, but your apps must be GPL.

---

### Post by DavidBell on 2006-10-10
Thanks, I was tossing up between GTK & wxWidgets. I'll have a go with wxW on win32 (know where I'm going there) and see how they go. My gui stuff isn't complex, fairly simple front ends for bulk calculations. DB

---

### Post by kellogs on 2006-10-10
one thing to note, GTK+ has got a c++ binding called gtkmm , and more language bindings available, you only have to keep a bit the limits of what can be done with the bindings because its not totally a c++ gtk version.

The license in gtk+ and gtkmm is LGPL, so you can use them for commercial purposes and portability without license fees. I dont know which of them is better for portability or which one has better results when comparing apps made in windows gtk+/gtkmm(there are ports of gtk, called gtkwin I think) or linux versions but I read that there are few problems to solve and applications require few changes if not none between OS variants.

edit:fixed.

---

### Post by hey_ian on 2006-10-10
Yes your are right there are indeed changes required to make a GTK or gtkmm apps working on Windows. The same thing you need to do with wxWidgets apps, although it is a smaller number of changes (in Windows wxWidgets requires to use a resource file for the interface and the icon, in the X11 and the GTK port can use .xpm files instead .resource files with icons). The only GUI toolkit which compiles multiplattform without changes is Qt4. Again: If you are building a GPL open source app, I would recommend Qt, otherwise go wxWidgets.

Here is a pretty IDE for wxWidgets, which you can use both on Win and Lin:
[http://www.parinyasoft.com/](http://www.parinyasoft.com/)
MinGW developer Studio
Download MinGWStudioFullSetupPlus.exe file, it has precompiled wxWidgets lib, so you do not have to build it yourself.

---

