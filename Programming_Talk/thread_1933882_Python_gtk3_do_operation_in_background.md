---
title: "Python gtk3 do operation in background"
date: 2012-03-01
forum: Programming Talk
---

### Post by Frozen Forest on 2012-03-01
How do you make gtk run in a separate thread, as it's now does the Gtk,main() block everything, even things in separate threads.

What I though would happen with this code was that the gui was created an did run in the thread 'Gui' then would the thread 'test1' update the listview every second. What happen is that the gui get initiated, visible and block the 'test1' thread from starting. When the gui is terminated with Gtk.main_quit will test1 finally start executing.
[PHP]
    def update_stat(self, t, data): # update the listview with new data
        while True:
            print(threading.current_thread().name)
            self.stat_list[1][2]+=2
            sleep(1)

def g(editor):   
    editor.window.show()
    Gtk.main()  
     
if __name__ == "__main__":
    editor = Gui() # create gui
    t = threading.Thread(target=g, name='Gui', args=(editor,))
    t.daemon = True
    t.start()
    threading.Thread(target=editor.update_stat, name='test1', args=(None,None)).start()
[/PHP]How do you do this in gtk?
```

editor = Gui()
editor.window.show()
Gtk.main()
answer = calc_atoms_in_body()
editor.display_answer(answer)

```

---

### Post by r-senior on 2012-03-01
I'd suggest having your GUI controlled by the main thread and using the background thread to do work. Don't create a new thread for the GUI and only update the GUI in the main thread.

Background threads with PyGTK won't work unless you call gobject.threads_init() [COLOR="RoyalBlue"][GObject.threads_init() with GTK3][/COLOR].

Have a look here:

[http://faq.pygtk.org/index.py?req=show&file=faq20.006.htp](http://faq.pygtk.org/index.py?req=show&file=faq20.006.htp)

This is GTK2, but the principle is the same.

---

### Post by Frozen Forest on 2012-03-01
I'm guessing I need something similar to this [http://www.jejik.com/articles/2007/01/python-gstreamer_threading_and_the_main_loop/](http://www.jejik.com/articles/2007/01/python-gstreamer_threading_and_the_main_loop/)

I can't seem to find the python3 bindings for gobject, I got python3-gobject installed but it does not work.

---

### Post by r-senior on 2012-03-01
You need the equivalent GTK3 bindings ...

```
from gi.repository import Gtk, GObject
```

To initialize the threading, start the application like this:

```
if __name__ == '__main__':
	GObject.threads_init()
	app = YourApplication()
	Gtk.main()

```

Then kick off the background thread and use an idle loop in your main application thread to update the GUI, e.g. put the following in your __init__ method and create an update_progress method that updates the GUI from the data collected by the background thread.

```
GObject.idle_add(self.update_progress)
```

If your background thread is a long-term daemon-type thread you'll probably also want to have it check for a flag so that it knows when to exit. Set the flag when your main thread quits, e.g. in response to the window destroy event.

---

### Post by Frozen Forest on 2012-03-04
Thanks, missed that goject also where in the same spot as gtk.

---

