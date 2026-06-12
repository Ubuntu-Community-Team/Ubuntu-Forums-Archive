---
title: "[Python] Socket Trouble"
date: 2011-10-28
forum: Programming Talk
---

### Post by ki4jgt on 2011-10-28
```

import socket
import threading

class server(threading.Thread):
    def run(self):
        s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        s.bind("", 7890)
        s.listen(10)
        while True:
            client, address = s.accept()
            x = client.recv()
            print x
            client.close()

server().start()

```

Output:
> 
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.7/threading.py", line 552, in __bootstrap_inner
    self.run()
  File "server.py", line 7, in run
    s.bind("", 7890)
  File "/usr/lib/python2.7/socket.py", line 224, in meth
    return getattr(self._sock,name)(*args)
TypeError: bind() takes exactly one argument (2 given)


EDIT: This script worked fine before I upgraded to 11.10.

---

### Post by karlson on 2011-10-28
> **ki4jgt said:**
> ```

import socket
import threading

class server(threading.Thread):
    def run(self):
        s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        s.bind("", 7890)
        s.listen(10)
        while True:
            client, address = s.accept()
            x = client.recv()
            print x
            client.close()

server().start()

```

Output:


EDIT: This script worked fine before I upgraded to 11.10.

From Python Website:

> 
Note This method has historically accepted a pair of parameters for AF_INET addresses instead of only a tuple. This was never intentional and is no longer available in Python 2.0 and later.

[http://docs.python.org/release/2.6.7/library/socket.html](http://docs.python.org/release/2.6.7/library/socket.html)
[http://docs.python.org/library/socket.html](http://docs.python.org/library/socket.html)

---

