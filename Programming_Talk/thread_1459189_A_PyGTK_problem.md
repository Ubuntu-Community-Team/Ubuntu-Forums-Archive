---
title: "A PyGTK problem"
date: 2010-04-21
forum: Programming Talk
---

### Post by Xhacker Liu on 2010-04-21
Hello folks!
I'm writing a pyGTK program, and there are some trouble. Click the button several times, the program will crash. I try to find some informations on the Internet, but I found nothing about the problem.

I simplify my program, only the problem part remain. I'm attaching it.

Please help me, thank you.

---

### Post by simeon87 on 2010-04-21
Are you sure the problem happens in this simplified code? I can click the button all I want without errors.

You're using threads so it's very likely that the bug is related to that.. you probably need to prevent two threads from accessing the same object at the same time.

---

### Post by Xhacker Liu on 2010-04-21
> **simeon87 said:**
> Are you sure the problem happens in this simplified code? I can click the button all I want without errors.
Please click the button more times, it will crash.

> **simeon87 said:**
> You're using threads so it's very likely that the bug is related to that.. you probably need to prevent two threads from accessing the same object at the same time.
How to do it?

Thank you for your reply!

---

### Post by simeon87 on 2010-04-21
> **Xhacker Liu said:**
> Please click the button more times, it will crash.

I clicked the button many times but it really doesn't crash. For programs that use threads, that's not weird because my computer could be scheduling the threads differently than yours. What is the error that you get?

> **Xhacker Liu said:**
> How to do it?

Thank you for your reply!

You need to add synchronization code which causes a thread to wait for another thread. I don't have experience with that in Python but you could look here for example: [http://effbot.org/zone/thread-synchronization.htm](http://effbot.org/zone/thread-synchronization.htm) . When a thread tries to do something, it needs to acquire a lock and if that's not possible, it needs to wait because another thread already has the lock. This way, two threads won't access the same object together.

---

### Post by Tony Flury on 2010-04-21
I think Python Threads are different to threads implemented in C for instance, so you will need to take that into account too. Normally method is some sort of semaphore to prevent clashes.

---

### Post by Xhacker Liu on 2010-04-22
> **simeon87 said:**
> I clicked the button many times but it really doesn't crash. For programs that use threads, that's not weird because my computer could be scheduling the threads differently than yours. What is the error that you get?

Here is the crash information:
```
**
Gtk:ERROR:/build/buildd/gtk+2.0-2.20.0/gtk/gtktextview.c:3571:gtk_text_view_validate_onscreen: assertion failed: (text_view->onscreen_validated)
Core dumped.
```

> **simeon87 said:**
> You need to add synchronization code which causes a thread to wait for another thread. I don't have experience with that in Python but you could look here for example: [http://effbot.org/zone/thread-synchronization.htm](http://effbot.org/zone/thread-synchronization.htm) . When a thread tries to do something, it needs to acquire a lock and if that's not possible, it needs to wait because another thread already has the lock. This way, two threads won't access the same object together.

Maybe it can work, but it is a little bit complex. I should get lock before access the GUI every time. Do you know some easy method for PyGTK?

Thank you again!

---

### Post by Xhacker Liu on 2010-04-22
> **Tony Flury said:**
> I think Python Threads are different to threads implemented in C for instance, so you will need to take that into account too. Normally method is some sort of semaphore to prevent clashes.

Could you tell me more about PyGTK thread? Thank you!

---

### Post by Tony Flury on 2010-04-22
Just to make clear - it is Python Threads (not pyGTK - as far as I know the pyGTK framework does not provide a threading mechanism).

