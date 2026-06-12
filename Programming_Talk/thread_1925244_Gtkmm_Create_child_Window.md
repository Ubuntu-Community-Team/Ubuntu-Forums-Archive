---
title: "Gtkmm: Create child Window ?"
date: 2012-02-14
forum: Programming Talk
---

### Post by fallenshadow on 2012-02-14
Does anyone know how to create a child window? (Window inside the main window that maximizes inside the boundaries of the main window)

Like this:
[IMG]http://i43.tinypic.com/5frxtu.png[/IMG]

I know how to create a window but I don't want a normal window.

---

### Post by fallenshadow on 2012-02-15
Anyone know at all? o.O

---

### Post by pbrane on 2012-02-15
I don't think MDI/WiW is implemented in Gtk. You would have to do that coding yourself. An alternative is to use a notebook container, like in gedit. 

Have you tried making a window as a child of the main window to see what happens?

---

### Post by fallenshadow on 2012-02-15
Im not sure how to set a window as a child of a parent window... is it something to do with this?

> 
void Gtk::Window::set_transient_for (Window&  parent)


---

### Post by fallenshadow on 2012-02-15
Alright I had a proper attempt at it:

> newfile.cc:117:21: error: ‘add_window’ was not declared in this scope

This is the line of code it has trouble with:

[PHP]add_window(*window);[/PHP]

However it is from example code so I don't know how its wrong...

---

### Post by Cookieh on 2012-02-15
Try having a look at python as it is way more simple than PHP and it also can control the window size to full screen, hidden menu bars and controls. Just try to look at it, but not sure if it would be good in this concept..

---

### Post by pbrane on 2012-02-15
The add_window function is a custom function that you have to implement, it's not a Gtkmm function.

---

### Post by fallenshadow on 2012-02-15
Oh right... I will do some more investigating then.

@Cookieh By the way it is C++ im using not PHP. :)

---

### Post by fallenshadow on 2012-04-08
Question open to all here:

Which is better in your honest opinion for an image editor, Window in Window or Tabs? (per image)

Your answers will determine the direction I take. :)

---

### Post by fallenshadow on 2012-04-09
Decided on tabs since its built into GTK. :D

---

