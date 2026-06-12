---
title: "python check this one out"
date: 2013-07-08
forum: Programming Talk
---

### Post by wingnut2626 on 2013-07-08
```
from sys import exit
    
class adder(object):
    def __init__(self):
        self.a = []
        self.item = []
        self.argument=0        
    def dictCopy(*args):
        pass
    def adder(self,*args):
        for item in args:
            print item
            raw_input()
            if type(item)!=int and type(item) != float:
                    print 'not a number'
                    if type(item) == list:
                        print item
                        self.item = item
                        listOccourance(self.item)
                    continue
            else:
                self.a.append(item)
                print self.a
        print sum(self.a)
    def listOccourance(self, argument):
        self.argument = argument
        print self.argument
        print 'It seems that you have a list in here. How do you want to handle that?'
        print 'Press 1 to nest this list.\n Press 2 to take the sum thus far and append that to the list.'
        print 'Press 3 to do nothing.'
        choice = raw_input()
        if choice == 1:
            self.a.append(self.argument)
            print self.a
            raw_input()
        elif choice == 2:
            self.argument.append(sum(self.a))
            print self.argument
            raw_input
            exit(0)
        elif choice == 3:
            #this will default to back to list a
            pass    


```no matter how I code this, I cannot get self.argument  to append to self.a correctly.

---

### Post by wingnut2626 on 2013-07-08
here is a sample of it running:>>> reload(adder)
<module 'adder' from 'adder.py'>
>>> d=adder.adder()
>>> d
<adder.adder object at 0x01B61F50>
>>> d.adder(45,32,22,34,45,67,b,34,23)
45
[45]
32
[45, 32]
22
[45, 32, 22]
34
[45, 32, 22, 34]
45
[45, 32, 22, 34, 45]
67
[45, 32, 22, 34, 45, 67]
[119, 210, 126, 9, 284, 154, 162, 262, 38, 20]
not a number
[119, 210, 126, 9, 284, 154, 162, 262, 38, 20]
It seems that you have a list in here. How do you want to handle that?
Press 1 to nest this list.
 Press 2 to take the sum thus far and append that to the list.
Press 3 to do nothing.
1
34
[45, 32, 22, 34, 45, 67, 34]
23
[45, 32, 22, 34, 45, 67, 34, 23]
302
>>>

---

### Post by trent.josephsen on 2013-07-08
Take a closer look at this:
> **wingnut2626 said:**
> 
```
        choice = raw_input()
        if choice == 1:
```

---

### Post by alan9800 on 2013-07-09
as explained [here]("http://docs.python.org/release/2.7.3/library/functions.html#raw_input"), raw_input returns a string, hence you have to convert that string into an int as follows```
choice = int(raw_input())
```

---

