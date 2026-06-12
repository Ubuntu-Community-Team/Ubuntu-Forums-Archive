---
title: "GUI in C"
date: 2013-08-22
forum: Programming Talk
---

### Post by MOBASIR on 2013-08-22
How i will create GUI in c language with ubuntu.

---

### Post by sffvba[e0rt on 2013-08-22
*Thread moved to **Programming Talk**.*


404

---

### Post by ofnuts on 2013-08-22
You use a GUI library such as [GTK+]("http://www.gtk.org/"). But honestly, if you ask this kind of very generic question, I doubt your current programming knowledge and Google skills are sufficient to the task...

---

### Post by nvteighen on 2013-08-23
Although you should take a look at what Google tells you about this topic, in summary, writing a GUI in C (or any other language) is done by using libraries dedicated to this task. There are a couple of them which are  very widespread, e.g. Qt (C++, though) and Gtk. Search for the official Gtk or Qt tutorials to have a glimpse on how GUI code looks like and what kind of things are required to know in order to step into this kind of programming (really good understanding of the language, for instance). Some people use RAD tools like Glade or Qt Designer that allow you to create your GUI visually, and then have your code interpret it (you still have to code the behavior of each widget, though), but IMO it's better to start learning to write them by hand.

---

