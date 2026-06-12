---
title: "How to create a custom text editor-like widget? pygtk"
date: 2008-05-06
forum: Programming Talk
---

### Post by ::: on 2008-05-06
I want to implement a custom Gtk-Widget (using python/pyGtk). Basically, It's supposed to be an editor for bulleted list (it shouldn't be possible to enter anything that is not a list item). It should also allow indention / unindention of Items and be keyboard controllable (e.g. Ctrl+left indents current item).

While I found some tutorials and samples on how to implement custom widgets in pyGtk I am kinda lost when it comes to implementing a text editor:

How do I represent selection?
How do I enable Copy&Paste / Drag&Drop?
How do I enable Spell-Checking?
How do I draw the cursor?
How do I make the widget use standard Fonts for text / color for selection?
How do I implement undo/redo?
How do I implement typing text into the widget?

Another thing that bugs me is how to represent the data internally. Currently I consider to represent the list as a tree (with each list item beeing a node and indented items beeing child nodes of the nearest un-indented node before them). This is mainly due to some fancy things I want to do to the List afterwards (like generating a document template out of it where each list items becomes a headline). However, how do I represent the text inside a List Item? I figured a simple string will probably not be sufficient, since it won't be able to represent selections and such stuff well.

Has anyone here done something similar and can give me some advice?
Or can someone provide me a link to an existing implementation where I can borrow some ideas?

---

### Post by Can+~ on 2008-05-06
Why not GTK Tree View object?

Gtk Tree view:
-supports drag & drop of cells.
-supports text editing inside it's cells, checkboxes, radiobuttons, any widget in fact.
-Sorting
-Cursor

Besides, gtk also supports the Font selector, and color selector.

Before jumping into pygtk, learn how to use glade, it will cut a lot of work, glade3.

---

### Post by Tony Flury on 2009-06-13
In terms of representing the text, you need to look at the concept called ropes, which a Data structure concept which is very good at representing strings.

Essentially it is a binary tree represented, which can gets fragmented as the user selects, cuts, formats etc.

---

### Post by Can+~ on 2009-06-13
> **Tony Flury said:**
> In terms of representing the text, you need to look at the concept called ropes, which a Data structure concept which is very good at representing strings.

Essentially it is a binary tree represented, which can gets fragmented as the user selects, cuts, formats etc.

Old post is old.

---

