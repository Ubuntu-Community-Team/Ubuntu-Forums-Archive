---
title: "GUI programming reccommendation???"
date: 2008-08-29
forum: Programming Talk
---

### Post by raedbenz on 2008-08-29
Hi,,
I want to learn GUI programming. I am working on Ubuntu8.04.
My scope is to read/write to parallel or serial ports and run simple graphics according the status of the hardware, in other words a simple data acquisition software.
i know how to do system programming in Linux (using system calls, GNU C functions, etc...)
what software can i use to do this task?? i need one with good support and most important with tutorials.
thanks

---

### Post by mssever on 2008-08-29
> **raedbenz said:**
> Hi,,
I want to learn GUI programming. I am working on Ubuntu8.04.
My scope is to read/write to parallel or serial ports and run simple graphics according the status of the hardware, in other words a simple data acquisition software.
i know how to do system programming in Linux (using system calls, GNU C functions, etc...)
what software can i use to do this task?? i need one with good support and most important with tutorials.
thanks
If you head over to the Programming Talk subforum, there's a sticky there with a bunch of info to help you get started.

---

### Post by mb_webguy on 2008-08-29
I would suggest for languages C++, Java, Python, or Perl, as those are supported by both GTK+ and Qt (the toolkits for Gnome and KDE, respectively).  C++ or Java may be better choices for what you're wanting to do, since I'm not sure if it would be possible (or at least easy) for Python or Perl, as scripting languages, to work with hardware on such a basic level as you're talking about.

If you want your GUI to integrate with Gnome, you'll need the [GTK+ toolkit]("http://www.gtk.org/").  If you want your GUI to integrate with KDE, you'll need the [Qt toolkit]("http://trolltech.com/products/qt/").  Each of them has tutorials on its website.

As for IDEs, NetBeans is good for Java, and I've heard good things about [KDevelop]("http://www.kdevelop.org/"), [anjuta]("http://anjuta.sf.net/"), and [code::blocks]("http://www.codeblocks.org/").  Code::blocks is supposed to be very similar to Visual Studio, if you've used that before.  Go with KDevelop if you're going to be using Qt.

---

### Post by Rocket2DMn on 2008-08-29
moved to Programming Talk.

---

### Post by raedbenz on 2008-08-29
is it possible to use C langauge with any IDE for GUI?

---

### Post by StOoZ on 2008-08-29
if you want to use C , use GTK+ , you can also use gtkmm for C++ , or Qt or what I use (with C++) , wxWidgets.

---

### Post by LaRoza on 2008-08-29
See the sticky for GUI toolkits in common use by Linux apps (and non Linux apps)

---

### Post by raedbenz on 2008-08-29
HI,,
does the KDE work under Ubuntu? because Ubuntu uses GNOME for all its graphical interfaces ?
thanks

---

### Post by StOoZ on 2008-08-29
you can install KDE  separately , and on the login screen select which one you want to use (GNOME / KDE )

---

### Post by Rocket2DMn on 2008-08-29
> **raedbenz said:**
> HI,,
does the KDE work under Ubuntu? because Ubuntu uses GNOME for all its graphical interfaces ?
thanks

Yes, that is what Kubuntu is.  You can instal KDE without re-install Ubuntu though.  Have a look at [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by LaRoza on 2008-08-29
> **raedbenz said:**
> HI,,
does the KDE work under Ubuntu? because Ubuntu uses GNOME for all its graphical interfaces ?
thanks

You can use QT in GNOME and GTK+ in KDE. It just takes a second longer to start up (if the libraries aren't loaded)

---

