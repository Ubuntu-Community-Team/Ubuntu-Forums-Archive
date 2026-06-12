---
title: "Python &amp; gtk"
date: 2009-02-26
forum: Programming Talk
---

### Post by `GooZ´ on 2009-02-26
Hi everyone,

I'm creating a mostly commandline python app, but I would like the user to have the ability to be notified of some events using a simple GUI. I can't use notifications for this because the user can also input some text in the window (it's kind of like a small IM application).

What I tried is this:
- Started a gtk main loop every time I wished to create a window. This is not a possibility since the main loop is blocking and my program has to keep running in the background.
- Started this loop and window in a new thread. This time the windows looked all weird and were hanging.
- Started a main loop at the beginning of the program (in a thread), and creating windows troughout the program. Same problem as in point 2.

Any ideas? Thanks in advance!

---

### Post by Vadi on 2009-02-26
I don't think you need to start a loop per window. "windows looked all weird and were hanging" doesn't explain much either... could be other issues there.

---

### Post by `GooZ´ on 2009-02-26
Yes I know I don't need to start a loop per window, that's why I tried the other two options where only one loop was running troughout the program. The thing I tried with the different main loops was quitting them when the window was closed.
What I meant with the 'hanging windows' problem was that I got windows, but they only displayed a white rectangle where the input box should be, and were grey in all other places. They were also not responsive to any mouse clicks and ubuntu showed the "Application is not responding"-window.

---

### Post by unutbu on 2009-02-26
[PHP]#!/usr/bin/env python

from subprocess import Popen,PIPE,STDOUT
import time

proc=Popen("zenity --info --text 'Hi GooZ!'", shell=True, stdout=PIPE, stderr=PIPE )
while proc.poll() is None:
    time.sleep(2)
    Popen("pkill zenity", shell=True, stdout=PIPE, stderr=PIPE ).communicate()

proc=Popen("zenity --entry --text='What is your favority color'", shell=True, stdout=PIPE, stderr=PIPE )
output=proc.communicate()[0]
print 'Your favorite color is %s'%output[/PHP]

This pops up a message window for two seconds, and then closes it automatically. There is probably a cleaner way using gtk, and there is probably a cleaner way to kill the zenity process than the way I've written it. However, the above works in a pinch.

The second zenity command shows how you can get a simple text entry box, and receive a string from the user.

---

### Post by G|N| on 2009-02-26
maybe you need this:

```

lock = thread.allocate_lock()
lock.acquire()
thread.start_new_thread(self.open_window, ())
while lock.locked():
    while gtk.events_pending():
        gtk.main_iteration()
    time.sleep(0.05)

```

and don't forget to lock.release() when your thread did its job

---

### Post by tbastian on 2009-02-26
I've been working on a python gtk project myself, and had some issues with 'the windows looking weird and hanging'. It turned out that it was an issue with the fact that I was using IDLE, and gtk was interfering with the toolkit (TK) it was built on. I'm not sure which IDE you're using (if any), but you may want to try running your program via the command line to see if that fixes any bugs.

---

