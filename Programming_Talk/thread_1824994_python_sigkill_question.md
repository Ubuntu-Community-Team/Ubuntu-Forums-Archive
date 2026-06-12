---
title: "python sigkill question"
date: 2011-08-14
forum: Programming Talk
---

### Post by d3v1150m471c on 2011-08-14
I have a function in my python program that writes data to files. Does anyone know how to catch a sigkill from a terminal or another command and make the kill execute after the file has been closed to prevent problems? ie:
```

def MyFunction():
    # if sigkill exists make it wait...
    FILE = open('file', 'r')
    #do something
    FILE.close()
    # now do the sigkill

```

---

### Post by cgroza on 2011-08-14
You cannot catch a SIGKILL. You may have signal handlers for others signals, but not SIGKILL.
Take a look here.
[http://www.gnu.org/s/hello/manual/libc/Termination-Signals.html](http://www.gnu.org/s/hello/manual/libc/Termination-Signals.html)

More on signals and Python:
[http://docs.python.org/library/signal.html](http://docs.python.org/library/signal.html)

---

### Post by Smart Viking on 2011-08-14
Here's an example for handling signals, it gives you a chance to get some stuff done if some signal appears:

```
import signal,time

def hey(some,thing):
  print "Exit or whatever"

signal.signal(signal.SIGTERM,hey)
time.sleep(25) #now you do kill -15 6096


```But, as cgroza said, SIGKILL hates everyone and will kill your program.

---

### Post by d3v1150m471c on 2011-08-14
this is useful information, and thanks for all the replies. i believe i'm thinking of sigint and not sigkill. i'm thinking i'd need to catch the signal and then issue it after the file has closed?

---

### Post by cgroza on 2011-08-14
> **d3v1150m471c said:**
> this is useful information, and thanks for all the replies. i believe i'm thinking of sigint and not sigkill. i'm thinking i'd need to catch the signal and then issue it after the file has closed?
If you want to handle sigint, you have 2 alternatives.

You either use the signal module or put your code in a try block, like this:

```


try:

     #your code here
except KeyboardInterrupt:
     #your handling here


```

Python automatically throws a KeyboradInterrupt exception when SIGINT is received.

---

### Post by d3v1150m471c on 2011-08-14
i think going with the signal module will be the better of the two options here as it will be more portable. thanks for the advice. i'll mark this thread as solved.

---

