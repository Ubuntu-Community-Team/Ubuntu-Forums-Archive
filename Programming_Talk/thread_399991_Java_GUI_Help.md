---
title: "Java GUI Help"
date: 2007-04-03
forum: Programming Talk
---

### Post by Griff on 2007-04-03
I've never really done much with GUIs in general and I'm especially rusty in java.  I've searched through the java docs site, but it left me a little confused with references to 'java web start' and other things.  If I have a just an empty frame up, how do I add a bar at the top (like the one at the top of this browser that has pull down menus) and use a selection to bring up a save dialog box.  I'm pretty sure there is an easy way to do this, but I've been struggling for a while now and would greatly appreciate some help.

Thanks,
Griff

---

### Post by amohanty on 2007-04-03
you have to add a JMenuBar and populate it with menu items.
[http://java.sun.com/docs/books/tutorial/uiswing/components/menu.html](http://java.sun.com/docs/books/tutorial/uiswing/components/menu.html)

HTH
AM

---

### Post by Griff on 2007-04-03
Thank you! That helped a lot.  Now I just need to figure out how to bring up a file browser to select a save location.

---

### Post by amohanty on 2007-04-03
[http://java.sun.com/javase/6/docs/api/javax/swing/JFileChooser.html](http://java.sun.com/javase/6/docs/api/javax/swing/JFileChooser.html)

I would suggest browsing a swing book at the local bookstore and bookmarking the api docs :)

HTH
AM

---

### Post by laxmanb on 2007-04-03
you want to add a menu bar and a Save dialog?

Sun Java Tutorials*(JFileChooser):
[http://java.sun.com/docs/books/tutorial/uiswing/components/filechooser.html](http://java.sun.com/docs/books/tutorial/uiswing/components/filechooser.html)

---

