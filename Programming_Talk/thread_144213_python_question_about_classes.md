---
title: "python question about classes"
date: 2006-03-13
forum: Programming Talk
---

### Post by krypto_wizard on 2006-03-13
I have following two classes
```

## file_A.py
class A(object):
    ## a contains isntances of A
    a= [ ]
    def __init__(self, node):
        self.nodes_in_A = []
        self.nodes_in_A.append(node)
        packet_queue = [ ]
        ...etc
## file_B.py
import A
class B(object):
    ## n contains instances of B
    n = [ ]
    def some_func(self):
        _len = len (A.A.a[0].packet_queue) 

```

I get an error AttributeError: 'A' object has no attribute 'packet_queue'


Can you please explain me ...why ? and How to fix this ?

---

### Post by thumper on 2006-03-14
Are you expectng A.a to be a member variable or a static variable?

You are missing self. for packet_queue in class A, so it is thought to be a local variable in __init__.

---

### Post by krypto_wizard on 2006-03-14
static variable...


[QUOTE=thumper]Are you expectng A.a to be a member variable or a static variable?

You are missing self. for packet_queue in class A, so it is thought to be a local variable in __init__.[/QUOTE]

---

### Post by thumper on 2006-03-14
My first question is why would you want to do that?

I am assuming that somewhere in the body of the A.__init__ method, self is getting appended into A.a
If you are going to index into a static list then you probably want to check the length first (unless you know that there is something in there).
You also don't need the first A.
Assuming that A.a contains instances of A, and that packet_queue is a member of A, then
```
len(A.a[0].packet_queue)
```should be sufficient.

However I do query your use of static variables here to store instances of the class.

---

### Post by krypto_wizard on 2006-03-15
I realized what you are saying but I guess bad design of code or inability to think how to pass objects around has made me do this.




[QUOTE=thumper]My first question is why would you want to do that?

I am assuming that somewhere in the body of the A.__init__ method, self is getting appended into A.a
If you are going to index into a static list then you probably want to check the length first (unless you know that there is something in there).
You also don't need the first A.
Assuming that A.a contains instances of A, and that packet_queue is a member of A, then
```
len(A.a[0].packet_queue)
```should be sufficient.

However I do query your use of static variables here to store instances of the class.[/QUOTE]

---

