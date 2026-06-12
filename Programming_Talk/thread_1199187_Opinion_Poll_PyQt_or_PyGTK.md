---
title: "Opinion Poll: PyQt or PyGTK?"
date: 2009-06-28
forum: Programming Talk
---

### Post by master_kernel on 2009-06-28
It has been suggested to me to use PyQt instead of PyGTK for developing KernelCheck. Can someone provide further insight into this? Is PyQt harder to learn than PyGTK? What other features does PyQt give (that PyGTK does not have)? IOW, what are the advantages/disadvantages of PyQt?

Thanks,
mk

---

### Post by monraaf on 2009-06-28
Well, Qt is the 'native' toolkit for KDE. GTK+ for Gnome.  Ubuntu is a Gnome based distro and is far more popular than the KDE based Kubuntu.

Unless you're specifically targeting a KDE based distro, I would say go with GTK+.

---

### Post by master_kernel on 2009-07-14
The verdict is sticking with PyGTK.

---

### Post by JordyD on 2009-07-14
> **master_kernel said:**
> The verdict is sticking with PyGTK.

I know you've already decided, but I'd go with PyQt, personally.

PyQt looks native on KDE, GNOME, Mac, and Windows, because it uses each platform's native methods to draw the widgets.

GTK looks native on GNOME. Others if you have the right themes, but that restricts your choices in themes if you're using KDE and it usually has minor differences with the real thing.

---

### Post by master_kernel on 2009-07-15
Wish I'd known this earlier. I'll look into Qt a little more, but since I've already done a lot of work on the next version in Glade, it would be the version after next before I could implement any Qt work.

---

### Post by days_of_ruin on 2009-07-15
> **JordyD said:**
> I know you've already decided, but I'd go with PyQt, personally.

PyQt looks native on KDE, GNOME, Mac, and Windows, **because it uses each platform's native methods to draw the widgets**.

GTK looks native on GNOME. Others if you have the right themes, but that restricts your choices in themes if you're using KDE and it usually has minor differences with the real thing.

[citation needed]

Aren't you thinking of wxwidgets?

---

### Post by JordyD on 2009-07-15
Well, if you've already done it in PyGTK, it *may* be worth it to stick with it. There is a gtk-qt engine that makes gtk blend in better with qt applications, but I have no clue how good it is, since I don't use it.

And considering your application only applies to Linux distros, it doesn't matter whether the toolkit looks natural in Windows or Mac, so if gtk-qt engine works well, then neither toolkit really has the advantage.

[gtk-qt-engine]("http://code.google.com/p/gtk-qt-engine/")

You may want to look into this engine and see how well it works before you change to Qt. I can't help since I don't use it.

Good luck with your application.

**EDIT:** I didn't mention this in my last post because I didn't know of it then.

---

### Post by JordyD on 2009-07-15
> **days_of_ruin said:**
> [citation needed]

Aren't you thinking of wxwidgets?

Does [Wikipedia]("http://en.wikipedia.org/wiki/Qt_(toolkit)#Use_of_native_UI-rendering_APIs") count?

I don't like wxwidgets. It looks funny in my experience.

---

### Post by Tibuda on 2009-07-15
> **JordyD said:**
> I know you've already decided, but I'd go with PyQt, personally.

PyQt looks native on KDE, GNOME, Mac, and Windows, because it uses each platform's native methods to draw the widgets.

GTK looks native on GNOME. Others if you have the right themes, but that restricts your choices in themes if you're using KDE and it usually has minor differences with the real thing.

Qt does not use the native widgets in Gnome. It can mimic Gtk+ themes,  but it is not the same. Gtk+ uses the native widgets in Windows too (not sure about Mac), and also mimic Qt themes.

---

### Post by JordyD on 2009-07-15
> **danielrmt said:**
> Qt does not use the native widgets in Gnome. It can mimic Gtk+ themes,  but it is not the same. Gtk+ uses the native widgets in Windows too (not sure about Mac), and also mimic Qt themes.

No, GTK+ [*emulates*]("http://en.wikipedia.org/wiki/Gtk%2B#Design") the widgets on Windows through GTK engines. Qt uses Windows and Mac's native toolkits.

Regardless, if you're already using GTK, I recommend you stick with it. Earlier when I posted, I was not aware of the gtk-qt engine which allows GTK to emulate Qt in the same way Qt emulates GTK.

---

