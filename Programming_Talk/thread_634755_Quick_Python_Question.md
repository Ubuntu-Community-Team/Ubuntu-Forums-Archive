---
title: "Quick Python Question"
date: 2007-12-08
forum: Programming Talk
---

### Post by thenetduck on 2007-12-08
How do you define Public / Private class / def in Python? 

I am confused about how Python handles this. 

Thanks!

The Net Duck

---

### Post by Compyx on 2007-12-08
AFAIK Python doesn't really provide a private/public distinction for class methods and objects like C++ or Java, the closest you can get is [this]("http://docs.python.org/tut/node11.html#SECTION0011600000000000000000").

---

### Post by Martin Witte on 2007-12-08
you can have private methods as well, see [http://www.diveintopython.org/object_oriented_framework/private_functions.html](http://www.diveintopython.org/object_oriented_framework/private_functions.html)

---

### Post by LaRoza on 2007-12-08
For private data, name the method or variable with a leading underscore.

(Posted edited to fix error)

---

### Post by pmasiar on 2007-12-08
Not exactly. Private data (it is just convention, you can still access them) have single underscore. Double underscore adds "name mangling" (see google), when inherited, not sure if OP was asking for that.

---

### Post by slavik on 2007-12-08
heh, same object orientation principle as in C ... neat. :)

---

### Post by Wybiral on 2007-12-08
> **slavik said:**
> heh, same object orientation principle as in C ... neat. :)

Well, double underscore isn't much different than private in C++ (it mangles it).
```

class obj:
    def __init__(self):
        pass
    def __method(self, data):
        print(data)
    def method(self, data):
        self.__method(data + " world!")

o = obj()
o.method("Hello")

# Error:
o.__method("Hello world!")

```

But no, Python doesn't have any sort of "protected", it's just understood that a single underscore is meant to be protected (but not enforced).

---

### Post by pmasiar on 2007-12-08
"Protected" as in: "I expect you stay out of my living room because I asked you and you are decent person, not because I have shotgun". 

Programmers are consenting adults, and if you mess with private variables, and something blows into your face, you have only yourself to blame (and you know it). But if you know what you are doing and need access to private variables  and do it right (and you are prepared to maintain code changes in future releases), no problems. You are free to shoot very close to your feet if you want to. :-)

---

