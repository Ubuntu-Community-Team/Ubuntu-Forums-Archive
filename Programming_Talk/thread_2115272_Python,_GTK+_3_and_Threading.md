---
title: "Python, GTK+ 3 and Threading"
date: 2013-02-12
forum: Programming Talk
---

### Post by Nebelhom on 2013-02-12
Hi,

I've been trying to use a [progressbar in GTK+ 3]("http://python-gtk-3-tutorial.readthedocs.org/en/latest/progressbar.html") lately, but during the processes where a progressbar is needed to show that it's working, my GUI freezes up during the call. At least when following [the GTK+ 3 Tutorial]("http://python-gtk-3-tutorial.readthedocs.org/en/latest/index.html").

Thus, I am trying to do it with a Worker Thread. Unfortunately, I am not getting anywhere. Does anyone know of a decent example that I could use as a guide?

I only found examples of PyGTK so far (I really start to wonder why I didn't use it in the first place) and I am having trouble adjusting that code to my needs :(

Thanks for all the help.

Here are the links that I came across:

[http://stackoverflow.com/questions/2805455/gtk-progressbar-pulsing-python]("http://stackoverflow.com/questions/2805455/gtk-progressbar-pulsing-python")
[http://ubuntuforums.org/showpost.php?p=6755239&postcount=17]("http://ubuntuforums.org/showpost.php?p=6755239&postcount=17")
[http://faq.pygtk.org/index.py?req=show&file=faq20.001.htp]("http://faq.pygtk.org/index.py?req=show&file=faq20.001.htp")

---

### Post by bird1500 on 2013-02-12
I'm using gtkmm, if you know how to use the Glib::signal_idle() function you should be fine.
Here's in C++ how I do it:

```

class ClassObj {
    //runs in main thread
    //when called from another thread thru Glib::signal_idle()
    bool updateMyBar() {
        myProgressbar..do something
        return false;
    }
}

```From your (non-main) thread call:
...
ClassObj *classObj;//obtain pointer to the ClassObj from the thread
Glib::signal_idle().connect(*classObj, &ClassObj::updateMyBar);

And nothing should be blocking. Otoh the python paradigm might be so different that it's not practical to use my approach.

---

### Post by Nebelhom on 2013-02-12
@bird1500: Thanks for your input! I think gtkmm is just the name of the library for C++ (I may be wrong though, but [this page]("http://stackoverflow.com/tags/gtk/info") suggests it)

I will try to look for a Glib::signal_idle() equivalent and attempt to incorporate it. Unfortunately, I have no knowledge of C++ whatsoever, which also makes reading the GTK+ 3 Manual interesting at times ;)

Thanks again. It's really appreciated.

---

### Post by Nebelhom on 2013-02-14
Ok folks,

I am still stumped on this problem, but I have made progress. I have adapted the example below from [this post here]("http://ubuntuforums.org/showpost.php?p=6755239&postcount=17") that describes the procedure for pygtk. This example works fine.

Now, my worker thread needs to have the ability to accept arguments for the function, too. Ideally the amount of arguments can be variable so that I can pass any function, I want over to it. Eg.

```
WT = WorkerThread(self, self.work, arg1, arg2,... argX)
```

which would run a function that "could" look like this here:

```
def work(self, *args)
```

Does anyone have an idea how to do this? I will not show my unsuccesful attempts as I have noticed that it only brings people to bark up the wrong tree :(

Thanks for all your help, folks.

```
import threading
import random, time

from gi.repository import Gtk, GObject 

class MainThread:

    def __init__(self):
        GObject.threads_init()
        self.fs = None

    def main_quit(self, obj):
        if not self.fs == None: self.fs.stop()
        Gtk.main_quit()
        
    def pulse(self):
        self.progressbar.pulse()
        return self.still_working # 1 = repeat, 0 = stop

    def work(self): ###### This would be the actual time-consuming workload
        time.sleep(200) 

    def main(self):
        window = Gtk.Window()
        vbox = Gtk.VBox()
        self.progressbar = Gtk.ProgressBar()
        vbox.pack_start(self.progressbar, True, True, 0)
        window.add(vbox)
        window.show_all()
        window.connect('destroy', self.main_quit)
        
        WT = WorkerThread(self.work, self)
        WT.start()
        GObject.timeout_add(100, self.pulse)
        
        Gtk.main()


class WorkerThread(threading.Thread):
    def __init__ (self, function, parent):
        threading.Thread.__init__(self)
        self.function = function
        self.parent = parent
    
    def run(self): # when does "run" get executed?
        self.parent.still_working = True
        self.function()
        self.parent.still_working = False
    
    def stop(self):
        self = None
        
if __name__ == '__main__':
    MT = MainThread()
    MT.main()
```

---

### Post by Nebelhom on 2013-02-14
I'm a dumb little *<expletive>*. Find the solution to my problem below. Note the use of this simple line here:

```
self.wt = threading.Thread(target=self.work, args=()) # <- put arguments here
```

the rest is the in essence the same. thanks goes to a user in a different forum where I asked the question.

```
import threading
import random, time

from gi.repository import Gtk, GObject

class MainThread:

    def __init__(self):
        GObject.threads_init()
        self.fs = None

    def main_quit(self, obj):
        if self.fs is not None: self.fs.stop()
        Gtk.main_quit()
       
    def pulse(self):
        self.progressbar.pulse()
        return self.is_alive() # 1 = repeat, 0 = stop

    def work(self): ###### This would be the actual time-consuming workload
        time.sleep(200)

    def main(self):
        window = Gtk.Window()
        vbox = Gtk.VBox()
        self.progressbar = Gtk.ProgressBar()
        vbox.pack_start(self.progressbar, True, True, 0)
        window.add(vbox)
        window.show_all()
        window.connect('destroy', self.main_quit)
       
        self.wt = threading.Thread(target=self.work, args=()) # <- put arguments here
        self.wt.start()
        GObject.timeout_add(100, self.pulse)
       
        Gtk.main()


if __name__ == '__main__':
    mt = MainThread()
    mt.main()
```

---

