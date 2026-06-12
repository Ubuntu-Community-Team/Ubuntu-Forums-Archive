---
title: "(C) GTK+ layout problems"
date: 2009-06-24
forum: Programming Talk
---

### Post by psld on 2009-06-24
Hi!
I've sat all afternoon trying to puzzle my GTK layout right, but it's a bit hard since this is my first time with GTK. I am using C and I wonder if you guys could help me with this layout problem. Which containers shall I use and how etc..

This is what I want:

[IMG]http://gunnesgard.se/per/skiss.png[/IMG]

---

### Post by Can+~ on 2009-06-24
As a general rule of thumb:

Build the functionality first, then create a GUI around it. Try to make the functional part modular, so when you have to plugin both it's just a matter of pressing a button and it will call a some_function(x,y,z) that will handle everything.

As far as your layout goes, why don't you try installing Glade3?

The bottom part seems like a StatusBar, the readable text is a text view within a scrolled window, etc.

Uploaded a Glade3 file (inside .tar.gz because Ubuntuforums doesn't like .xml or .glade)

---

### Post by simeon87 on 2009-06-24
I'd say the elements should be nested like this:

```
VBox
- Menubar
- HBox
-- VBox
--- DrawingArea (or something, for SDL)
--- TextView
--- TextEntry
-- VBox
--- Toolbar/menu
--- Toolbar
--- Toolbar
--- Scroll list
```

---

