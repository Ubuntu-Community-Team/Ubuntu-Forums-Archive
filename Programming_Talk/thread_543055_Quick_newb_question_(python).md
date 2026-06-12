---
title: "Quick newb question (python)"
date: 2007-09-04
forum: Programming Talk
---

### Post by triptoe on 2007-09-04
my question is... when I fire up the interactive python interpreter... i import my file but it doesn't work right. for instance here is my code:

```
#! /usr/bin/env python
# linked lists

class Node:
        def __init__(self, cargo=None, next=None):
                self.cargo = cargo
                self.next = next

        def __str__(self):
                return str(self.cargo)

     

node = Node("test")
print node

```

when i type at the commandline: python

and then it brings up the interpreter... then i type: import nodes (the filename is nodes.py)

it prints test correctly. However when i try to interact with it like declare another node:

node1 = Node(1) it screams at me and tells me Node is undefined

> Python 2.5.1 (r251:54863, May  2 2007, 16:56:35) 
[GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import nodes
test
>>> node1 = Node(1)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'Node' is not defined
>>> 


---

### Post by Tuna-Fish on 2007-09-04
try node1 = nodes.Node(1)

import doesn't invade the main namespace by default.

---

### Post by triptoe on 2007-09-04
> **Tuna-Fish said:**
> try node1 = nodes.Node(1)

import doesn't invade the main namespace by default.

ah TY. that makes sense.. One more question if anyone knows...

How do i escape space?

Like if i use concatenation it escapes space.. but if i use a comma it adds a space.
but i want to do something like this:

```

print "[",
while node:
    print str(node) + ",",

print "]"
```

it looks like this [ 1, 2, 3, 4 ]
but i want it to look [1,2,3,4]

do i have to use if statements and test for the begginning and ends off the string and use concatenation?

---

### Post by bashologist on 2007-09-04
Like this?
```
>>> print "no", "\b unwanted whitespace";
```

---

### Post by pmasiar on 2007-09-04
"print x, " adds space. Use list comprehension to build one list:

print ''.join(str(x) for x in node)

''.join(listexpression) is idiomatic way to build one string (joining using empty string - you can put any separator you want).

Google for "Python idioms".

I know I should add them to my wiki but I am so swamped... :-(

---