### Post by Tibuda on 2009-07-15
> **JordyD said:**
> No, GTK+ [*emulates*]("http://en.wikipedia.org/wiki/Gtk%2B#Design") the widgets on Windows through GTK engines. Qt uses Windows and Mac's native toolkits.

Thanks, I stand corrected. I was really sure Pidgin, GIMP and Deluge were using native widgets. I think Gtk+ is doing a good job emulating Windows widgets.

---

### Post by nrs on 2009-07-15
> **danielrmt said:**
> Thanks, I stand corrected. I was really sure Pidgin, GIMP and Deluge were using native widgets. I think Gtk+ is doing a good job emulating Windows widgets.
Really? GTK+ apps on Windows have also stood out like a sore thumb to me. I have an obsessive attention to detail though. 

While the OP has already made up his mind: 

I find the documentation for (Py)Qt infinitely superior. I generally use it when multi-platform is more than an afterthought, or if I plan on doing something relatively out of the oridinary. If I'm doing any OpenGL stuff I go with Qt, I find gtkglext to be an intrusive hack. 

In C++ I generally use GTKmm when I want something "simpler". There is little difference between PyQt and PyGTK in terms of ease though, IMO. 

As far as features, (Py)Qt wins hands down. Ignoring the greater variety of widgets, etc. one must remember that Qt is more than just a GUI toolkit: 
> The **QtHelp** module contains classes for creating and viewing searchable documentation and being able to integrate online help with PyQt applications. It is based on the C++ port of the Lucene text search engine.
The **QtNetwork** module contains classes for writing UDP and TCP clients and servers. It includes classes that implement FTP and HTTP clients and support DNS lookups. Network events are integrated with the event loop making it very easy to develop networked applications.
The **QtOpenGL** module contains classes that enable the use of OpenGL in rendering 3D graphics in PyQt applications.
The **QtScript** module contains classes that enable PyQt applications to be scripted using Qt's JavaScript interpreter.
The **QtSql** module contains classes that integrate with open-source and proprietary SQL databases. It includes editable data models for database tables that can be used with GUI classes. It also includes an implementation of [SQLite]("http://www.sqlite.org/").
The **QtSvg** module contains classes for displaying the contents of SVG files. It supports the static features of SVG 1.2 Tiny.
The **QtTest** module contains functions that enable unit testing of PyQt applications. PyQt does not implement the complete Qt unit test framework. Instead it assumes that the standard Python unit test framework will be used and implements those functions that simulate a user interacting with a GUI.
The **QtWebKit** module implements a web browser engine based on the [WebKit]("http://webkit.org/") open source browser engine used by Apple's Safari. It allows the methods and properties of Python objects to be published and appear as JavaScript objects to scripts embedded in HTML pages.
The **QtXml** module implements SAX and DOM interfaces to Qt's XML parser.
The **QtXmlPatterns** module implements XQuery and XPath support for XML and custom data models.
The **phonon** module implements a multimedia framework that enables the use of audio and video content in PyQt applications. On Windows DirectX is used as the backend, on MacOS/X QuickTime is used as the backend, and on Linux GStreamer is used as the backend.
Threading classes, etc.

---

### Post by monraaf on 2009-07-15
> **nrs said:**
> 
I find the documentation for (Py)Qt infinitely superior.


I think the PyGTK documentation is excellent. Can you tell me where the PyGTK documentation is lacking in your opinion?

> 
As far as features, (Py)Qt wins hands down. Ignoring the greater variety of widgets, etc. one must remember that Qt is more than just a GUI toolkit: 
Threading classes, etc.

The guy is using Python, he already gets all that stuff and more for free.

---

