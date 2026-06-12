---
title: "pygtkconsole.py program does not accept any input in ubuntu"
date: 2011-03-31
forum: Programming Talk
---

### Post by simar.mohar on 2011-03-31
Hi

I'm a beginner in pygtk and while I was reading the official tutorial here [http://www.pygtk.org/pygtk2tutorial/ch-Introduction.html#sec-ExploringPygtk](http://www.pygtk.org/pygtk2tutorial/ch-Introduction.html#sec-ExploringPygtk), I found this([http://www.pygtk.org/pygtk2tutorial/examples/pygtkconsole.py](http://www.pygtk.org/pygtk2tutorial/examples/pygtkconsole.py)) very effective program that can be very helpful for learning and experimenting with various widgets. But unfortunately this does not accept any input in ubuntu. I searched the internet but could not find any relevant answer or fix. I tried asking in ubuntu IRCs but all in vain.

Please let me know if there exist some remedy to make it work. If its in a official tutorial it must work in a popular OS such as ubuntu.

---

### Post by andrew1992 on 2011-03-31
How do you know it's not accepting your input? Perhaps it is accepting it, but not doing anything with it.  Post your code and the console output so we can determine what the actual problem is.

---

### Post by azhargiri on 2011-04-12
So do I. I run pygtkconsole.py on my Lucid. Then appear the prompt below :

> Python 2.6.5, PyGTK 2.17.0 (Gtk+ 2.20.0)
Interactive console to manipulate GTK+ widgets.
>>>

 I try to type some characters/commands, but the prompt doesn't response what I type. Any clue?

I think this tool is very helpful for me (and others, may be) as a newbie in python programming.

Thank's before.

---

### Post by matthewkurowski on 2011-04-13
I've confirmed your issue but am about to run for home.

For now, run your shell/environ and import pygtkconsole such as:

```
Python 2.6.6 (r266:84292, Sep 15 2010, 15:52:39) 
[GCC 4.4.5] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from pygtkconsole import gtk


```


Cheers

---

### Post by matthewkurowski on 2011-04-13
I don't mean to spam the thread with no real news but that pygtkconsole is in this state isn't a recent problem from a quick test on an old image that I had lying around from last year.

I'll dig in as soon as I can. It's probably something very simple.

---

### Post by matthewkurowski on 2011-04-13
I put some quick notes up on [my website]("http://matthew.kurowski.org/?page_id=223") 

I modified the pygtkconsole.py file quickly and tested the first tutorial. Everything worked great but keep in mind the limited testing (I did this over dinner, a beer and a mythbusters).

I don't have any more time right now, but I'll try to finish everything tomorrow and possible put some additional intelligence into the module.

For now, feel free to jump to my personal link above, or (better for the raw code) below. So sorry to have to jump and run.

---
Only test box:
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.10
Release:    10.10
Codename:    maverick

```
#!/usr/bin/env python
# -*- Mode: python; c-basic-offset: 4 -*-
#
# Interactive PyGtk Console, Johan Dahlin 2002 
# Kurowksi note; being tweaked for newer dists by mk, hopefully with some intelligence which I'll test on a few dists/platforms
#  
#
# from pygtkconsole (scratch)

import os
import signal
import sys
import string
import socket, select
from code import InteractiveInterpreter, InteractiveConsole
import gtk
import gobject

# For compatibility, instead of using GDK.INPUT_READ or
# gtk.gdk.INPUT_READ depending on the PyGtk version
# GDK_INPUT_READ = 1
gtk.gdk.INPUT_READ = 1

class Mainloop(InteractiveInterpreter):
    def __init__(self, read_fd, sock):
        InteractiveInterpreter.__init__(self)
        self._rfd = os.fdopen(read_fd, 'r')
        self._sock = sock
        gobject.io_add_watch(read_fd, gtk.gdk.INPUT_READ, self.input_func)
    def read_message(self):
        length = ord(self._rfd.read(1))
        return self._rfd.read(length)
    def input_func(self, fd, cond):
        data = self.read_message()
        more = self.runsource(data)
        self._sock.send(chr(more))
        return True
    def run(self):
        gtk.main()


class Console(InteractiveConsole):
    def __init__(self, write_fd, sock, pid):
        InteractiveConsole.__init__(self)
        self._wfd = os.fdopen(write_fd, 'w')
        self._sock = sock
        self.pid = pid
    def send_message(self, message):
        self._wfd.write('%c%s' % (len(message), message))
        self._wfd.flush()
    def interact(self, banner=None):
        InteractiveConsole.interact(self, banner)
        # Die child die
        os.kill(self.pid, 9)
    def runsource(self, source, filename):
        self.send_message(source)
        # wait for notification from parent
        select.select([self._sock],[],[])
        more = ord(self._sock.recv(1))
        return more


class GtkInterpreter(Console):
    def __init__(self):
        rfd, wfd = os.pipe()
        # set up socket for returning command result
        sigsock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock_addr = None
        for port in range(4321,5321):
            try:
                sigsock.bind(('', port))
                sock_addr = ('', port)
            except:
                pass
        if not sock_addr:
            print "Can't open socket"
        sigsock.listen(1)
        parent_pid = os.getpid()
        child_pid = os.fork()
        if not child_pid:
            # connect to command return socket
            sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
            sock.connect(sock_addr)
            g = Mainloop(rfd, sock)
            g.run()
        else:
            # Wait for command return socket connection
            sock, addr = sigsock.accept()
            Console.__init__(self, wfd, sock, child_pid)

def interact():
    try:
        import readline
        import rlcompleter
        readline.parse_and_bind('tab: complete')
    except ImportError:
        pass    
    gi = GtkInterpreter()
    gi.push("from gtk import *")
    python_version = string.split(sys.version)[0]
    pygtk_version = string.join(map(str, gtk.pygtk_version), '.')
    gtk_version = string.join(map(str, gtk.gtk_version), '.')
    banner = """Python %s, PyGTK %s (Gtk+ %s) Interactive console to manipulate GTK+ widgets.""" % (python_version, pygtk_version, gtk_version)
    gi.interact(banner)


if __name__ == '__main__':
    interact()

```

---

### Post by bkanuka on 2011-06-09
Hi Matthew,

Thank you for the help, but this doesn't work on Natty (at least for me).  I'd really like to use this as a learning tool. Do you think you could pull off another magic trick?

---

### Post by jfosorio on 2011-08-01
Hello, 
I have the same problem. It work for me with the changes proposed my Matthew. but you have to be careful of calling the program as he did: 
 python -i -v -t pygtkconsole.py | tee error.log
The last part is necessary otherwise the program does not work. 

Update: I tried with the old version using also: 
  python -i -v -t pygtkconsole_old.py | tee error.log
and It also works that way!!!. 
It seems that the all matter comes with the way the error messages are handle (But that is just my guess !!!). Those are my first steps with python. 
Regards 
Juan

---

### Post by ikem.krueger on 2012-04-23
> **jfosorio said:**
> You have to be careful of calling the program as he did:

```
python -i -v -t pygtkconsole.py|tee error.log
```

The last part is necessary, otherwise the program does not work! 

This is sufficient:

```
python -i pygtkconsole.py|tee /dev/null
```

Still don't know why..

---

