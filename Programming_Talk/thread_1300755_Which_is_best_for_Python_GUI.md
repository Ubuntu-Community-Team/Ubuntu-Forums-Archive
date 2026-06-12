---
title: "Which is best for Python GUI  ???"
date: 2009-10-25
forum: Programming Talk
---

### Post by baskar007 on 2009-10-25
Which is best for Python GUI  ???

gtk :
gtk looks ok, But it have many troubles

Tkinter:
ugly look, low widgets

Qt4:
looks great,easy coding, everything ok, but my questions is "IS ALL LINUX USERS HAVE INSTALLED QT4??" 


or there is any other things?

share your ideas friends.:popcorn:

---

### Post by bonefry on 2009-10-25
Qt4 if you want to go multi-platform. It doesn't matter how many people have it installed. The Linux distro can pull the required dependencies if you package your application right.

Gtk+ if you'd like your application to "blend in" the Gnome desktop.

Both are easy to use from Python.

---

### Post by baskar007 on 2009-10-25
> **bonefry said:**
> Qt4 if you want to go multi-platform. It doesn't matter how many people have it installed. The Linux distro can pull the required dependencies if you package your application right.

Gtk+ if you'd like your application to "blend in" the Gnome desktop.

Both are easy to use from Python.
thanks, 
i think gtk is best for all.but always i am facing many problem with gtk.

my code struck always when i use gtk+ 
do you know how to solve this?
[http://ubuntuforums.org/showthread.php?t=1300712]("http://ubuntuforums.org/showthread.php?t=1300712")

---

### Post by baskar007 on 2009-10-25
> **bonefry said:**
> Qt4 if you want to go multi-platform. It doesn't matter how many people have it installed. The Linux distro can pull the required dependencies if you package your application right.

Gtk+ if you'd like your application to "blend in" the Gnome desktop.

Both are easy to use from Python.
thanks, 
i think gtk is best for all.but always i am facing many problem with gtk.

my code struck always when i use gtk+ 
do you know how to solve this?
[http://ubuntuforums.org/showthread.php?t=1300712]("http://ubuntuforums.org/showthread.php?t=1300712")

---

### Post by giuspen on 2009-10-25
read the [pygtk faqs]("http://faq.pygtk.org/index.py?req=index") when you have troubles, they almost all the times solve the problems

in this case if you read [this]("http://faq.pygtk.org/index.py?req=show&file=faq20.006.htp") you should understand how to not stuck

---

### Post by vinutux on 2009-10-25
Gtk is most popular..... but both gtk and kde is able to use any desktops...no prob... An alter way make two versions gtk and kde like avidemux...........:P

---

### Post by ibutho on 2009-10-25
> **vinutux said:**
> Gtk is most popular..... but both gtk and kde is able to use any desktops...no prob... An alter way make two versions gtk and kde like avidemux...........:P

This depends on what distro you use and the default DE or WM. Where GNOME and XFCE are popular, then GTK is popular. Where KDE is popular, then qt is popular. Its easy to install both anyway, so a developer should just develop using the tools they wish and the dependencies will be automatically installed by the package manager.

---

### Post by vinutux on 2009-10-25
I used that word coz of most populer distros like ubuntu,fedora,debian,redhat are use gtk/gnome default....

i am also aware of sese/mabdriva use kde/qt .....

---

### Post by ibutho on 2009-10-25
> **vinutux said:**
> I used that word coz of most populer distros like ubuntu,fedora,debian,redhat are use gtk/gnome default....

i am also aware of sese/mabdriva use kde/qt .....

I understand. My point was that although almost every distro has gtk available it does not translate to it being the most popular. The distros you mentioned also have qt by default (its part of the LSB standard like gtk) and sizeable numbers of KDE users.

---

### Post by juancarlospaco on 2009-10-25
***WXWidgets***

---

### Post by matthew.ball on 2009-10-25
^ Yes!

wxPython to be exact :D
[http://www.wxpython.org/](http://www.wxpython.org/)

[http://en.wikipedia.org/wiki/WxPython](http://en.wikipedia.org/wiki/WxPython)

It also has an IDE I believe, not that that is very important in your choice.

---

### Post by Sandsound on 2009-10-26
> **baskar007 said:**
> my code struck always when i use gtk+

I'm also new to Python and have a similar problem with hanging scripts, so I made this little python-app i call : [Reload]("http://www.sandgreen.dk/index.php?side=python_reload")

btw. GTK is (imho) the best place to begin, and theres a lot of documentation out there.

---

### Post by dodle on 2009-10-26
I prefer wxPython.  It is mult-platform and uses Gtk+ style for Gnome desktop.  I would like it even better if it would use the Qt4 style for KDE.

So usually if I want my app to look nice on KDE, I'll make a Qt4 version of it.  Well, actually, I only have one app and I'm not the greatest developer ;).

---

