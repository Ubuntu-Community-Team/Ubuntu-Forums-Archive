---
title: "[Python] cast base class to derived class"
date: 2008-08-01
forum: Programming Talk
---

### Post by raccoonone on 2008-08-01
I'm trying to do something like this:
```
b = Base()
#do some stuff to b here
d = Derived(b)
```
would this be the best (or even a workable) way to do it?
```

class Base:
  def __init__(self):
    self.x = "some variable"
class Derived(Base):
  def __init__(self, b=None):
    Base.__init__(self)
    if b:
      self.__dict__.update(b.__dict__) # copy instance variables
    self.y = "some more variables in derived class"  
```

---

### Post by NovaAesa on 2008-08-02
That's more or less how I would do it in Java, not sure how well it would go in Python though. The best way of finding it out would be to give it a try (or wait til a Python guru comes along :P).

---

### Post by raccoonone on 2008-08-02
I gave it a try and it works in that simple case, but not how I actually want to use it. I'm trying to extend the socket.socket class like this:
```

class NonBlockingSocket(socket.socket):
    """provides a non-blocking socket.
     extention of socket.socket"""
    def __init__(self, sock=None):
        socket.socket.__init__(self)
        if sock:
            self.__dict__.update(sock.__dict__)
        self.setblocking(0)
```
However, when I do that I get an error that __dict__ is not a member of _socketobject. Any suggestions?

---

### Post by raccoonone on 2008-08-03
bump. anyone?

---

### Post by nvteighen on 2008-08-03
Hmm... In the Python console, if I do:
```

>>> import socket
>>> dir(socket.socket)
['__class__', '__delattr__', '__doc__', '__getattribute__', '__hash__', '__init__', '__module__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__slots__', '__str__', '__weakref__', '_sock', 'accept', 'bind', 'close', 'connect', 'connect_ex', 'dup', 'family', 'fileno', 'getpeername', 'getsockname', 'getsockopt', 'gettimeout', 'listen', 'makefile', 'proto', 'recv', 'recv_into', 'recvfrom', 'recvfrom_into', 'send', 'sendall', 'sendto', 'setblocking', 'setsockopt', 'settimeout', 'shutdown', 'type']

```

I see no __dict__ for socket.socket...

---

### Post by pmasiar on 2008-08-03
Why you feel urge to cast? Duck typing allows you to use properly named methods even if instance is not of a base or derived class. It is Python, not Java :-)

---

### Post by LaRoza on 2008-08-03
> **pmasiar said:**
> Duct typing allows you to use properly named methods even if instance is not of a base or derived class. 

Duck, I think. This isn't tape :-)

---

### Post by Wybiral on 2008-08-03
> **nvteighen said:**
> I see no __dict__ for socket.socket...

Yes, what's happening here is the difference between old-style and new-style classes.

```

class Test1(object):
    pass

class Test2:
    pass

print dir(Test1)
print dir(Test2)

```

It seems that socket.socket uses the old-style classes and doesn't inherit from "object".

EDIT:

BTW, you can't "cast" anything in Python... You can only call something that returns something else :)

---

### Post by raccoonone on 2008-08-04
I looked into duck typing and it doesn't sound like it would help me in this case. I'll explain my problem in more detail. I have a NonBlockingSocket class which inherits from socket.socket and it adds some extra functionality. Now I'm getting sockets from the socket.socket.accept function, and I would like to turn them into NonBlockingSockets. Is there an easy way to do this?

---

### Post by catchmeifyoutry on 2008-08-04
> **raccoonone said:**
> I looked into duck typing and it doesn't sound like it would help me in this case. I'll explain my problem in more detail. I have a NonBlockingSocket class which inherits from socket.socket and it adds some extra functionality. Now I'm getting sockets from the socket.socket.accept function, and I would like to turn them into NonBlockingSockets. Is there an easy way to do this?

I would just create NonBlockingSocket as a wrapper object around socket.socket, thus keep a variable self._socket in NonBlockingSocket to maintain the original socket.socket object.
Then define member functions for NonBlockingSocket for altered behavior w.r.t. socket.socket.
And for normal (unaltered) behavior you could define a __getattr__ function in NonBlockingSocket to directly call the corresponding socket.socket member.
From the top of my head:
[PHP]

class NonBlockingSocket (object):
  def __init__(self, socket):
     self._socket = socket

  def do_foobar(self, arg1):
     # some alter behavior here
     # possibly call original method eventually:
     self._socket.do_foobar(arg1)

  def __getattr__(self, var):
     # for non altered functions, properties
     # just do what _socket would do
     return self._socket.__getattr__(var)

[/PHP]

Funny thing is, I used this approach for a similar connection problem (I wanted a automatically reconnecting FTP object that extended some module's normal FTP object). This approach worked for me.
But write some test cases to ensure that you don't get any strange side effects later on!

---

### Post by raccoonone on 2008-08-04
The problem that I had with storing a _socket member was that I want to be able to pass my NonBlockingSocket to functions like select.select, I'll try __getattr__ it seems like that would fix my problem. Thanks!

---

