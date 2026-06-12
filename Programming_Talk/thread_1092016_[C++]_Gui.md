---
title: "[C++] Gui"
date: 2009-03-09
forum: Programming Talk
---

### Post by detorresrc on 2009-03-09
Hi i want to create gui in c++ with form,textbox,button , etc.. Wat libraries i need to use?

Tnx

---

### Post by digital_x on 2009-03-09
That really depends.  There are a number of toolkits you can use for creating a gui.  Some examples are GTK+ (which is written in C but has a C++ binding called gtkmm), QT, wxWidgets and more.  Each of the ones I mentioned also have RAD gui builders as well for speady development.  Its really going to be a choice of preference.  You will just have to try out the viable options and see which you like.  I personally like GTK (and no I am not advocating, just stating my preference) because of its compatibility and bindings with a vast number of languages.  There is no defacto standard though, so its up to you to decide which you want to use.

---

### Post by detorresrc on 2009-03-10
tnx for your reply, can u give me a link were can i download that libraries. Tnx so much.

---

### Post by Sinkingships7 on 2009-03-10
You'll want to take into consideration the platform you're developing the application for. Qt feels more "at home" on a Windows system than GTK. But GTK, of course, feels just right for Ubuntu and other Gnome based Linux distros. 

Qt's native binding is for C++, and I've heard great things about it. In fact, I plan on exploring it myself sometime in the near future. So if you want to go the "natural" way, then this may be right for you.

---

### Post by cabalas on 2009-03-10
> **detorresrc said:**
> tnx for your reply, can u give me a link were can i download that libraries. Tnx so much.

Most of the libraries can be found in apt

---

### Post by nvteighen on 2009-03-10
To download, get the *-dev packages from apt. Also the *-doc packages to have the documentation when you're offline. This is true for **any** library you want to use for development :) (except ncurses, which for some weird reason, doesn't have a -doc package but includes the docs in its -dev package...)

---

### Post by Tibuda on 2009-03-10
> **Sinkingships7 said:**
> You'll want to take into consideration the platform you're developing the application for. **Qt feels more "at home" on a Windows system than GTK**. But GTK, of course, feels just right for Ubuntu and other Gnome based Linux distros.Untrue. GTK+ feels "at home" in Windows too. Just look at Deluge and Pidgin. They are both GTK+ and looks good in both OSs.

---

### Post by krazyd on 2009-03-10
> **danielrmt said:**
> Untrue. GTK+ feels "at home" in Windows too. Just look at Deluge and Pidgin. They are both GTK+ and looks good in both OSs.
Not in KDE though ;)

---

### Post by Zdravko on 2009-03-10
I use FLTK.

---

### Post by abhilashm86 on 2009-03-10
you can start off with qt 4.5, it supports linux,
[qt 4.5]("http://www.qtsoftware.com/")

you actually find qt creator which has great things like code completion, integration with OPENGL and many others, you can download at their site( if you want qt 4.5 latest).
[http://www.qtsoftware.com/products](http://www.qtsoftware.com/products) , check here for more info.........

---

### Post by Simian Man on 2009-03-10
> **detorresrc said:**
> tnx for your reply, can u give me a link were can i download that libraries. Tnx so much.

If you intend to do anything serious with programming, I'd like to introduce you to my good friend Google.  Google, detorresrc; detorresrc, Google.  Now that that's out of the way you will get better results asking about programming if you do research ahead of time and then ask specific questions later.  Proper English doesn't hurt either.

---

