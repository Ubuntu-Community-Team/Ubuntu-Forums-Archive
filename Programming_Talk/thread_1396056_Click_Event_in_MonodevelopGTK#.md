---
title: "Click Event in Monodevelop/GTK#"
date: 2010-02-01
forum: Programming Talk
---

### Post by joshb86 on 2010-02-01
Hey Guys,

This is a complete noob question but I've not found an answer anywhere yet so I figured I'd post here. 


I've decided to play with monodevelop IDE and learn a little C#. All I need to know is how the heck do I capture a click event from a button on my gui?

---

### Post by argor on 2010-02-03
one image speaks many words

---

### Post by joshb86 on 2010-02-03
> **argor said:**
> one image speaks many words


Wow... how handy, a signal tab! Can't believe I didn't notice that, thanks man!

---

### Post by loe on 2010-03-06
> **joshb86 said:**
> Wow... how handy, a signal tab! Can't believe I didn't notice that, thanks man!


You are not alone, I am glad I found this thread using google - monodevelop is quite different to use than visual studio....

---

### Post by cszikszoy on 2010-03-06
All the signal tab does is create the method for you in the code view.  You can also just add the .Clicked handler yourself, like this:

Gtk.Button a = new Gtk.Button ();
a.Clicked += delegate {
// do something when the button was clicked...
};

---

