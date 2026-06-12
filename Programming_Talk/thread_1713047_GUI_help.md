---
title: "GUI help"
date: 2011-03-23
forum: Programming Talk
---

### Post by Gihan Lakmal on 2011-03-23
I want to create GUI for my C based application in Ubuntu. What is the easiest and fastest way to create GUI for C based applications.

---

### Post by andrew1992 on 2011-03-23
> **Gihan Lakmal said:**
> [SIZE=3]I want to create GUI for my C based application in Ubuntu. What is the easiest and fastest way to create GUI for C based applications. [/SIZE]
I would personally go with Glade Interface Designer and GTK+, which is easy to use with C. Here is a very good tutorial: [http://www.micahcarrick.com/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/gtk-glade-tutorial-part-1.html)

---

### Post by nvteighen on 2011-03-23
Just be aware that if you want something like the "KDE look", you won't be able to do it in C because the underlying Qt GUI toolkit used there is for C++.

But, if you are thinking about GNOME or any other "GTK+-oriented" (ugh... I've coined a new term...) Desktop Environment, C will do. And the best would be to use Glade or some visual GUI designer for creating the layout.

---

### Post by Gihan Lakmal on 2011-03-31
Thans for all for your kindly reply .....=D>

---

