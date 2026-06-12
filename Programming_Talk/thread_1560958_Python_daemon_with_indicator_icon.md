---
title: "Python daemon with indicator icon"
date: 2010-08-25
forum: Programming Talk
---

### Post by monkeyBox on 2010-08-25
I'm writing a python daemon and I'd like for it to show an indicator icon when it's running (in the future I'll likely add a menu to the icon for misc. options).  

My daemon has a basic "while: True" main loop.  So, I can't put gtk.run() in my main thread.  My solution was to put the indicator code, along with gtk.run() in a separate thread, as such:

```

gtk.gdk.threads_init()

class IndicatorThread(Thread):
    "Separate thread for gnome indicator icon"
    def run(self):
        self.ind = appindicator.Indicator("tracker-daemon", "gtg-panel", 
                appindicator.CATEGORY_APPLICATION_STATUS)
        self.ind.set_status(appindicator.STATUS_ACTIVE)
        menu = gtk.Menu()
        self.ind.set_menu(menu)
        self.running = True
        gtk.main()
        
    def stop(self):
        if getattr(self, 'running', False):
            gtk.main_quit()

```

This works for the most part, but my daemon hangs when I kill it or when I do a debug breakpoint using ipdb.set_trace().

Am I going about this all wrong?  Is there no clean way to have the gtk main loop all contained within its own thread?

---

### Post by StephenF on 2010-08-25
```

<gtk init stuff>

while running:
    while gtk.events_pending():
        gtk.main_iteration()

    <non user interface code here>

```

Alternatively:

```

<gtk init stuff>

gobject.timeout_add(100, code_to_run_periodically)
gtk.main()

```

Both those solutions will work provided you're not doing blocking IO. Such activities are best done in a thread.

Calling gtk.gdk.threads_init is not enough to make GTK thread safe. You need to bound code that accesses GTK with gtk.gdk.threads_enter / threads_leave calls.

---

### Post by monkeyBox on 2010-08-26
Thanks! A couple more questions (I'm a bit new to threading, so bear with me).  So are you saying the examples you gave could be done in a separate thread? Or do they need to be done in the main? 

Also, the only I/O I'm doing is sqlite inserts -- but I'm assuming that counts as blocking I/O, right?

---

### Post by StephenF on 2010-08-26
Some database commands are slow. It depends on whether slow commands are going to be used as to whether to go multithreaded.

Generally though, it will be possible to do one database insertion per attempt at a gtk event loop and have a very responsive user interface without additional threads.

---