### Post by nrs on 2009-07-15
> **monraaf said:**
> I think the PyGTK documentation is excellent. Can you tell me where the PyGTK documentation is lacking in your opinion?
It often lacks verbosity where required. There the documentation often provides little more insight than the name of the method. Take [http://www.pygtk.org/docs/pygtk/class-gdkpixbuf.html#method-gdkpixbuf--get-pixels](http://www.pygtk.org/docs/pygtk/class-gdkpixbuf.html#method-gdkpixbuf--get-pixels) nevermind the typo, what is that telling me that the method name isn't? What is it not telling me? Everything. Presumably if I'm using get_pixels() I want to play with the data, but it gives no clue as to how the data is represented, formatted, etc. Contrast to this [http://library.gnome.org/devel/gdk-pixbuf/stable/gdk-pixbuf-gdk-pixbuf.html#gdk-pixbuf-get-pixels](http://library.gnome.org/devel/gdk-pixbuf/stable/gdk-pixbuf-gdk-pixbuf.html#gdk-pixbuf-get-pixels) note the link which explains all.

Forget about extensions like gtkglext.

> **monraaf said:**
> 
The guy is using Python, he already gets all that stuff and more for free.
Sure, he can get everything listed in separate modules/libraries, just as I can in Python/C++. However, separate modules means separate API, separate documentation, and separate support, ...

---

### Post by JordyD on 2009-07-15
Although I've never used PyQt, it seems to me that Qt documentation is more complete than GTK documentation. Perhaps because there is a company (Nokia, once Trolltech), behind it?

---

### Post by nrs on 2009-07-15
> **JordyD said:**
> Although I've never used PyQt, it seems to me that Qt documentation is more complete than GTK documentation. Perhaps because there is a company (Nokia, once Trolltech), behind it?
It may not be popular opinion, but I think it's part of it. Writing documentation isn't sexy, and I don't know anyone who thinks it is. You'd have to pay me to write it. I find Plain-Jane GTK+ reasonably documented, with a decent amount of examples though, so if you understand C you can always fallback on it if you find the docs for whatever binding your using incomplete.

---

### Post by JordyD on 2009-07-15
> **nrs said:**
> It may not be popular opinion, but I think it's part of it. Writing documentation isn't sexy, and I don't know anyone who thinks it is. You'd have to pay me to write it. I find Plain-Jane GTK+ reasonably documented, with a decent amount of examples though, so if you understand C you can always fallback on it if you find the docs for whatever binding your using incomplete.

Actually, I get so frustrated when developers don't write documentation, if I wrote my own library, you'd probably find video tutorials on my site.

---

### Post by monraaf on 2009-07-16
> **nrs said:**
> It often lacks verbosity where required. There the documentation often provides little more insight than the name of the method. 

I don't think this is a fair representation of the PyGTK documentation that you are giving here, sure there are some methods that aren't that well documented as one would like them to be, probably because these methods aren't really used that much. I'm sure there are areas in which your 'infinitely superior' PyQt documentation is lacking. Even the website with the PyQt documentation acknowledges that:

> 
Because this is based on the Qt C++ documentation it still contains C++ code fragments, broken links etc


Anyway, I have no interest in trashing PyQt so I won't even go there. I'm very pleased with PyGTK and the quality of the documentation and certainly can't find myself in the claim that 'it often lacks verbosity'.

---

### Post by lykwydchykyn on 2009-07-16
Though I personally prefer QT, the last time I looked the **pyQt** documentation is severly lacking.  The (C++) QT documentation is the absolute bees-knees, but I had such a hard time finding any PyQT docs online that I just went and sprang for the book.  In fact, the official docs from Riverbank are horrid, and (last time I looked at them) contained code samples that were not even Python (looked like C++ that someone tried to convert to python with some kind of find-and-replace script).  Maybe they fixed that...

EDIT:  Well, they now have all the classes listed, but this caveat still appears: > Because this is based on the Qt C++ documentation it still contains C++ code fragments, broken links etc. These will be fixed in future releases.

from [http://www.riverbankcomputing.co.uk/static/Docs/PyQt4/html/classes.html](http://www.riverbankcomputing.co.uk/static/Docs/PyQt4/html/classes.html)

EDIT2: Oops, monraaf already posted that.  I don't pay attention this time of night...

Apart from all the extra stuff that QT adds, the biggest difference I saw between the two libraries is the way event handling is implemented.  I prefer the way QT does it, personally.  

It's been a while since I wrote something with PyGTK, and I was probably doing it badly, but it seemed like I had to do a lot of silly stuff explicitly, like calling show() on every dadblame widget.

---

### Post by monraaf on 2009-07-16
> **lykwydchykyn said:**
> It's been a while since I wrote something with PyGTK, and I was probably doing it badly, but it seemed like I had to do a lot of silly stuff explicitly, like calling show() on every dadblame widget.

A show_all() on the container widget suffices ;)

---

### Post by JordyD on 2009-07-16
> **lykwydchykyn said:**
> The (C++) QT documentation is the absolute bees-knees

This is actually the only documentation I've used, so that would explain why I love their documentation so much.

---

### Post by lykwydchykyn on 2009-07-16
> **monraaf said:**
> A show_all() on the container widget suffices ;)

My bad.  Demonstrates why I shouldn't criticize things I don't use regularly...

---

### Post by master_kernel on 2009-07-16
So which would look best on both KDE and Gnome? PyGTK or PyQt?

