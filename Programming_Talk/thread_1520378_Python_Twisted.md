---
title: "Python: Twisted"
date: 2010-06-29
forum: Programming Talk
---

### Post by Chamillionaire2 on 2010-06-29
A-hoy hoy!

Basically I need to be able to use the sendLine() function when the definition is not under a LineReceiver class. Here's an example of what I mean.

```
def custom():
    self.sendLine('text')

class EchoClient(LineReceiver):
  def connectionMade(self):
     custom()
```

But of course that won't work because sendLine is not under the Class EchoClient bit, How could I make this work?

Thanks Bye!

---

### Post by soltanis on 2010-06-29
[php]
def custom(obj):
    obj.sendLine('text')

class EchoClient(LineReceiver):
  def connectionMade(self):
     custom(self)
[/php]

Hooray object references?

---

### Post by Chamillionaire2 on 2010-06-29
> **soltanis said:**
> [php]
def custom(obj):
    obj.sendLine('text')

class EchoClient(LineReceiver):
  def connectionMade(self):
     custom(self)
[/php]

Hooray object references?

That works however if the sendLine is in a while loop, For some reason it won't send any text.

---

### Post by soltanis on 2010-06-29
Might be buffering or could be a code error. Can I see the relevant loop?

---

### Post by -grubby on 2010-06-29
If you need to share instance variables with that function it should probably be under the class definition. As demonstrated above you can also pass the class instance (self) to the function.

---

