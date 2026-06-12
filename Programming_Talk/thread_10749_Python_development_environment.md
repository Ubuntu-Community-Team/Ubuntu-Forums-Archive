---
title: "Python development environment"
date: 2005-01-10
forum: Programming Talk
---

### Post by Ozitraveller on 2005-01-10
I've read a lot of the Python threads here and I haven't seen any mention of an IDE I know there is one. And I haven't found it in the repositories yet. I'm just getting into python, so I'm just exploring possibilities here.

I'd be interested to hear what people are using and maybe causes thhem to make the choice, and what they build with python.

I hope this question hasn't been aksed before, I didn't see one!!!

---

### Post by iwasbiggs on 2005-01-11
gvim and a terminal or two. I know there are ample ides on windows but I haven't found one I like for large projects on Linux.

---

### Post by Quest-Master on 2005-01-11
I don't use any IDEs in Python simply because I don't need one, but here's a really nice one called SPE: [http://spe.pycs.net/](http://spe.pycs.net/)

---

### Post by DirtDawg on 2005-01-11
Shoot. I just use IDLE. But then, I'm not very good at programming (but i do looooove Python!). :D

---

### Post by dataw0lf on 2005-01-11
A combo of jedit and IDLE works for me.
dataw0lf

---

### Post by Ozitraveller on 2005-01-11
Thanks Guys

---

### Post by Ozitraveller on 2005-01-11
I've seen some use PyGTK, and I've mention of Python and Glade, are they the same?

---

### Post by Ozitraveller on 2005-01-11
I've seen some use PyGTK, and I've mention of Python and Glade, are they the same?

---

### Post by Quest-Master on 2005-01-11
Glade is an GUI designer for your applications. You make all of the stuff on the inside work with Python. :)

---

### Post by Ozitraveller on 2005-01-11
[QUOTE=Quest-Master]Glade is an GUI designer for your applications. You make all of the stuff on the inside work with Python. :)[/QUOTE]

Interesting Quest-Master. Thanks.

---

### Post by Daniel G. Taylor on 2005-01-12
I mostly just code in gedit because it can syntax-highlight Python code and is quick for me. I always keep a terminal open so I can run my program after making changes and saving, too. For bigger projects I also always keep python running in another terminal so I can test new code interactively (one of the best things about Python, in my opinion).

About Python, pygtk, Glade: Python is the programming language, pygtk is a set of bindings for the GTK+ interface toolkit, and Glade is a graphical interface designer and XML file format for storing interfaces (which you can load using Python and pygtk + glade). So, you generally build a GUI using glade, save it and load it from a Python program, finish up the interface and connect to events (like mouse clicks) with pygtk, and then do the actual program logic in Python.

For beginners it may be helpful to look at just pure pygtk without glade to help you better understand how GTK+ works. (This would mean building your interface piece-by-piece in the code instead of a GUI builder)

It's quite simple really:
```
#!/usr/bin/env python
import gtk
label = gtk.Label("Hello, world!")
window = gtk.Window()
window.set_title("My first pygtk app!")
window.add(label)
window.show_all()
window.connect("destroy", gtk.main_quit)
gtk.main()
```

---

### Post by Ozitraveller on 2005-01-12
[QUOTE=Daniel G. Taylor]I mostly just code in gedit because it can syntax-highlight Python code and is quick for me. I always keep a terminal open so I can run my program after making changes and saving, too. For bigger projects I also always keep python running in another terminal so I can test new code interactively (one of the best things about Python, in my opinion).

About Python, pygtk, Glade: Python is the programming language, pygtk is a set of bindings for the GTK+ interface toolkit, and Glade is a graphical interface designer and XML file format for storing interfaces (which you can load using Python and pygtk + glade). So, you generally build a GUI using glade, save it and load it from a Python program, finish up the interface and connect to events (like mouse clicks) with pygtk, and then do the actual program logic in Python.

For beginners it may be helpful to look at just pure pygtk without glade to help you better understand how GTK+ works. (This would mean building your interface piece-by-piece in the code instead of a GUI builder)

It's quite simple really:
```
#!/usr/bin/env python
import gtk
label = gtk.Label("Hello, world!")
window = gtk.Window()
window.set_title("My first pygtk app!")
window.add(label)
window.show_all()
window.connect("destroy", gtk.mainquit)
gtk.main()
```[/QUOTE]

Thanks Daniel.

---

### Post by jdodson on 2005-01-12
i just use gedit like daniel.  its a nice program that does syntax highlighting and when i want to run the script head over to the terminal.

i dont use any fancy debuggers as simple print statements find the bug quick enough.  now if i was debugging someone elses code...... maybe i might find one as its hard to retrace code you are not used to sometimes. :) 

anyways, gedit+terminal == nice python development enviorment.

not sure what else you would need, unless it had a built in debugger.

---

### Post by Ozitraveller on 2005-01-12
Thanks.

I was hoping for a good IDE, it just makes it better to work on large projects woth other peoples code. That SPE one looks ok, but probably still a bit green yet for prod work maybe.

---

### Post by Daniel G. Taylor on 2005-01-12
Stupid me, that line should read 'gtk.main_quit' instead of 'gtk.mainquit'

