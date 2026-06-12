---
title: "Python Class"
date: 2009-05-12
forum: Programming Talk
---

### Post by matmatmat on 2009-05-12
I'm trying to create an address book class:
```

class addressBookEntry(object):
    def _init_(self, nm, nn="", ph="", em=""):
        self.name = nm
        self.nick = nn
        self.number = ph
        self.email = em
    def updatePhone(self, newph):
        self.number = newph
    def updateEmail(self, newem):
        self.email = newem
    def printAll(self):
        print "%s\t%s\t%s\t%s" % (self.name, self.nick, self.number, self.email)

james = addressBookEntry("james")
jil.printAll()

```
It says:
```

matio@matio-desktop:~/Documents/Python$ python addressbook.py 
Traceback (most recent call last):
  File "addressbook.py", line 14, in <module>
    james = addressBookEntry("james")
TypeError: object.__new__() takes no parameters

```
Don't you use _init_ and specify parameters like I've done?

---

### Post by dandaman0061 on 2009-05-12
It looks like your 'init' method only has single underscores before and after the 'init'.  It needs double underscores.
```

_init_
# change to
__init__

```

---

### Post by matmatmat on 2009-05-12
Thanks

---

### Post by matmatmat on 2009-05-12
...

---

