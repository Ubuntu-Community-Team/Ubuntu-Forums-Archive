---
title: "Good Glade + Python tutorial"
date: 2009-07-04
forum: Programming Talk
---

### Post by M4rotku on 2009-07-04
Hey guys,

I tried following [<this>]("http://www.linuxjournal.com/article/6586") tutorial to create a GUI with Glade to be manipulated by Python.  I have no prior experience with GUI programming, a decent amount of experience with Python, and if it helps I know a bit of C++.  I followed the tutorial and thought that everything was great until I received the following error upon launching my new program:

> :~/Programs/Glade/Server Info$ ./serverinfo.py

(serverinfo.py:22718): libglade-CRITICAL **: glade_xml_build_interface: assertion `wid != NULL' failed


I have no idea what this means.  I went back to the tutorial and realized that it is a few years old (2003).  Does anyone know of a good glade tutorial that is up-to-date and easier to understand.

If it helps, my long-term goals with GUI programming is to create a Battleship game.  I have previously coded a less-sophisticated one in C++ which stayed in the realm of the cl.  I want to have a GUI that has a menu, the game, and a prompt area at the bottom that can display messages about missing or hits and such.

In case it will help, I will attach the files that I created following the tutorial.

---

### Post by days_of_ruin on 2009-07-04
[http://live.gnome.org/Glade]("http://live.gnome.org/Glade")

I would recommend the second one from the top (in the "Links" section).

---

### Post by matmatmat on 2009-07-05
[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")

---

### Post by bruce2000 on 2009-07-05
[http://pygtk.org/articles.html]("http://pygtk.org/articles.html")

---

### Post by M4rotku on 2009-07-05
Lol, you all linked to the same article, just via different addresses.  I'm guessing it's good then.  I'll give it a read.

Thanks,
M4rotkuthat's why I L0v3 LinuX and choosed Ubuntu as my fav Distro

---

### Post by M4rotku on 2009-07-06
Okay.  That was a brilliant tutorial, absolutely brilliant.  However, it left off at part 3 and didn't include the part 4 to which he referred.  Is part 4 important or would it just contain more statements like the:

> self.window = builder.get_object("window")

I think if it just contained statements like this, then maybe I could manage.  However, I still feel as though part 4 might be important.

Can anyone point me to a part 4 or an equivalent tutorial or should I be ready to start with my GUI after this?

Much thanks,
M4rotku

---

### Post by M4rotku on 2009-07-06
Okay, i think I know what was missing that is confusing me.  We didn't use any of the handlers such as 'on_about_menu_item_activate'.  So none of the menu items do anything.

---

### Post by M4rotku on 2009-07-07
bumpity bump

---

### Post by M4rotku on 2009-07-08
bump.  looking through the devhelp and still insanely confused.

---

### Post by Can+~ on 2009-07-08
What's the question?

---

### Post by M4rotku on 2009-07-08
I need to know how to make the rest of the options in the tutorial work.  The tutorial covered how to create a text editor and it had the options in the menu to save and copy and paste and stuff like that and then he never covered how to program those functions.  He mentioned that there would be another part to the tutorial which I assume would cover these, but that was a year ago and there hasn't been another part released.  I guess my question is how, with the setup described in the tutorial, do I program the copy, paste, cut, and save functions?

---

### Post by Can+~ on 2009-07-08
In glade you define the events that occur, and name them. For example, add to a button, on click the event "dosomething"

Later, on python you write
[PHP]
def __init__(self):
    #...
    signals = {"on_window_destroy" : gtk.main_quit, "dosomething" : self.afunction }

    builder.connect_signals(signals)

    #...

def afunction(self, widget, data=None):
    pass
    #do stuff here

[/PHP]

For copy and paste, add an event that gets the current selection on your [textbuffer]("http://www.pygtk.org/docs/pygtk/class-gtktextbuffer.html") and take it/replace with the content of the [Clipboard]("http://www.pygtk.org/docs/pygtk/class-gtkclipboard.html").

As for saving, moving the whole content of the textbuffer to a file using the save dialog?

You already should know about events and how to retrieve objects from the .glade file, it's about looking onto [their properties]("http://www.pygtk.org/docs/pygtk/"). Or follow [another tutorial]("http://www.pygtk.org/pygtk2tutorial/index.html"), and skipping the things you already now.

---

### Post by unutbu on 2009-07-08
The rest of Micah Carrick's Glade tutorial is here:

[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)
[http://www.micahcarrick.com/12-27-2007/gtk-glade-tutorial-part-2.html](http://www.micahcarrick.com/12-27-2007/gtk-glade-tutorial-part-2.html)
[http://www.micahcarrick.com/01-01-2008/gtk-glade-tutorial-part-3.html](http://www.micahcarrick.com/01-01-2008/gtk-glade-tutorial-part-3.html)

To run the editor:
```

wget http://www.micahcarrick.com/files/gtk-glade-tutorial/tutorial.xml
wget http://www.micahcarrick.com/files/gtk-glade-tutorial/PyGTK/tutorial.py

python ./tutorial.py
```

---

