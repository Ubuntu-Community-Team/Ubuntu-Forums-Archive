---
title: "[pygtk] getting row data from mouse click?"
date: 2005-01-08
forum: Programming Talk
---

### Post by stateq2 on 2005-01-08
In a treeview/liststore, I'm trying to figure out how to catch a mouseclick and return the data from that particular row...perhaps by connecting a signal to a treeview or something?  I'd love input from anyone who's familiar w/ pygtk...thanks.

---

### Post by iwasbiggs on 2005-01-11
Yep, signal to treeview on click or mouse down event then grab the current row(s) from teh tree/list store. Don't have any examples off hand...

---

### Post by Johan on 2005-01-11
Do you have any links to the documentation of the pygtk api? I'd really appreciate it (and go write some nice-looking gnome-apps)!

---

### Post by Daniel G. Taylor on 2005-01-12
You can find an API reference here: [http://www.pygtk.org/reference.html](http://www.pygtk.org/reference.html)

I'm sure I've done what you are asking before, but I also don't have any examples of getting the current row at the moment...

---

### Post by Johan on 2005-01-12
[QUOTE=Daniel G. Taylor]You can find an API reference here: [http://www.pygtk.org/reference.html](http://www.pygtk.org/reference.html)

I'm sure I've done what you are asking before, but I also don't have any examples of getting the current row at the moment...[/QUOTE]
 Ah, thanks!

---

### Post by stateq2 on 2005-01-13
[QUOTE=iwasbiggs]Yep, signal to treeview on click or mouse down event then grab the current row(s) from teh tree/list store. Don't have any examples off hand...[/QUOTE]

thanks, that's the basic idea.  I did a little more searching and found this page
[http://www.async.com.br/faq/pygtk/index.py?querytype=simple&query=double+click&req=search](http://www.async.com.br/faq/pygtk/index.py?querytype=simple&query=double+click&req=search)

so basically, I added an event to my treeview, as well as connected the signal:
```

self.treeview.add_events(gtk.gdk.BUTTON_PRESS_MASK)
self.treeview.connect('button_press_event', self.selectTest)

```

the signal was to this callback:
```

def selectTest(self, widget, event):
                if event.button == 1 and event.type == gtk.gdk._2BUTTON_PRESS:
                        print 'left double click'

                        #get data from highlighted selection       
                        treeselection = self.treeview.get_selection()
                        (model, iter) = treeselection.get_selected()
                        name_of_data = self.liststore.get_value(iter, 0)

                        #do something w/ 'name_of_data' here                                                  

```

and it worked great :)  thanks for the info.....now to impliment threading  ](*,)

---

### Post by Daniel G. Taylor on 2005-01-13
[QUOTE=stateq2]now to impliment threading[/QUOTE]
Be careful with GTK + threading!

Only access the GUI from a single thread (or use a queued dispatcher)!

If you start to get seemingly random segmentation faults, it's most likely that different threads are touching data simultaneously or when they aren't supposed to.

Check out (I think) gtk_threads_init or something like that and secure your variables with locks/semaphores.

Alternatively check out gobject.timeout_add(milliseconds, function) (newest development pygtk version, for older versions use gtk.timeout_add). That will call function() every so many milliseconds and you can update your GUI that way. For an example, I use it with my [Key Status Monitor ](http://programmer-art.org/key-status)app.

---

### Post by stateq2 on 2005-01-14
I almost got it, but there's a small problem...so here's the quick question about threading.....

the following won't work right
```

threading.Thread(target=myClass.func(foo)).start()

```
but this will
```

threading.Thread(target=myClass.func).start()

```

'foo' is an argument passed to 'myClass.func()'.  for some reason, threading doesn't work when I do this.  is there any way I can pass an argument to this function?  thanks

**edit:**
problem fixed....
```

threading.Thread(target=myClass.func, args=(foo, )).start()

```
....did the trick

---

