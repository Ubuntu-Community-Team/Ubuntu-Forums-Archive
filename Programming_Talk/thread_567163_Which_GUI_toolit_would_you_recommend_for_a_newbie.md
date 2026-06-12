---
title: "Which GUI toolit would you recommend for a newbie?"
date: 2007-10-04
forum: Programming Talk
---

### Post by p.i.m.p on 2007-10-04
I'm new to programming and would like to develop simple gui applications in c++.. which toolkit would you guys recommend? which is the simpler to use and has the least learning curve?

---

### Post by LaRoza on 2007-10-04
I would start with Python for GUI programming. For Python, EasyGUI is the easiest, also wxPython (port of wxWidgets), and Tkinter (Tk). The Python ports are similar to the C++ API so that you can use the knowledge of them. I do not do much GUI programming, but wxPython is quite easy, but powerful. EasyGUI is a simple way of using a gui for an app, but is limited.


wxWidgets, then.

---

### Post by p.i.m.p on 2007-10-04
Hi,

I'm learning Java and C++ so I have my hands full currently.. Python sounds interesting - I'll give it a shot during Winter break.. Is there any way I can draw a "gui" with wxwidgets like in Visual Studio?

---

### Post by yage on 2007-10-04
> **p.i.m.p said:**
> Hi,

I'm learning Java and C++ so I have my hands full currently.. Python sounds interesting - I'll give it a shot during Winter break.. Is there any way I can draw a "gui" with wxwidgets like in Visual Studio?

Don't know about wxwighets but GTK has GLADE for that job...

---

### Post by ryno519 on 2007-10-04
I prefer gtkmm. Makes very good use of standard C++ libraries and coding styles and you can use glade to create the guis if you like. It's all nice and easy.

---

### Post by p.i.m.p on 2007-10-04
Thank you for your replies

---

### Post by Acglaphotis on 2007-10-04
I would recommend Glade + python + gladex.

ps: Cool username.

---

### Post by p.i.m.p on 2007-10-04
hahahaha thanks

---

### Post by Blue Sky on 2007-10-04
I recommend QT if you're going to be doing C++, GTK for C#.

Glade is awful, stay away from it.

---

### Post by Acglaphotis on 2007-10-04
> **Blue Sky said:**
> I recommend QT if you're going to be doing C++, GTK for C#.

Glade is awful, stay away from it.

Elaborate, please? I've been using Glade lately and i don't see anything worth labeling as 'awful'

---

### Post by Wybiral on 2007-10-04
PyGTK is pretty simple. GTK with C is pretty easy too, I just can't stand the glib OOP style. I've tried wx and Tk (in Python) as well but I don't think they're that much easier than GTK.

---

### Post by Fbot1 on 2007-10-04
Qt, theres a lot more stuff for it.

---

### Post by pmasiar on 2007-10-05
> **Blue Sky said:**
> Glade is awful, stay away from it.

To OP: if you see "opinions" like this, without any hint of "why", stay away from the opinion :-)

---

### Post by p.i.m.p on 2007-10-05
haha Just one more thing, is code written for gtk cross platform? gtk is available for windows too right?

---

### Post by ryno519 on 2007-10-05
> **p.i.m.p said:**
> haha Just one more thing, is code written for gtk cross platform? gtk is available for windows too right?

Yes, if the Windows user has the Gtk+ Runtime Environment installed.

---