---

### Post by OutOfReach on 2009-07-16
> **master_kernel said:**
> So which would look best on both KDE and Gnome? PyGTK or PyQt?

I would say PyQt...because on KDE Qt will obviously look native and in GNOME (with the help of QGtkStyle) it will look native as well.
but PyGTK on the other hand will look native on GNOME (obviously), but not so native on KDE...sure you can try QtCurve or GTK-Qt-Engine but they still won't look fully native.

---

### Post by Tibuda on 2009-07-16
> **OutOfReach said:**
> I would say PyQt...because on KDE Qt will obviously look native and in GNOME (with the help of QGtkStyle) it will look native as well.
but PyGTK on the other hand will look native on GNOME (obviously), but not so native on KDE...sure you can try QtCurve or GTK-Qt-Engine but they still won't look fully native.

QGtkStyle looks native, but you can tell the difference. Using your own words, it's not "fully native". There are also some random font rendering issues.

---

### Post by master_kernel on 2009-07-16
So I guess the verdict here is neither is 'fully' compatible with another. I'll install a Kubuntu machine in Virtualbox and see how my PyGTK version runs on that.

---

### Post by zolookas on 2009-07-17
I think Qt + QGtkStyle on GNOME wins, because applications then use not only GTK+ themes, but even file open/save dialogs. If you want GTK+ apps to use KDE file open/save dialogs, you need to [use hacks]("http://www.kde-apps.org/content/show.php?content=36077") which require you to modify all shortcuts to your GTK applications.