I thought I'd also note that that quick example is using the latest GTK+ and pygtk from Hoary, so if you are using Warty you should maybe replace 'gtk.main()' with 'gtk.mainloop()' and use 'gtk.mainquit'.

That said, gedit 2.9.4 (or maybe it's the new gtksourceview?) is adding a sort of  current line highlighting feature, which I like. It let's you see where you are very quickly.

Also, about debugging: check out python's logging functionality. It's very useful for outputting debug statements. (I don't know of anything that will provide step-by-step execution or break points, though)

[http://docs.python.org/lib/module-logging.html](http://docs.python.org/lib/module-logging.html)

I like to use the format string "%(module)s [%(lineno)d]: %(levelname)s %(message)s" which will output stuff formatted like: "log [66]: INFO Logging system started." That tells me it's from the file log.py, line 66, and an informational message letting me know the logging system is running. To produce the above message I called the logging module's info function: info("Logging system started").

You can also have it output to any stream, so you could for example output to a log file or to stdout/stderr, or do both simultaneously with very little code.

---

### Post by Ozitraveller on 2005-01-13
[QUOTE=Daniel G. Taylor]Stupid me, that line should read 'gtk.main_quit' instead of 'gtk.mainquit'

I thought I'd also note that that quick example is using the latest GTK+ and pygtk from Hoary, so if you are using Warty you should maybe replace 'gtk.main()' with 'gtk.mainloop()' and use 'gtk.mainquit'.

That said, gedit 2.9.4 (or maybe it's the new gtksourceview?) is adding a sort of  current line highlighting feature, which I like. It let's you see where you are very quickly.

Also, about debugging: check out python's logging functionality. It's very useful for outputting debug statements. (I don't know of anything that will provide step-by-step execution or break points, though)

[http://docs.python.org/lib/module-logging.html](http://docs.python.org/lib/module-logging.html)

I like to use the format string "%(module)s [%(lineno)d]: %(levelname)s %(message)s" which will output stuff formatted like: "log [66]: INFO Logging system started." That tells me it's from the file log.py, line 66, and an informational message letting me know the logging system is running. To produce the above message I called the logging module's info function: info("Logging system started").

You can also have it output to any stream, so you could for example output to a log file or to stdout/stderr, or do both simultaneously with very little code.[/QUOTE]

Thanks Daniel, that's useful info!

And yes I am running Hoary, and it's current;y broken too. Also I think it had something to do with python!!!!  This "gtksourceview" looks familiar from the log.

---

### Post by Daniel G. Taylor on 2005-01-13
Ozitraveller, I don't think it has much to do with Python, unless it's not letting you upgrade your python/pygtk packages because of the new gtksourceview one. The basic problem is that libgtksourceview wants to be upgraded, which depends on the new libgtksourceview-common package, and that package now contains a file that was previously owned by the libgtksourceview package, so libgtksourceview-common refuses to overwrite it while the old libgtksourceview package is still installed.

There is a post here on the forums about it and a bug I commented on yesterday, so hopefully it will be fixed soon. If you need it fixed now, you can "solve" the issue by removing libgtksourceview, upgrading libgtksourceview-common, then reinstalling libgtksourceview (and everything else that was removed, which is why I say "solve" like that). I think I will wait a few days and see what happens. :-)

---

### Post by gamehack on 2005-01-13
[QUOTE=Ozitraveller]Thanks.

I was hoping for a good IDE, it just makes it better to work on large projects woth other peoples code. That SPE one looks ok, but probably still a bit green yet for prod work maybe.[/QUOTE]
Try ActiveState Komodo :) It's superb. It's available for Lin, Win and Mac.

---

### Post by Ozitraveller on 2005-01-13
[QUOTE=gamehack]Try ActiveState Komodo :) It's superb. It's available for Lin, Win and Mac.[/QUOTE]

Yes, I like it, and I wish it were free too!

---

### Post by stateq2 on 2005-01-13
I use vim only

---

### Post by lee_connell on 2005-01-21
[www.wingide.com](www.wingide.com) is very nice ide which is built using pygtk and has support for mod_python, plone, zope :)

---

### Post by Ozitraveller on 2005-01-21
[QUOTE=lee_connell][www.wingide.com](www.wingide.com) is very nice ide which is built using pygtk and has support for mod_python, plone, zope :)[/QUOTE]

It'd be nice, but it's not free.

had anyone an opinion on which is better Glade/Tkinter? Or is there a better UI builder?

---

### Post by Quest-Master on 2005-01-21
Glade is most likely the best you'd get; besides using Boa with wxPython.. too bad the wxPython in apt (Warty) is so old, it still uses GTK1.x. :(

---

### Post by Ozitraveller on 2005-01-21
[QUOTE=Quest-Master]Glade is most likely the best you'd get; besides using Boa with wxPython.. too bad the wxPython in apt (Warty) is so old, it still uses GTK1.x. :([/QUOTE]

Is anyone does a one ide does all, like vs.net, with the ui builders in the ide? BTW vs.net was only an example, there others as well.

---

### Post by poster_nutbag on 2005-01-24
[QUOTE=stateq2]I use vim only[/QUOTE]

I think you misspelt 'Emacs' there, my friend

---

### Post by dataw0lf on 2005-01-24
Eh? vim is a lightweight, yet powerful, editor.  Emacs is an actual operating system.  There is no comparison.
dataw0lf

---

