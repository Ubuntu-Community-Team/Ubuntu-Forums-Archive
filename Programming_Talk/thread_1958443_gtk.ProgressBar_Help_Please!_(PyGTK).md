---
title: "gtk.ProgressBar Help Please! (PyGTK)"
date: 2012-04-14
forum: Programming Talk
---

### Post by ammyt on 2012-04-14
Hello there!
I am trying to build a simple program with the following code:
```

import gtk
import os
import hildon

class Finestra(gtk.Window):
    #GTK Window
   def __init__(self):
       gtk.Window.__init__(self, gtk.WINDOW_TOPLEVEL)
       self.set_title('NITDroid Installer')
       self.resize(220,150)
       self.connect('destroy', self.chiudi)

    #Buttons
       install = hildon.Button(gtk.HILDON_SIZE_AUTO_WIDTH | gtk.HILDON_SIZE_FINGER_HEIGHT, hildon.BUTTON_ARRANGEMENT_VERTICAL)
       install.set_text("                            Quick Install                          ", "")
       install.connect('clicked', self.install, None)
       install.show()

     #Progressbar
       pbar = gtk.ProgressBar()
       pbar.set_pulse_step(2)
       pbar.pulse()
       pbar.show()

    #Graphic setup
       fixed = gtk.Fixed()

       #install
       fixed.put(install, 160, 70)
       #progress bar
       fixed.put(pbar, 0, 370)

       fixed.show()
       self.add(fixed)

    #Function of buttons
   def mostra(self):
       self.show()
       gtk.main()

   def install(self, widget, data=None):
       fancy_stuff_to_activate_progressbar_pulsing
       os.system('sh /home/user/test')

   def chiudi(self, widget, data=None):
       gtk.main_quit()

if __name__ == '__main__':
   f = Finestra()
   f.mostra()
```
As you can see, the code creates a window with a single button and a progressbar. I want the button, when clicked, to execute a small script and trigger activity mode of the progressbar until the script finishes its job. I searched a lot but still canmt figure it out. some help is greatly appreciated!

---

### Post by r-senior on 2012-04-14
I just happen to have a little example that does similar. It's Python with GTK3 though.

```
#!/usr/bin/env python
'''
Simple example of a PyGTK3 application with a background thread.
'''

import random
import threading
import time

from gi.repository import Gtk, GObject

APP_NAME = 'Threaded GUI Example'
TARGET = 100.0

class WorkerThread(threading.Thread):
    '''
    The worker thread, which would normally do something more useful.

    It is important that the worker thread does not attempt to update the
    GUI. Doing so can cause crashes and weird behaviour.

    @param delegate the object to be informed of progress being made
    '''
    def __init__(self, delegate):
        threading.Thread.__init__(self)
        self.delegate = delegate
        self.counter = 0
        self.done = False

    def run(self):
        '''
        The work done by the thread.

        Overridden from threading.Thread. Sits in a loop until the done
        flag is set, updating a counter and sleeping to simulate some work.
        '''
        while True:
            if self.done:
                print 'Background thread shutting down cleanly'
                break

            # This counter is only updated by one thread, so probably
            # doesn't need a lock, but it needs thinking about.
            self.counter = self.counter + 1 if self.counter < TARGET else 0

            # Ask the main thread to update the GUI when it has time.
            GObject.idle_add(self.delegate.update_progress)

            # Sleep for a little bit ...
            time.sleep(random.uniform(0.01, 0.1))


class Main(Gtk.Window):
    '''
    The main application GUI running in the main thread.
    '''
    def __init__(self):
        Gtk.Window.__init__(self, title=APP_NAME)
        self.set_size_request(500, 300)

        # Lay out the GUI.
        vbox = Gtk.VBox(False, 0)

        # Set up a progress bar to show how the worker is progressing.
        self.progress_bar = Gtk.ProgressBar()
        vbox.pack_start(self.progress_bar, False, False, 0)

        # Set up a text view to show the responsiveness of the GUI.
        scroller = Gtk.ScrolledWindow()
        textview = Gtk.TextView()
        textview.get_buffer().set_text(
            'The counting is going on in the worker thread with the GUI '\
            'handling updates in the idle loop. You can type in the text '\
            'view or resize the window and it should be responsive.\n\n'
        )
        textview.set_wrap_mode(Gtk.WrapMode.WORD)
        scroller.add(textview)
        vbox.pack_start(scroller, True, True, 0)

        self.add(vbox)
        self.show_all()

        # Connect the destroy event so that we can set the done flag and
        # terminate the worker cleanly.
        self.connect("destroy", self.on_quit)

        # Kick off the background thread.
        self.worker = WorkerThread(self)
        self.worker.start()

    def update_progress(self):
        '''
        Update the progress bar.

        The method called on request in the idle loop to update the GUI. The
        worker requests the update using GObject.idle_add()
        @return True to repeat indefinitely, False for a single invocation
        '''
        progress = self.worker.counter / TARGET
        self.progress_bar.set_fraction(progress)
        self.set_title('{} ({}%)'.format(APP_NAME, progress * 100))
        return False

    def on_quit(self, widget):
        '''
        Quit the application

        Handler called when the application is about to quit. Set the done
        flag so that the worker quits cleanly, then quit.
        '''
        self.worker.done = True
        Gtk.main_quit()


if __name__ == '__main__':
    # The background thread will not run concurrently against the main
    # thread without the threads_init() call:
    GObject.threads_init()
    Main()
    Gtk.main()


```

---

### Post by ammyt on 2012-04-14
@r-senior
Thanks a lot!
I will look into it and reply back.

---

### Post by ammyt on 2012-04-14
I tried that and it works however, this whole threading setup is driving me nuts, i still don't know how should I execute the script...

---

### Post by r-senior on 2012-04-14
You'd replace the body of the run method with whatever your script does. You need to change the progress calculation stuff to suit. The GObject.idle_add asks the main thread to do something when it can and your script would need to use that to call update_progress at appropriate points. Perhaps that would be better with a progress percentage as a parameter, e.g.

```
def update_progress(self, progress):
    '''
    Update the progress bar.

    progress -- the progress as a percentage

    The method called on request in the idle loop to update the GUI.  
    The worker requests the update using GObject.idle_add()
    Return True to repeat indefinitely, False for a single invocation
    '''
    self.progress_bar.set_fraction(progress)
    return False
```

---

