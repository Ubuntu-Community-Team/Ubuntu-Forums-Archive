---
title: "Detect ubuntu shutdown event in python"
date: 2010-03-22
forum: Programming Talk
---

### Post by yabune on 2010-03-22
Is there any way to detect the shutdown event of Ubuntu in Python?

I tried this, but doesn't work...

```

import signal

def handler(signum, frame):
    print 'Shutting down...'
    f = open('log.txt', 'w')
    f.write('shutdown...')
    f.close()

signal.signal(signal.SIGTERM, handler)

```

Thank you!

---

### Post by lavinog on 2010-03-22
You need to use a signal.pause()
[http://docs.python.org/library/signal.html](http://docs.python.org/library/signal.html)
> 
signal.pause()¶
    Cause the process to sleep until a signal is received; the appropriate handler will then be called. Returns nothing. Not on Windows. (See the Unix man page signal(2).)


```

import signal

def handler(signum, frame):
    print 'Shutting down...'
    f = open('log.txt', 'w')
    f.write('shutdown...')
    f.close()

signal.signal(signal.SIGTERM, handler)
signal.pause()

```

---

### Post by yabune on 2010-03-22
> **lavinog said:**
> You need to use a signal.pause()
[http://docs.python.org/library/signal.html](http://docs.python.org/library/signal.html)


```

import signal

def handler(signum, frame):
    print 'Shutting down...'
    f = open('log.txt', 'w')
    f.write('shutdown...')
    f.close()

signal.signal(signal.SIGTERM, handler)
signal.pause()

```

thank you, lavinog!
what if I need to do something and not being in sleep mode?
I would like to have an infinite loop that is doing something in each iteration, but when it detects a shutdown, it does something else.

Something like:
```

import signal

def handler(signum, frame):
    print 'Shutting down...'
    f = open('log.txt', 'w')
    f.write('shutdown...')
    f.close()

signal.signal(signal.SIGTERM, handler)

while True:
    do_something()
    time.sleep(60)

```

thank you!

---

### Post by soltanis on 2010-03-22
Ubuntu changes runlevel when shutting down or restarting.
Runlevel 0 = Halt (shutdown)
Runlevel 6 = Reboot

Adding services those runlevels will cause them to be triggered when Ubuntu enters those conditions, so you can have them signal your script (or have your script run at those times)

---

### Post by lavinog on 2010-03-22
```

import signal
import time
import sys

def handler(signum, frame):
    print 'Shutting down...'
    f = open('log.txt', 'w')
    f.write('shutdown...')
    f.close()
    sys.exit()

def do_something():
    sys.stdout.write('.')
    sys.stdout.flush()

signal.signal(signal.SIGTERM, handler)

while True:
    do_something()
    time.sleep(60)

```

notice the sys.exit() in the handler

---