Python Threads are documented here : [http://docs.python.org/tutorial/stdlib2.html#multi-threading](http://docs.python.org/tutorial/stdlib2.html#multi-threading)

---

### Post by spillz on 2010-04-22
try adding gtk.gdk.threads_init() below gobject.threads_init(). gtk has its own locks that need to be initialized.

but, why are you manipulating gtk objects on multiple threads in the first place? safest practice is to manipulate gtk objects on a single thread to the extent possible.

---

### Post by moephan on 2010-04-23
When you access the UI from a thread, it's best to block other threads for a bit. 

So try changing this:
```

    def clearv(self):
        """clearv - clear the result view"""
        buf = gtk.TextBuffer(None)
        self.result_view.set_buffer(buf)

```
to this:
```

    def clearv(self):
        """clearv - clear the result view"""
        gtk.gdk.threads_enter()
        buf = gtk.TextBuffer(None)
        self.result_view.set_buffer(buf)
        gtk.gdk.threads_leave()

```

---

### Post by Xhacker Liu on 2010-04-23
Thank you very much, spillz and moephan! Mixed your ideas, my program now working well!

---

### Post by Xhacker Liu on 2010-04-23
> **spillz said:**
> try adding gtk.gdk.threads_init() below gobject.threads_init(). gtk has its own locks that need to be initialized.

but, why are you manipulating gtk objects on multiple threads in the first place? safest practice is to manipulate gtk objects on a single thread to the extent possible.

The code I attached was simplified. Actually, my program calls some other program, and show some result in the result view. Without thread, the whole GUI will be freeze when the called program is running. And is there any better idea?

Thanks a lot!

---

### Post by StephenF on 2010-04-23
Function decorators can take the pain out of matching up threads_enter with threads_leave calls. This is especially true for functions and methods with multiple exit points. Here is the fixed trage file.

```
#!/usr/bin/python
# -*- coding: utf-8 -*-

import gtk
import threading

from gettext import gettext as _
from functools import wraps

def threadlock(f):
    @wraps(f)
    def wrapper(*args, **kwds):
        gtk.gdk.threads_enter()
        ret = f(*args, **kwds)
        gtk.gdk.threads_leave()
        return ret
    return wrapper

class TrageWindow(gtk.Window):
    __gtype_name__ = "TrageWindow"

    def __new__(cls):
        builder = gtk.Builder()
        builder.set_translation_domain('trage')
        builder.add_from_file('ui/TrageWindow.ui')
        new_object = builder.get_object("trage_window")
        new_object.finish_init(builder)
        return new_object

    def finish_init(self, builder):
        self.builder = builder
        self.builder.connect_signals(self)

    def on_click(self, widget):
        t = MyThread(self.builder)
        t.start()

class MyThread(threading.Thread):
    def __init__(self, builder):
        super(MyThread, self).__init__()
        self.builder = builder
        self.result_view = self.builder.get_object('result_view')

    @threadlock
    def printv(self, str):
        """printv - print to the result view"""
        buf = self.result_view.get_buffer()
        end_iter = buf.get_end_iter()
        buf.insert(end_iter, str)

    @threadlock
    def clearv(self):
        """clearv - clear the result view"""
        buf = gtk.TextBuffer(None)
        self.result_view.set_buffer(buf)

    # No threadlock here because there are no PyGTK calls.
    def run(self):
        self.clearv()
        self.printv(_('Hello!\n'))

# The main code and its callbacks count as a single thread.
@threadlock
def main():
    window = TrageWindow()
    window.show()
    gtk.main()
    
if __name__ == "__main__":
    gtk.gdk.threads_init()
    main()

```

**Edit:**
Here is an improved version of threadlock that will prevent exceptions from hanging the program.

```
def threadlock(f):
    @wraps(f)
    def wrapper(*args, **kwds):
        gtk.gdk.threads_enter()
        try:
            ret = f(*args, **kwds)
        finally:
            gtk.gdk.threads_leave()
        return ret
    return wrapper

```

---

### Post by StephenF on 2010-04-23
> **Xhacker Liu said:**
> The code I attached was simplified. Actually, my program calls some other program, and show some result in the result view. Without thread, the whole GUI will be freeze when the called program is running. And is there any better idea?

You could try subprocess.Popen and gobject.io_add_watch together to create a sub-process and perform polling on the pipe in the background. I imagine the code will be a great deal simpler.

**Edit:**
It works.

```
#!/usr/bin/python
# -*- coding: utf-8 -*-

import gtk
import gobject
import subprocess

from gettext import gettext as _

class TrageWindow(gtk.Window):
    __gtype_name__ = "TrageWindow"

    def __new__(cls):
        builder = gtk.Builder()
        builder.set_translation_domain('trage')
        builder.add_from_file('ui/TrageWindow.ui')
        new_object = builder.get_object("trage_window")
        new_object.finish_init(builder)
        return new_object

    def finish_init(self, builder):
        self.builder = builder
        self.builder.connect_signals(self)
        self.connect('destroy', lambda x: gtk.main_quit())

    def show_data(self, pipe, condition, result_view, proc):
        # Could clear the text buffer here to only ever show one set of results.
        stdoutdata, stderrdata = proc.communicate()
        buf = result_view.get_buffer()
        end_iter = buf.get_end_iter()
        buf.insert(end_iter, '*** pid=%d ***\n%s\n' % (proc.pid, stdoutdata))
        return False

    def on_click(self, widget):
        result_view = self.builder.get_object('result_view')
        # Could put the clear function on a separate button.
        result_view.set_buffer(gtk.TextBuffer(None))
        # Five second delay allows multiple clicks to be accumulated.
        proc = subprocess.Popen('sleep 5 ; /bin/ls /usr', shell=True, stdout=subprocess.PIPE, close_fds=True)
        gobject.io_add_watch(proc.stdout, gobject.IO_HUP | gobject.IO_IN, self.show_data, result_view, proc)
    
if __name__ == "__main__":
    window = TrageWindow()
    window.show()
    gtk.main()

```

---

### Post by Xhacker Liu on 2010-04-24
> **StephenF said:**
> You could try subprocess.Popen and gobject.io_add_watch together to create a sub-process and perform polling on the pipe in the background. I imagine the code will be a great deal simpler.

**Edit:**
It works.

```
#!/usr/bin/python
# -*- coding: utf-8 -*-

import gtk
import gobject
import subprocess

from gettext import gettext as _

class TrageWindow(gtk.Window):
    __gtype_name__ = "TrageWindow"

    def __new__(cls):
        builder = gtk.Builder()
        builder.set_translation_domain('trage')
        builder.add_from_file('ui/TrageWindow.ui')
        new_object = builder.get_object("trage_window")
        new_object.finish_init(builder)
        return new_object

    def finish_init(self, builder):
        self.builder = builder
        self.builder.connect_signals(self)
        self.connect('destroy', lambda x: gtk.main_quit())

    def show_data(self, pipe, condition, result_view, proc):
        # Could clear the text buffer here to only ever show one set of results.
        stdoutdata, stderrdata = proc.communicate()
        buf = result_view.get_buffer()
        end_iter = buf.get_end_iter()
        buf.insert(end_iter, '*** pid=%d ***\n%s\n' % (proc.pid, stdoutdata))
        return False

    def on_click(self, widget):
        result_view = self.builder.get_object('result_view')
        # Could put the clear function on a separate button.
        result_view.set_buffer(gtk.TextBuffer(None))
        # Five second delay allows multiple clicks to be accumulated.
        proc = subprocess.Popen('sleep 5 ; /bin/ls /usr', shell=True, stdout=subprocess.PIPE, close_fds=True)
        gobject.io_add_watch(proc.stdout, gobject.IO_HUP | gobject.IO_IN, self.show_data, result_view, proc)
    
if __name__ == "__main__":
    window = TrageWindow()
    window.show()
    gtk.main()

```

Thanks a lot! Your code inspired me. Now my program is perfect.

---

