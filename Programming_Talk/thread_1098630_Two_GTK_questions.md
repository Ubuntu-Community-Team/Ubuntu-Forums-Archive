---
title: "Two GTK questions"
date: 2009-03-17
forum: Programming Talk
---

### Post by jimi_hendrix on 2009-03-17
1) whats the easiest way to positions something? i am used to the .Net way of setting a coord...

2) how would i get a list like box that is like the one in your music player where you can click a button and it gets organized by artist or album or whatever

---

### Post by simeon87 on 2009-03-17
I tend to organize widgets by nesting horizontal and vertical boxes.

---

### Post by jimi_hendrix on 2009-03-17
well is there a way i can set the widget position by a coord?  also, if i want to put an hbox at the bottom of the window, how do i do it

---

### Post by Vadi on 2009-03-17
> **jimi_hendrix said:**
> well is there a way i can set the widget position by a coord?  also, if i want to put an hbox at the bottom of the window, how do i do it

Yes, but *do not do it*. Positioning by coordinates is a very horrible thing you can do that starts out with unscalable and a pita to modify later interfaces.

It's best to use relative positioning - so use boxes, and alignment values inside them.

Take a read of this: [http://library.gnome.org/devel/gtk-tutorial/stable/c355.html](http://library.gnome.org/devel/gtk-tutorial/stable/c355.html) I found it very rewarding. And too often did I have to redo an interface completely because someone used absolute positioning and as soon as something was changed, it all broke completely.

---

### Post by sujoy on 2009-03-17
1) gtk layout is container based, here you divide the window into horizontal and vertical sections and place stuffs there, kinda like a tiling WM

2) i guess thats done by the TreeView widget. Haven't worked with treeview yet, so can't provide any further info on that.

---

### Post by jimi_hendrix on 2009-03-17
> **sujoy said:**
> 1) gtk layout is container based, here you divide the window into horizontal and vertical sections and place stuffs there, kinda like a tiling WM



nvm figured out my question but i have a new one

i am doing gtk_table_attach_defaults(GTK_TABLE(table), playButton, 1, 2, 1, 2); to a 25x25 table...but its filling the whole screen

---

### Post by Tony Flury on 2009-03-17
Probably because the Table is set to fill and expand, or it maybe that the table needs all the cells filled with somethhing (not sure never used the Table widget).

The GTK friendly way of doing what i think you want is to use box containers to fill your window.

create a Vbox - and then use the Pack_end method to add you button to the the bottom of the Vbox.

as everyone else has said using a combination of container widgets (VBOX and HBOX are the main ones) is by far the best way to control the layout of your controls, and far less likely to break, when you want to add another control to your interface.

for example 
say you fill your 25x25 table - and then you want to add another button in the bottom left corner - how do you do it - to my reckoning - you now need a 26 x 25 table and most if not all of your controls will need to be changed to accomodate the fact that the table is 26 wide - and not 25. I would suggest that a table is only ever useful if you know your controls will only ever be displayed as a table - in my opinion they should not be used as a general layout tool.

On the other hand with HBoxes and Vbox - correctly layed out -  adding a new widget in the bottom left, could be as simple as 2 lines of code - one to create the new widget, and one to pack that widget into an already created HBox or VBOX - and nothing else needs to change, as everything else will automatically resize within the packing boxes to cope the wider on screen size.

---

### Post by Vadi on 2009-03-18
Use Glade for doing all design. Hard-coding your widgets is as bad as hard-coding your value in code these days :)

---

