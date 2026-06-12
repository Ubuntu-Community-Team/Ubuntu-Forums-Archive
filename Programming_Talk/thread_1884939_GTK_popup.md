---
title: "GTK popup"
date: 2011-11-22
forum: Programming Talk
---

### Post by dargaud on 2011-11-22
Hello all,
a very basic question. I have to do some support on an oldish C++ program that uses GTK (which I've never used before). In particular I need to add some modal popup windows. On my usual environment I simply do MessagePopup("Title", "Message") and it appears until the user clicks the only button available ("OK").

How do I do that in GTK ? I found [this page]("http://developer.gnome.org/gtk3/stable/GtkDialog.html") which seems overly complicated... Do I really need external XML resources for such a simple task ?!?
Thanks.

---

### Post by PaulM1985 on 2011-11-22
Is this what you are after?

[http://www.gtk.org/api/2.6/gtk/GtkMessageDialog.html](http://www.gtk.org/api/2.6/gtk/GtkMessageDialog.html)

Paul

---

### Post by dargaud on 2011-11-22
Yes, thank you. Just what is this "main_application_window" parameter ? Can it default safely to NULL ?

---

### Post by Liiiim on 2011-11-22
It would be the main window of your program.  You can call it with NULL with no problems though.

---

### Post by crdlb on 2011-11-22
That link is pretty old; the current reference for gtk2 is: [http://developer.gnome.org/gtk/stable/GtkMessageDialog.html](http://developer.gnome.org/gtk/stable/GtkMessageDialog.html)

---

### Post by nvteighen on 2011-11-23
> **dargaud said:**
> Hello all,
a very basic question. I have to do some support on an oldish C++ program that uses GTK (which I've never used before). In particular I need to add some modal popup windows. On my usual environment I simply do MessagePopup("Title", "Message") and it appears until the user clicks the only button available ("OK").

How do I do that in GTK ? I found [this page]("http://developer.gnome.org/gtk3/stable/GtkDialog.html") which seems overly complicated... Do I really need external XML resources for such a simple task ?!?
Thanks.

Read the page more carefully... (example 44, e.g.). There you'll see that you don't need an XML GtkBuilder definition.

However, in time you'll see that using GtkBuilder is way more practical than doing these things by hand.

---

