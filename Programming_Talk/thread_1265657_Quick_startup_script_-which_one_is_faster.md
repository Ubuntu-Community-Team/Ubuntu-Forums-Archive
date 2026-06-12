---
title: "Quick startup script -which one is faster?"
date: 2009-09-13
forum: Programming Talk
---

### Post by froggyswamp on 2009-09-13
Folks,
I need to create a script that connects to say localhost:9898 and sends a string, if there's nobody listening then start a given executable (a Java file manager for those interested) instead with that string as param.

Since this is to run on Ubuntu, best options are (I think) either a bash or a python script.

Question is, how do you think, which script will startup _and_ execute faster: python or bash?

(I don't know either bash nor python.)

---

### Post by Habbit on 2009-09-13
> **froggyswamp said:**
> Folks,
I need to create a script that connects to say localhost:9898 and sends a string, if there's nobody listening then start a given executable (a Java file manager for those interested) instead with that string as param.

Since this is to run on Ubuntu, best options are (I think) either a bash or a python script.

Question is, how do you think, which script will startup _and_ execute faster: python or bash?

(I don't know either bash nor python.)

If you can use standard utilities like telnet, then probably a _sh_ (not bash, but sh, which in ubuntu means dash, a small performance-oriented POSIX shell) script will be faster than a full-fledged python script, but YMMV... Do both and time them ;)

---

### Post by froggyswamp on 2009-09-13
Thanks,
I can't do "both" because I don't know either, only Java, so based on feedback I'll choose which one to learn and then implement. Basically since connecting to a socket and sending a small string on localhost should happen in a blink of an eye, I think in the end it all boils down to "does an sh script start faster then a python one?" and, is the difference bigger than half a second or not. If the difference is under half a second then I'm going with python.

---

### Post by falconindy on 2009-09-13
Shell scripts will always be faster than loading extra libraries to run another language. Will the difference between shell and python be noticeable enough for you to care? Probably not.

---

### Post by linkmaster03 on 2009-09-13
You won't notice the difference. I'd do it in Python. This will probably work if you just need precisely what you explained in the first post:

```
#!/usr/bin/env python

import socket
import subprocess

string = 'data'
program = '/path/to/java_file_manager'

chat = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
try:
    chat.connect(('localhost', 9898))
    chat.send(string)
    print('Sent data successfully!')
except socket.error:
    subprocess.Popen(program, shell=True)
    print('Couldn\'t send data, started program instead.')

```

Learn from it! :D

---

### Post by Habbit on 2009-09-13
Doesn't AF_INET limit you to IPv4? Why not use the "I don't care" option (AF_UNSPEC, iIrc) instead?

---

### Post by linkmaster03 on 2009-09-13
I suppose you are right. I don't use IPv6 so it didn't occur to me. The topic creator can check out the [socket docs](http://docs.python.org/library/socket.html) if they decide to use Python for this task and use IPv6. It seems a bit more complicated than using IPv4, so I won't modify the snippet above.

---

### Post by froggyswamp on 2009-09-13
> **linkmaster03 said:**
> You won't notice the difference. I'd do it in Python. This will probably work if you just need precisely what you explained in the first post:

```
#!/usr/bin/env python

import socket
import subprocess

string = 'data'
program = '/path/to/java_file_manager'

chat = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
try:
    chat.connect(('localhost', 9898))
    chat.send(string)
    print('Sent data successfully!')
except socket.error:
    subprocess.Popen(program, shell=True)
    print('Couldn\'t send data, started program instead.')

```

Learn from it! :D

wow! thank you very much!..

---

