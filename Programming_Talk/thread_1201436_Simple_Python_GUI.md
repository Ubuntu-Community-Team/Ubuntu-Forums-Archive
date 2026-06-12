---
title: "Simple Python GUI"
date: 2009-07-01
forum: Programming Talk
---

### Post by Levo on 2009-07-01
I want to make a very simple Python GTK GUI Application. I need only one window, with three buttons (Yes, No, Cancel). And an about dialog (if possible). I don't know much about python. I hope you can help me!

---

### Post by mhh91 on 2009-07-01
look for an IDE that supports PyGTK

---

### Post by Nevon on 2009-07-01
For something that simple, couldn't you use Zenity? I haven't tried it with Python, but I don't see why it wouldn't work.

---

### Post by Levo on 2009-07-01
> **Nevon said:**
> For something that simple, couldn't you use Zenity? I haven't tried it with Python, but I don't see why it wouldn't work.

Yes I've already tried zenity. But there is no YES/NO/Cancel dialog.

---

### Post by Levo on 2009-07-01
> **mhh91 said:**
> look for an IDE that supports PyGTK

Can you suggest me one? Or maybe can you help me how to make a basic window?

---

### Post by monraaf on 2009-07-01
Here you go:

[PHP]
#!/usr/bin/env python
import gtk

dialog = gtk.Dialog("Are you sure?", None, 0,
                    (gtk.STOCK_CANCEL, gtk.RESPONSE_CANCEL,
                     gtk.STOCK_NO, gtk.RESPONSE_NO,
                     gtk.STOCK_YES, gtk.RESPONSE_YES))

response = dialog.run()

dialog.destroy()
while gtk.events_pending():
    gtk.main_iteration(False)

if response == gtk.RESPONSE_YES:
    print 'yes'
elif response == gtk.RESPONSE_NO:
    print 'no'
[/PHP]

---

### Post by Levo on 2009-07-01
> **monraaf said:**
> Here you go:

[PHP]
#!/usr/bin/env python
import gtk

dialog = gtk.Dialog("Are you sure?", None, 0,
                    (gtk.STOCK_CANCEL, gtk.RESPONSE_CANCEL,
                     gtk.STOCK_NO, gtk.RESPONSE_NO,
                     gtk.STOCK_YES, gtk.RESPONSE_YES))

response = dialog.run()

dialog.destroy()
while gtk.events_pending():
    gtk.main_iteration(False)

if response == gtk.RESPONSE_YES:
    print 'yes'
elif response == gtk.RESPONSE_NO:
    print 'no'
[/PHP]

Thank you very much for this!
Now two more questions about your nice script: How can I add a text? And how can I change buttons' names?

---

### Post by monraaf on 2009-07-01
Well, I'm not going to do all your work for you. For the label you can insert the following code before the dialog.run().

[PHP]
label = gtk.Label("Hello World")
label.show()
dialog.get_content_area().add(label)
[/PHP]

For the rest, you can help yourself out here:

[http://www.pygtk.org/docs/pygtk/index.html](http://www.pygtk.org/docs/pygtk/index.html)

---

### Post by Levo on 2009-07-01
> **monraaf said:**
> Well, I'm not going to do all your work for you. For the label you can insert the following code before the dialog.run().

[PHP]
label = gtk.Label("Hello World")
label.show()
dialog.get_content_area().add(label)
[/PHP]

For the rest, you can help yourself out here:

[http://www.pygtk.org/docs/pygtk/index.html](http://www.pygtk.org/docs/pygtk/index.html)

Well, I said I need help, either a tutorial, or a sample script.

---

### Post by master_kernel on 2009-07-01
> **mhh91 said:**
> look for an IDE that supports PyGTK
I don't think there are any, or if there are, they probably aren't good.

Tutorial:
[http://www.pygtk.org/pygtk2tutorial/index.html](http://www.pygtk.org/pygtk2tutorial/index.html)

---

### Post by Levo on 2009-07-02
I want to set a variable:
```

DIR = gtk.FileChooserDialog(title="Please select an file",
                            action=gtk.FILE_CHOOSER_ACTION_OPEN,
                            buttons=(gtk.STOCK_CANCEL, gtk.RESPONSE_CANCEL,
                                     gtk.STOCK_OK, gtk.RESPONSE_OK))
FILE = DIR.get_filenames()
DIR.run()

```

How can I now use the variables I set? E.g. to print their values.

---

### Post by benj1 on 2009-07-02
why don't you have a look at zenity, not python but dead easy, installed by default, check the man page, will save you learning gtk just to do a simple box, unless of course you want to

---

### Post by ee_guy on 2009-07-02
I tried an IDE for pygtk and it was pretty bad.  I ended up using boa-constructor with wxpython for a project that I did.  I was pretty new to python at the time and I had not made GUIs so it really helped me out a lot.  There are also some really good tutorials for boa-constructor.

---

### Post by Levo on 2009-07-02
> **benj1 said:**
> why don't you have a look at zenity, not python but dead easy, installed by default, check the man page, will save you learning gtk just to do a simple box, unless of course you want to

I added more buttons to the dialog, so zenity doesn't fit. + I want to learn python/pygtk.
But I now need help with the variables.

---

### Post by bruce2000 on 2009-07-02
> **Levo said:**
> I added more buttons to the dialog, so zenity doesn't fit. + **I want to learn python/pygtk**.
But I now need help with the variables.

This site has a good tutorial for building a gui with pygtk and glade:

[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")

There are more here if you're interested:

[http://www.pygtk.org/articles.html]("http://www.pygtk.org/articles.html")

---

### Post by smartbei on 2009-07-02
I really think you should take the time to learn basic python before getting into GUI work. Make some console programs, take a look at the beginners challenges here at the forum, etc.

---

