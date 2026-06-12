---
title: "Python: Twisted"
date: 2010-09-21
forum: Programming Talk
---

### Post by Sailor5 on 2010-09-21
Ahoy Sailors!

So currently I've spawned a UI using easygui, Got your in putted text and now I'm needing to send it, But there's a problem```

class Echo(LineReceiver):
    
    def Menu():
      while 1:
       choice = buttonbox(msg='',choices=('Func','Func1'),root=None)
       if (choice=='Func'):
            outgoing = "Slam dunk the Func!"
       if (choice=='Func1'):
            outgoing = "Func1"
            
       sendLine(outgoing)       

    thread = Thread(target=Menu)
    thread.start()
```However as we can see, We can't say self.sendLine() because Menu() has no attribute of self. We also couldn't say thread.start(self) for the same reason. 

How could I fix this?

Thanks Bye!

---

### Post by Queue29 on 2010-09-21
Is Menu() supposed to be an instance method or a class method?

If it's an instance method, you should be accepting a variable called "self" in it:

```

def Menu(self):
    self.doStuff()

```

If it's a class method, you should have the @classmethod annotation before the method declaration. 

If you don't know what I'm talking about, buy a better python book.

---