Plus QGtkStyle supports FreeDesktop icons. Look here (screenshots): [http://labs.trolltech.com/blogs/2009/02/13/freedesktop-icons-in-qt/](http://labs.trolltech.com/blogs/2009/02/13/freedesktop-icons-in-qt/)

---

### Post by monraaf on 2009-07-17
Despite all the propaganda here the few Qt apps I've used never looked 100% native on my Gnome desktop. Maybe the programmers of these applications didn't use some of the features of Qt to give it a native look, I don't know and I don't care. All I can say is that as a Gnome user I prefer Gtk+ applications on my desktop, not Qt, not WxWidgets nor applications using any other toolkit. Obviously If I was a Kde user my preference would be for Qt applications.

Now what if 80% of the users of your application are using a Gnome based distro, do you really want to annoy them with an application that doesn't really belong there just to satisfy 20% of your users? Of course the same argument can be made in favour of Qt, it just happens to be that Gnome based distro's are more popular than Kde ones.

---

### Post by master_kernel on 2009-07-17
> **monraaf said:**
> Despite all the propaganda here the few Qt apps I've used never looked 100% native on my Gnome desktop. Maybe the programmers of these applications didn't use some of the features of Qt to give it a native look, I don't know and I don't care. All I can say is that as a Gnome user I prefer Gtk+ applications on my desktop, not Qt, not WxWidgets nor applications using any other toolkit. Obviously If I was a Kde user my preference would be for Qt applications.

Now what if 80% of the users of your application are using a Gnome based distro, do you really want to annoy them with an application that doesn't really belong there just to satisfy 20% of your users? Of course the same argument can be made in favour of Qt, it just happens to be that Gnome based distro's are more popular than Kde ones.

I've only heard one complaint, as of recent. Maybe people who compile kernels tend to use Gnome more that KDE?

---

### Post by days_of_ruin on 2009-07-17
> **master_kernel said:**
> I've only heard one complaint, as of recent. Maybe people who compile kernels tend to use Gnome more that KDE?

More people just use gnome.

---

### Post by JordyD on 2009-07-17
I use GNOME. I love KDE's look though. If there was a mashup of Oxygen+GNOME, I would be delighted.

---

### Post by Tibuda on 2009-07-17
> **JordyD said:**
> I use GNOME. I love KDE's look though. If there was a mashup of Oxygen+GNOME, I would be delighted.

Have you searched gnome-look.org? There are some Oxygen clones there.

---

### Post by L815 on 2009-07-17
I would say Qt just because I know of many more applications written in Qt for cross-platform than Gtk.

---

### Post by gorilla on 2009-07-18
Since Qt is not just a GUI toolkit but a whole application programming framework (designed with platform independence in mind), there is quite some duplication between a language's standard library and Qt.
In many cases you could write an app in pure Qt, minimizing use of Python's native library.
The nice thing about this is that you could then quickly port your app to a different language later. Making PyQt good for prototyping.

---

### Post by ahmatti on 2009-07-18
Thanks a lot for this thread for all contributors! I've found it really interesting and helpful. I was thinking about using wxPython for a project of mine, but after reading your posts, making few experiments and looking at some apps I think I'll go with PyQT instead.

I find that QT apps look good also in Gnome,which is currently my desktop of choice. I wan't my  app to look native also on OSX so GTK is not really an option for me.

---

### Post by ahmatti on 2009-08-04
Hmm... I'm just trying to get PyQT working in my Macbook and it is a pain in the ***. It seems that the binary installer (by googling) for QT has some problems so PyQT won't compile.. I'm trying to install qt from source and try again with PyQT. I know that it doesn't affect kernelcheck, but I thought I post anyway.

If somebody is planning a cross platform app (as I am) that they want to distribute easily then wxPython provides a much lighter version, in size and ease of set up. Although its not as versatile as QT, you can create some nice apps with it.

---

### Post by ZuLuuuuuu on 2009-08-04
> **JordyD said:**
> Qt uses Windows and Mac's native toolkits.

After spending some time with Qt I found out that it actually emulates the native toolkits, too, like GTK+. But it emulates them really good that it *does* look like the native widgets. But the "feel" part of the look & feel might slightly differ for some widgets. There are also some speculations that it started using native toolkits with the new versions but I don't know if it is true or not.

Comparing GTK+ with Qt is a little like comparing OpenGL with DirectX. One of them focuses on one topic while the other provides a whole framework. GTK+ focuses on GUI so you have to use it with supporting libraries for other things while Qt tries to be the ultimate solution for your whole program. Comparing wxWidgets with Qt might be more fair in that regard. Actually, GTK+ provides some other libraries as well beside the GUI, but not as rich or as complete or as cross-platoform as Qt's.

Personally I think GTK+ is one of the most elegant libraries ever written. Writing GTK+ applications is, for me, more fun than writing Qt or wxWidgets applications. And it looks and feels beautiful on Gnome (no other widget toolkit like Qt or wxWidgets can emulate that feel 100%). I can't say the same for Windows or Mac ports but they are okay. Qt looks really good on Windows but personally I don't like it on Linux. Also, I don't like the moc thing which makes you write non-C++ code. On the other hand it provides lots of libraries and developer tools. Also installing a development environment for Qt on Windows is a piece of cake, just download ~150MB setup package, install it and you are ready to build Qt programs with one click. GTK+ development is not that easy on Windows, you have to make some configuration etc. On Linux both are easy to install and use.

---

### Post by Umang on 2009-08-04
A bit about tools like Glade and wxGlade:

Glade seems to be getting better very rapidly, and is already far (**far**) better than wxGlade. 

Also, wxGlade will write the code for you, while PyGTK lets you use GTK builder. This means that your code and your GUI layout, etc are not written in the same place and you can develop both at the same time.

I had great problems when I was trying to do something wxGlade didn't let me do. Because I needed to edit the code for that. But if I changed something in wxGlade, then I would lose my changes (unless I used a VCS, which would be like using a sledgehammer to kill a fly!). However, with Glade, I can keep editing my GUI while working on my code. The GUI is in an XML file!

I've only shared my opinion about development tools, I cannot say much about PyGTK and PyQt themselves (PyGTK has been very easy to code with, though I haven't tried PyQt). From the little I have seen, Glade is the best UI development tool when compared to tools for WxPython. 

PS: I didn't try PyQt, because I never understood whether I was allowed to use it or not, and if I was, whether the users could or not.

---

### Post by lykwydchykyn on 2009-08-04
> **Umang said:**
> 
PS: I didn't try PyQt, because I never understood whether I was allowed to use it or not, and if I was, whether the users could or not.

And the licensing FUD continues.  Which part of the license was confusing, the "G", the "P", or the "L"?

---

### Post by JordyD on 2009-08-04
> **lykwydchykyn said:**
> And the licensing FUD continues.  Which part of the license was confusing, the "G", the "P", or the "L"?

Or LGPL for a price.

---

### Post by Umang on 2009-08-05
> **lykwydchykyn said:**
> And the licensing FUD continues.  Which part of the license was confusing, the "G", the "P", or the "L"?:eek: I could have sworn.....

(Did this just change recently or was I blind a few months back?)

---

### Post by lykwydchykyn on 2009-08-05
> **Umang said:**
> :eek: I could have sworn.....

(Did this just change recently or was I blind a few months back?)

They added LGPL as an option back in january, but it's been GPL for years now.

---

