---
title: "What GUI library should be used for Ubuntu applications?"
date: 2012-12-14
forum: Programming Talk
---

### Post by noname222 on 2012-12-14
We are researching software development for Ubuntu.  One thing I am not sure of is which GUI library we should use to give a consistent look with other Ubuntu applications.  I hope to find something that will work with Scintilla, because part of our product is a code editor with syntax highlighting, but I will go with whatever the official/recommended solution is.

---

### Post by lykwydchykyn on 2012-12-14
They seem to push GTK pretty heavily, but I don't think QT applications are necessarily going to look "bad" if you'd rather use that (I know QT has a scintilla widget).

---

### Post by noname222 on 2012-12-14
Ah, I see it here:
[http://developer.ubuntu.com/get-started/](http://developer.ubuntu.com/get-started/)

Python though, is that a joke?  Sorry Ubuntu, we will be using C++.  :P

---

### Post by memilanuk on 2012-12-14
Not a joke.  Depends on what the app is for... some things 'need' C/C++, some do not.

---

### Post by cariboo on 2012-12-14
This is neither a Testimonial or an Experience, moved to Programming Talk.

---

### Post by llanitedave on 2012-12-14
Seems to me that the KDE applications look better in a GTK+ environment than GTK apps look in a KDE environment.  I don't know if that's to the credit of QT or GTK+.

---

### Post by zombifier25 on 2012-12-16
The difference, if there is any at all, between GTK+ and Qt in terms of looks, speed, etc. is barely noticeable these days. Qt apps in a GTK+ environment uses the GTK+ themes natively and vice versa.

Risk turning this into a flamebate, I recommend Qt. It's easier to work with in terms of functionality, documentations, tools, and portability.

---

### Post by SuperCamel on 2012-12-16
> It's easier to work with in terms of functionality, documentations, tools, and portability.

I've never actually developed with Qt before so I don't know very much about it. But I've been using Gtk for a while and I like it for all the reasons you've recommended Qt for. So without in any turning this into a flamebate, could you substantiate your opinion please?

---

### Post by zombifier25 on 2012-12-16
> **SuperCamel said:**
> I've never actually developed with Qt before so I don't know very much about it. But I've been using Gtk for a while and I like it for all the reasons you've recommended Qt for. So without in any turning this into a flamebate, could you substantiate your opinion please?

Functionality: Qt is more than just a GUI toolkit. It includes a lot of modules. such as QtNetwork, QtOpenGL, ... Also, personally, I find Qt's syntax easier to code in than GTK+'s.

Documentations: There are WAAY more documentation on the net for Qt than GTK+ (gtkmm's documentation is even worse since I code in C++)

Tools: There are lots of useful tools for developing in Qt, such as Qt Creator.

Portability: It's easier to port Qt apps to other platforms, because of the availability of tools available.

Of course, everyone has their own preferences. If you're happy using GTK+, then good for you :P

---

### Post by lykwydchykyn on 2012-12-17
If the OP is coding in C++ and needs a ready-made Scintilla widget, QT sounds like a good fit.  If you code it right, it shouldn't be hard to keep it cross-platform.

---

