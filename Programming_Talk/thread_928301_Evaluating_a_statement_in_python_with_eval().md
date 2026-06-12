---
title: "Evaluating a statement in python with eval()"
date: 2008-09-23
forum: Programming Talk
---

### Post by Sagekilla on 2008-09-23
Hi all, I want to be able to evaluate a statement like so:

```
name = "foo"
eval(name) = "bar"
```

Where I'm trying to get what the value of name is (in this case, foo) and set a variable of that to bar. So I'd end up with foo = "bar" and if I type in print foo, I get 'bar' back.

Can anyone walk me through how to do this? I can't figure this out. Obviously I can't do it like in the example because you can't assign a value to a function, as python tells me.

---

### Post by ghostdog74 on 2008-09-23
i recommend you use dictionaries instead.

---

### Post by Sagekilla on 2008-09-23
I'm sorry could you elaborate on that a bit more? I don't know that much of python.

To elaborate more on my problem, I'm getting input from a file of a name. So I have a line of text that says: Circle c1

circle is the type of object, c1 is the name. I want to be able to set for any arbitrary number of objects, name = Function(). So from that file I get c1 = Circle()

---

### Post by Sagekilla on 2008-09-24
Anyone know a solution to my dilemma?

---

### Post by slavik on 2008-09-24
dictionaries ... please read the Python docs.

---

### Post by unutbu on 2008-09-24
[PHP]#!/usr/bin/env python
import sys
name = "foo"
setattr(sys.modules['__main__'],name,"bar")
print foo
[/PHP]

Output:
```

bar
```

[PHP]
#!/usr/bin/env python
import sys

class Circle():
    def __init__(self):
        print "Hi there!"

text = "Circle c1"
(clsname,name)=text.split()
setattr(sys.modules['__main__'],name,getattr(sys.modules['__main__'],clsname)())
print c1[/PHP]

Output:```


Hi there!
<__main__.Circle instance at 0xb7d2bbcc>
```

---

### Post by Sagekilla on 2008-09-24
Thank you all, it took some time but I've figured out how to use the dictionaries for my problem.

---

