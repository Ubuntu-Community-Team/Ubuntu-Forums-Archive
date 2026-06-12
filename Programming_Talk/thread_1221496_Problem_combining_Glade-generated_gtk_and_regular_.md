---
title: "Problem combining Glade-generated gtk and regular gtk"
date: 2009-07-23
forum: Programming Talk
---

### Post by M4rotku on 2009-07-23
Hello all,

I am currently writing a program in which the GUI has to change based on the number that the user selects.  The point of the app is to rip a given number of video tracks from a dvd.  After the user selects the number of tracks, using a GtkSpinButton, I need to make a two column chart appear prompting the user to enter the titles for the tracks looking vaguely like this:

> Title for track 1:    <field to input title>
Title for track 2:    <field to input title>
and so on.

I have the GUI all ready except for this part.  I tried using devhelp to get the gtkcommands, and it was a great help, but it's written for C++ and I think I'm missing something.  I have a horizontal box which already has the first prompt in it (assuming that people want to rip at least 1 track) when I made the GUI in Glade.  I need to use the gtk commands from scratch then to add another box to this horizontal box group for each track, split each one of those into two verticle boxes, and put a prompt and an input field into the verticle boxes.  I realize that what I just said is probably really confusing, but it's the best way I can think of to explain.  The code that I've tried in GTK so far to generate a horizontal row containing a title is as follows:

> self.wTree.get_widget("title_holder").pack_end(gtk_hbox_new(True,0),True,True,0)
self.wTree.get_widget("title_holder").gtk_hbox.pack_end(gtk_label_new("Title of Track 2:"))

Is there something that I am missing because when I run the application, nothing has changed?  I am including both the .py and the .glade files if anyone has time to look at them and give me advice.  I realize that this is probably a complicated question and I very much appreciate all answers.

Much thanks,
M4rotku

---

### Post by monraaf on 2009-07-23
You can find the Python GTK+ documentation here:

[http://www.pygtk.org/docs/pygtk/index.html](http://www.pygtk.org/docs/pygtk/index.html)

Personally I would probably use a treeView in a scrolled window for this or if the number of tracks is always a small nr a table maybe.

---

### Post by M4rotku on 2009-07-24
I've looked in that documentation, that's how I got so far in the first place.  I posted more in hopes that someone might point out the error in my code or what I'm doing wrong.  Thanks for the link though, I'll remember that for future stuff.

---

### Post by M4rotku on 2009-07-25
I forgot to include the files.  I had to turn the glade file into an archive in order to upload it.

---

### Post by M4rotku on 2009-07-26
bump

---

