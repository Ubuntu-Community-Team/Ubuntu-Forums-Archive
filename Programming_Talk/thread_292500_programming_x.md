---
title: "programming x"
date: 2006-11-03
forum: Programming Talk
---

### Post by cocteau on 2006-11-03
Hi

Does anyone know of a good online resource for learning how to do program X? 

I've been making terminal programs for a while now and want to know how to create windows and use mouse events.

---

### Post by nereid on 2006-11-04
Do you really want to use the xlibs or just one of the toolkits (GTK, Qt, wxWidgets,...)? The xlibs are a pain in the behind.

---

### Post by cocteau on 2006-11-04
I'm not really shure to be honest. I would like to use something that is platform independent. And since GTK is for Gnome and Qt is for KDE (as far as I understand it anyway), I was looking for something else. Don't know about wxWidgets though.

Besides. I'm really looking for basic functionality. Shadow effects and 3D stuff is way beyong what I'm looking for. Just something that can draw me a window with a few buttons on it.

---

### Post by tseliot on 2006-11-04
QT work in Linux, Mac and Windows.

I suggest you to use QT if you're planning to release your programs under the GPL licence.

---

### Post by nereid on 2006-11-04
I would recommend, that you choose the toolkit that you like best. Qt is a little bit more crossplatform than the others but there is also a Windows version of GTK and wxWidgets, as far as I know, also work on different OS.

---

### Post by Lord Illidan on 2006-11-04
wxWidgets and QT are the most cross platform, I think.

And they work on GNOME and KDE..

---

### Post by moma on 2006-11-04
My recommendation is XCB. 
XCB is a **[COLOR="Red"]replacement[/COLOR]** for the old, ancient, awkward Xlib. 
[http://xcb.freedesktop.org/wiki/](http://xcb.freedesktop.org/wiki/)

Turn to wxWidgets if you want to do cross platform applications in C++.

wxWidgets & Code::Blocks IDE.
[http://wxwidgets.org](http://wxwidgets.org)
+
[http://codeblocks.org](http://codeblocks.org)

+ My Code::Blocks story: "Compiling Code::Blocks IDE from the latest source.....".  Just type the commands and you have C::B up & running in 15 minutes.
[http://linux1.no/node/1938](http://linux1.no/node/1938)

---

### Post by almahtar on 2006-11-04
> **tseliot said:**
> QT work in Linux, Mac and Windows.

I suggest you to use QT if you're planning to release your programs under the GPL licence.

I second that.  Programming with Qt has been a real pleasure, for me.  The documentation is amazing, and it has tons of examples that it ships with (TONS).

---

### Post by cocteau on 2006-11-04
Thanks for the answers. I've been looking around and I seem to be stuck between wxwidgets and qt. I guess the best thing to do from here would be to do a few tutorials and see what I like best.

---

### Post by Eric_T on 2006-11-05
Don't forget to check out Tk as well. It's truly cross-platform, and
really easy to learn for simple stuff like you mention.

---

### Post by cocteau on 2006-11-05
Yup. Added tcl/tk to my todo list :)

---

### Post by Xealot on 2006-11-06
If you are going to use QT, I suggest reading their license first to make sure their ideas fit yours. For example, your program can not be closed source

other than that, good luck. :cool: 


I personally prefer GTK2, allthough some of the widgets are less documentet which i dont like very much :sad:

---

