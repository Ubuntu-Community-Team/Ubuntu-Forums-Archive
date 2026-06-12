---
title: "Glade and Timer Widget"
date: 2006-11-14
forum: Programming Talk
---

### Post by daniloeu on 2006-11-14
Hi Everybody!

Some know if exist some timer widget on Glade...

Like Visual Basic... A widget that execute some action in 5 to 5 seconds.
It exist or I need to make a thread to do that?

Thanks!

Danilo

---

### Post by llonesmiz on 2006-11-14
There isn't a widget like that. You can use this though:

[http://gtk.org/tutorial/c1761.html](http://gtk.org/tutorial/c1761.html)

---

### Post by mailbinoy on 2008-02-10
Hi,

I am also looking for something similar. I am suing pygtk. Once gtk.main() is callled, is it possible to call any function ?
without calling gtk.main() the main window is not displayed. 
As you can see I am a complete novice and basically I am creating an app for myself that needs to change the text in a textbox every 30 seconds. 
Any help would be appreciated.

---

### Post by mailbinoy on 2008-02-19
found it out myself. these two options work well for me
gobject.idle_add
and
gobject.timeout_add

---

