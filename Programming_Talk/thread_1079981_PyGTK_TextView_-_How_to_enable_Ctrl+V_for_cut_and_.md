---
title: "PyGTK TextView - How to enable Ctrl+V for cut and paste?"
date: 2009-02-24
forum: Programming Talk
---

### Post by aidave on 2009-02-24
Hi, I am currently developing an open source program called "Kabikaboo" to help assist in novel writing.  I am learning Python, GTK, etc, while doing so.  Kabikaboo is very functional, but one thing is stumping me:  

I do not know how to enable Ctrl+V, Ctrl+C, and other shortcuts inside of a TextView.

When I print the keys from a callback, it shows the user hitting the V key, and the Ctrl key, but no values for Ctrl+V when pressed together, nor Ctrl+AnyKey.

The funny thing is, the popup menu for the TextView has working cut-n-paste.  It is only the keyboard shortcuts that don't work.  I need those to work for it to be user-friendly.

Can anyone help, please?

thanks,
Dave

Code is available here:
[https://sourceforge.net/projects/kabikaboo/](https://sourceforge.net/projects/kabikaboo/)

---

### Post by kknd on 2009-02-25
Why don't you create an accel for Ctrl + C and Ctrl + V? You don't need to manually capture the typing events.

---

### Post by aidave on 2009-02-25
> **kknd said:**
> Why don't you create an accel for Ctrl + C and Ctrl + V? You don't need to manually capture the typing events.

I hadnt heard of those before, thanks.

Can you give more details on how they would solve the problem?

---

### Post by aidave on 2009-02-25
[http://www.google.ca/search?hl=en&q=textview+accel](http://www.google.ca/search?hl=en&q=textview+accel)

[http://www.nabble.com/gtk_accel_groups_activate-()-td21114267.html](http://www.nabble.com/gtk_accel_groups_activate-()-td21114267.html)

I found this while searching the net... I have no idea if this is the solution, what to do with accels, or if PyGTK is buggy.

Any help or a link to example programs that having working Ctrl+V/etc would be greatly appreciated!

---

### Post by aidave on 2009-02-26
Thanks to Juhaz and mariano on #pygtk IRC, a solution was found.

The GLADE interface designer generates overrides on its default File Menu.  The Edit submenu has Copy/Paste/Cut items.  Deleting those (or linking to them) solves the problem!  :)

---

