---
title: "Python and PyGTK questions"
date: 2009-09-28
forum: Programming Talk
---

### Post by Tortel on 2009-09-28
I am working on a program that will check my gmail and use libnotify to tell me when I have new messages. So far, it will connect/check gmail and the notification is working. I am also working on a tray icon that when clicked will open a window to change configuration settings. The window works, but right now when you close the window the tray icon dies too.

How would I go about closing a gtk.Window() element without killing the StatusIcon element too?

---

### Post by Tortel on 2009-09-28
UPDATE: I changed how my program works, its now threaded. Heres the threading code:

```

class trayThread ( threading.Thread ):
  def run ( self ):
    tmp = trayTest.trayIcon()
    gtk.main()

class readerThread ( threading.Thread ):
  def run ( self ):
    while(1>0):
      print strftime("%H:%M:%S", localtime()) + " Checking..."
      checkMail()
      print strftime("%H:%M:%S", localtime()) + " Done!"
      time.sleep(120)

if __name__=="__main__":
  readerThread().start()
  trayThread().start()

```

trayTest.trayIcon() is the tray icon, and the window is opened using self.icon.connect("activate", self.openWindow)

Now when I close the window, the tray icon stops responding and will not go away. Heres the code for the window to close:

```

  def delete_event(self, widget, event, data=None):
    gtk.main_quit()
    return False

  def destroy(self, widget, data=None):
    print "Destroy signal occurred, exiting..."
    self.delete_event(self,self.window,None)

```

Ideas?

(If you want to see more of the code, ask)

---

### Post by engla on 2009-09-29
You should run gtk.main() in the main thread, not in a separate thread you started.

All of your program's logic is going to happen "inside" the gtk.main() call; and you quit when you call gtk.main_quit(); so don't call that when closing the window if you don't want to quit your application!

Then you should probably use the main event loop and only spawn a new rescan thread every 2 minutes, instead of letting the thread run forever (the forever-running thread is what keeps your program hanging, neither responding nor exiting).

glib.timeout_add_seconds lets you set up timed callbacks inside the main event loop (to for example, start a new mail thread two minutes after the last one).

The callback to the window's delete-event should simply call .hide() on the window and return True (important True = you handled the event, otherwise it goes on to the default handler which destroys the window.)

---

### Post by Tortel on 2009-09-29
Well, the window will now open/close without killing the tray icon, but I cant seem to get the tray icon and window to work with the mail checking thread. It just stalls, and I think its the gtk.main() thats doing it. If I interrupt the main thread (which now runs the gtk.main() ), my second thread (the mail checking one) will finally work, then crash. I tried to use the glib.timeout_add_seconds(), but I get this error:

```

Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 525, in __bootstrap_inner
    self.run()
  File "threads.py", line 17, in run
    glib.timeout_add_seconds(120,checkMail())
TypeError: second argument not callable

```

Updated code:
```

class readerThread ( threading.Thread ):
  def run ( self ):
    glib.timeout_add_seconds(120,checkMail())
    

def readMail(*args):
  checkMail()
  return True

if __name__=="__main__":
  readerThread().start()
  tmp=trayTest.trayIcon()
  gtk.main()

```

I suppose that if I can get the exception fixed with the glib.timeout_add_seconds() call, I could stick that in another file and just execute that file from my tray icon/window file

---

### Post by engla on 2009-09-29
> **Tortel said:**
> 
```

glib.timeout_add_seconds(120,checkMail())

```


You should pass timeout_add_second a function object to call later, not call the function and give it the return value:

```

glib.timeout_add_seconds(120,checkMail)

```

What does the checkMail function do? If it does any gtk calls *at all* you have to init threads in the beginning of your program:

gtk.gdk.threads_init() 

and enclose any gtk operations **outside** of the main thread inside guarding enter/leave statements:

```
gtk.threads_enter()
status_icon.change_something() # this is a gtk call
gtk.threads_leave()
```

However, it is hardly worth it to do gtk calls from an outside thread! Do data processing or network requests (like here) on the separate thread, then update the GUI on the main thread. Using a timed callback like glib.timeout_add_seconds will execute on the main thread. So you can do this:

glib.idle_add(update_gui, result)

which will call
```
def update_gui(result):
    # well you fill this with content
    pass
```

on the main thread!

glib.idle_add is just like timeout_add_seconds, except it will be executed as soon as it gets around to it. timeout_add_seconds(0, ...) has much the same effect.

---

### Post by Tortel on 2009-09-30
Well, after changing it to glib.timeout_add_seconds(120,checkMail) and making checkmail return True, it now works fine.
I double checked the checkMail for and gtk calls, and remove an unused gtk import. After that, it started to work. 
Thanks for your help!

---

### Post by engla on 2009-10-01
It feels good to know that your program now uses a proper gtk event loop, and handles its threads correctly. Good luck with the program!

---

