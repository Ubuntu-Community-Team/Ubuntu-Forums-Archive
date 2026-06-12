---
title: "Is there a GTK widget that behaves like toolbarmenuitem looks like toolbarbutton?"
date: 2009-10-12
forum: Programming Talk
---

### Post by J V on 2009-10-12
I have a toolbar, and have created numerous toolbarmenuitems, the problem is, I only want one button, and it should be the big one, not the little arrow one below it,

Is there an option somewhere to disable the second button and only use the big one (My example is the forward button on firefox with the little arrow next to it, I want the menu to come out of the main button)

---

### Post by spupy on 2009-10-12
> **J V said:**
> I have a toolbar, and have created numerous toolbarmenuitems, the problem is, I only want one button, and it should be the big one, not the little arrow one below it,

Is there an option somewhere to disable the second button and only use the big one (My example is the forward button on firefox with the little arrow next to it, I want the menu to come out of the main button)

You can use a normal toolbar button instead, and have it display a pop-up menu when clicked.

---

### Post by J V on 2009-10-12
If you are talking about using signals to create the effect... Well lets just say I'm not a fan of that :)

How would I go about doing that? 

If thats not what you mean, then you must me mistaken, cause other than menu I can't let any one of them have a menu (just doesn't work)

---

### Post by spupy on 2009-10-12
> **J V said:**
> If you are talking about using signals to create the effect... Well lets just say I'm not a fan of that :)

How would I go about doing that? 

If thats not what you mean, then you must me mistaken, cause other than menu I can't let any one of them have a menu (just doesn't work)

Yes, I'm talking about signals - the callback of the normal toolbar button containing the code the pops-up the menu.

---

### Post by J V on 2009-10-12
Happen to know what that code is? Cause its probably miles long involving show(), positioning, focussing... it could also be a single command, but I don't know what it is...

---

### Post by spupy on 2009-10-12
> **J V said:**
> Happen to know what that code is? Cause its probably miles long involving show(), positioning, focussing... it could also be a single command, but I don't know what it is...

I don't have it in C, but in Python with pygtk it is really simple - i guess in C it won't be different. Actually, there is nothing special about this menu. You create a normal menu, add menu items to it, call it's show_all() (or whatever it is called in C). The important part is this method:
[http://library.gnome.org/devel/gtk/2.18/GtkMenu.html#gtk-menu-popup](http://library.gnome.org/devel/gtk/2.18/GtkMenu.html#gtk-menu-popup)
It has 6 arguments (one of which is user data) which aren't very important - in python I have them as either None (null) or 0 (zero).
The menu appears under the mouse.

---

### Post by J V on 2009-10-13
Ok, thanks!

The menus tend to open at a fixed spot on the button though... any way to replicate that?

(Perhaps gtk_menu_shell/gtk_menu_item?)

---

### Post by spupy on 2009-10-13
> **J V said:**
> Ok, thanks!

The menus tend to open at a fixed spot on the button though... any way to replicate that?

(Perhaps gtk_menu_shell/gtk_menu_item?)

I'm not sure I understand you. Do you mean that the menu doesn't place itself on top of the button, as a normal menu does? One of the arguments of the popup function is called "GtkMenuPositionFunc func". I guess this would be the proper way to position the menu, but it looks like it can get messy.

---

### Post by J V on 2009-10-13
well what I mean is, click at one side of the button and the menu will popup there, click on the other side, and it will popup there...

I would prefer the menu to popup from a defined place so it doesn't jump around... I think there are arguments somewhere to that effect...

Edit: ahh yes, func indeed...

whats the default function that goes there?

---

### Post by spupy on 2009-10-13
> **J V said:**
> well what I mean is, click at one side of the button and the menu will popup there, click on the other side, and it will popup there...

I would prefer the menu to popup from a defined place so it doesn't jump around... I think there are arguments somewhere to that effect...

Edit: ahh yes, func indeed...

whats the default function that goes there?

Sorry, I have no idea how this function works. Have a look here:
[http://library.gnome.org/devel/gtk/2.18/GtkMenu.html#GtkMenuPositionFunc](http://library.gnome.org/devel/gtk/2.18/GtkMenu.html#GtkMenuPositionFunc)
This is the positioning function you can pass to the popup menu.

---

### Post by J V on 2009-10-13
Ahh yes, thats way too complicated lol...

If it automtically chose to go from the widget in var 2 it would be nice, but the amount of work to fix it if not isn't worth it, I will test it later...

[SOLVED]

---

