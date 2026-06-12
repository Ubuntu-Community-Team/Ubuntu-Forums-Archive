---
title: "Python Libraries question"
date: 2006-05-04
forum: Programming Talk
---

### Post by krypto_wizard on 2006-05-04
I am using python on a linux terminal.

I want to shutdown a remote windows box. I found a script which does
something like this. My question is can we use windows libraries in
linux as follows ....

import win32api
import win32con
import win32netcon
import win32security
import win32wnet

def shutdown(parameters):
    OTHER CODE HERE

Every help is appreciated.

---

### Post by unbuntu on 2006-05-04
pywin32 just won't run under Linux AFAIK.

---

### Post by cwaldbieser on 2006-05-05
[QUOTE=krypto_wizard]I am using python on a linux terminal.

I want to shutdown a remote windows box. I found a script which does
something like this. My question is can we use windows libraries in
linux as follows ....

import win32api
import win32con
import win32netcon
import win32security
import win32wnet

def shutdown(parameters):
    OTHER CODE HERE

Every help is appreciated.[/QUOTE]

Unbuntu is correct.  The win32* python libraries call into various Win32 API DLLs in order to work.  Since the Win32 DLLs are not on your Linux box, the python libraries can't work.

---

### Post by thumper on 2006-05-05
The problem of trying to use a linux box to control a windows box is the lack of DCOM (not that you really want to use it anyway).

My suggestion is to write a service on the windows box that you need to control, and have the linux box talk to that service using CORBA / ICE / or plain TCP.  That way the service running on the windows box has full access to the API for the local machine.

---

### Post by krypto_wizard on 2006-05-05
I went to this webpage

[http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/360649]("http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/360649")

Isn't it supposed to run on the network and close the connected machine.

Every help is appreciate,

---

### Post by cwaldbieser on 2006-05-05
[QUOTE=krypto_wizard]I went to this webpage

[http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/360649]("http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/360649")

Isn't it supposed to run on the network and close the connected machine.

Every help is appreciate,[/QUOTE]
This line sums it up:
```

""" Shuts down a remote computer, requires NT-BASED OS. """

```
Thumper is right-- you are better off just running a simple server on the Windows box you can communicate with.  The server can shut down the box locally.  The standard library has a simple XMLRPC server you could use, or you could even just set up your own ulta-smple server with a socket.  If you want to be more fancy, you could look into a framework like Twisted.

---

