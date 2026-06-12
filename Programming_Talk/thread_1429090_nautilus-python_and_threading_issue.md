---
title: "nautilus-python and threading issue"
date: 2010-03-13
forum: Programming Talk
---

### Post by doubleeagle on 2010-03-13
Hi guys,

I'm having trouble starting a new thread from within a nautilus-python extension (or more so I'm having trouble keeping it running :D ).

Some super simple code. Place it in your nautilus-python extensions folder. (I've tried this many different ways, I think the example below shows the issue most clearly though)

```

import threading
import time
import gtk
import nautilus
import gobject

gobject.threads_init()

class Dispatcher(threading.Thread):
    def __init__(self):
        threading.Thread.__init__(self)
        self.flag = True

    def run(self):
        i = 0
        while self.flag:
            print i
            i = i + 1
            time.sleep(0.2)

t = Dispatcher()
t.start()

```

Then from the command line:
```
nautilus -q
nautilus
```

You'll see that a few numbers are printed in the terminal but pretty soon it ceases. Everytime you interact further with nautilus (click something) it'll spit out a few more iterations before ceasing again.

I really don't know what I'm doing wrong here. Is it even possible to do what I want to do here? I've googled quite a bit but am still answerless.

Any help would be greatly appreciated.

P.S. This is my first python project so please go easy :D

---

### Post by doubleeagle on 2010-03-15
Just in case someone else comes across this issue, turns out this isn't very well supported.

[http://www.mail-archive.com/nautilus-list@gnome.org/msg05930.html](http://www.mail-archive.com/nautilus-list@gnome.org/msg05930.html)

Use an external process (DBus or subprocess) to do intensive work.

---

