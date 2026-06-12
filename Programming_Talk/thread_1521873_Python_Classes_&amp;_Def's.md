---
title: "Python: Classes &amp; Def's"
date: 2010-07-01
forum: Programming Talk
---

### Post by Chamillionaire2 on 2010-07-01
Ahoy Sailor!

```
class LoopingCall():
    def custom(self, interval=3, now=True):
        print "Sending!"
        self.sendLine('|abc|')
        self.sendLine('|def|')

class Echo(LineReceiver):
    
    def connectionMade(self):
        var = LoopingCall()
        print "Roger, Someones connected!"
        var.custom()
```

** After some hard hours of googling and reading tutorial I finally figured it out!

---

