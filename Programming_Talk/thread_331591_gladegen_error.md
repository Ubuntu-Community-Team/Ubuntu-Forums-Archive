---
title: "gladegen error"
date: 2007-01-04
forum: Programming Talk
---

### Post by dfm21 on 2007-01-04
Hi!

After having walked through the first steps of the [PyGTK Tutorial]("http://www.pygtk.org/pygtk2tutorial/") I discovered [Glade]("http://glade.gnome.org/") and [GladeGen]("http://www.linuxjournal.com/article/7421").
Building a GUI with these tools should be rather easy, but I keep getting error messages from Gladegen...

To avoid misunderstandings where possible, I will list what I do:

1. Use **glade-2** to create xml file[INDENT]1.0 open glade-2 ;)
1.1 add "Window"
1.2 add a "Button" (button1)
1.3 add a Signal to button1 (on_button1_clicked)
1.4 save project as ~/Projects/project1 (everything else left at defaults)
1.5 quit glade-2
[/INDENT]
I'm now having two files (**project1.glade** and **project1.gladep**) in **~/Projects/project1/** which is my current working directory.
	
2. Use **gladegen** to create skeleton files
[INDENT]2.0 gladegen files are stored in **~/gladegen/**
2.1 calling **~/gladegen/GladeGen.py project1.glade Project1 Project1** [/INDENT]brings following error message:
```

Traceback (most recent call last):
  File "/home/dfm/gladegen/GladeGen.py", line 381, in ?
    main(sys.argv)
  File "/home/dfm/gladegen/GladeGen.py", line 367, in main
    pg.get_members()
  File "/home/dfm/gladegen/GladeGen.py", line 105, in get_members
    self.module = __import__(self.module)
ImportError: No module named Project1

```

Did I overlook something? The example in the tutorial at linuxjournal does not mention anything else...
Please help me with that!

Thanks

---

### Post by duff on 2007-01-04
before you spend to much time on this, what's wrong with libglade?

---

### Post by dfm21 on 2007-01-05
As far as I know, libglade works fine. I ran through [this tutorial]("http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/") and it worked...

---

### Post by DoctorLard on 2007-01-15
Works for me, but I am using **glade-3** which is a rewrite.

GladeGen is for generating the python stub code which still uses libglade to do the actual rendering (rather than generating the Gtk+ rendering code as glade-2 does for C and C++). The .gladep file is just the Glade project file which you can ignore, the .glade file contains all the XML for your UI. For the GladeGen parameters modulename and classname, they can be anything you like.

So, I don't know why it is failing for you, except to check that you got GladeGen from _[the LJ article link]("ftp://ftp.ssc.com/pub/lj/listings/issue123/7421.tgz")_ and that you try using glade-3:

```
sudo apt-get install glade-gnome-3
```

---

### Post by jasonakay on 2007-05-13
I had a similar error when using Glade-3 and found that moving the GladeGen files into the same directory as the XML (*.glade) file fixed it.

---

