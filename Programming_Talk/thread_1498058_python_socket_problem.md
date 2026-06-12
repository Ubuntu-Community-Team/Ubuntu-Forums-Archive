---
title: "python socket problem"
date: 2010-05-31
forum: Programming Talk
---

### Post by ixxalnxxi on 2010-05-31
I have this basic script, (I don't need help with the script, but rather it's process)

```
# Echo server program
import socket
import shelve
import pickle

HOST = 'localhost'                 # Symbolic name meaning all available interfaces
PORT = 50007              # Arbitrary non-privileged port
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind((HOST, PORT))
s.listen(1)
words = shelve.open('/home/tipu/Dropbox/dev/workspace/search/words.db', 'r');
tweets = shelve.open('/home/tipu/Dropbox/dev/workspace/search/tweets.db', 'r');
while 1:
    conn, addr = s.accept()
    print 'Connected by', addr
    query = conn.recv(1024)
    try:
        result = words[query]
        print(result)
    except KeyError:
        result = "set()"
    conn.send(result)
conn.close()
```

I run it doing python server.py, and it runs great. However when I terminate it, "killall -v python", I will randomly get:
```

Traceback (most recent call last):
  File "server.py", line 9, in <module>
    s.bind((HOST, PORT))
  File "<string>", line 1, in bind
socket.error: [Errno 98] Address already in use
```

Why is the address in use after the process has been killed?

---

### Post by tbastian on 2010-05-31
Usually this happens because when you kill the process you don't close the port properly. This means that the OS still thinks you're using it. You need to wait for it to timeout. I'm not sure how to tell the OS to free it up for you...

---

### Post by dwhitney67 on 2010-05-31
Do something like this when you set up your socket:
```

sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

sock.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)

```
You really should find a way to terminate the server without sending it a kill signal, which it is obviously unprepared to handle.

---

