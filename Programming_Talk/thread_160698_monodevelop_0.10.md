---
title: "monodevelop 0.10"
date: 2006-04-15
forum: Programming Talk
---

### Post by lee_connell on 2006-04-15
I'm using dapper with md 0.10 and am wondering how do you create a form/window?  I see how to bring up the widget/properties views, but how do I create one where I can drag and drop to build a window?

---

### Post by llonesmiz on 2006-04-15
I'm not sure I understand your problem, these are the two scenarios I can think of:

1. You want a program with a single window and what you want to modify is this window->The solution is easy, just create a new gtk project from the menu and then open the file MainWindow.cs in the editor. You'll see some code and below that you will find two buttons: Source code and Designer. Just press designer and you'll be able to construct the window you need.

2. You want an extra window->I haven't "played" too much with the environment but I think what you need to do is right click on "User Interface" in the panel on the left and select "New Dialog" (It doesn't work for me with "New Window", the "obvious" choice).

This link is really interesting, although you have probably watched it already.

[http://pixane.net/static/stetic_25.htm](http://pixane.net/static/stetic_25.htm)

---

### Post by mostwanted on 2006-04-16
Be sure to select the proper CS file in the solution sidebar, MyWindow and not Main. Then you'll see the two buttons.

---

