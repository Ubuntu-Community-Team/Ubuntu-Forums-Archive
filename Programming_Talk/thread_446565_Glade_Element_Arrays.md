---
title: "Glade: Element Arrays?"
date: 2007-05-17
forum: Programming Talk
---

### Post by tonyr1988 on 2007-05-17
This is kind of hard for me to explain, so here's an example:

Let's say I've got 10 text fields for my GUI. I want them named as if they were in an array. For example, label(0), label(1), . . ., label(9). If any label is clicked, I want an event passed as clickLabel(int index). 

Make sense? I hate to say this, but I want something similar to what VB6 had (yes, I'm a shameful former user :)). Is this possible with Glade?

I can elaborate and/or clarify if needed.

EDIT: Just found this similar question:

[http://lists.ximian.com/pipermail/glade-users/2000-November/000202.html](http://lists.ximian.com/pipermail/glade-users/2000-November/000202.html)

However, I couldn't find a reply, and it's from late 2000, so it doesn't do me a whole lot of good. I'm not the only one looking, though. :)

EDIT2: I just realized that I could just have different callbacks and tie them into the same function, and put my own parameter in there. It's kind of a hack-together workaround, but it would work. Are there any other ways?

---

### Post by slavik on 2007-05-18
when you create something and you want it to receive an event, you have to register yourself with the event handler.

---

