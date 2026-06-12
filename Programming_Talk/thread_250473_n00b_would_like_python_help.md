---
title: "n00b would like python help"
date: 2006-09-04
forum: Programming Talk
---

### Post by frup on 2006-09-04
I am doing chapter 13 of how to think like a computer scientist [http://www.ibiblio.org/obp/thinkCSpy/chap12.htm](http://www.ibiblio.org/obp/thinkCSpy/chap12.htm)

trouble is that the following code doesnt work and i have no idea why

```

import copy 

class Point:
  pass 
  
class Rectangle:
  pass 

def moveRect(box,dx,dy):
    newBox = copy.deepcopy(box)
    newBox.corner.x = newBox.corner.x + dx
    newBox.corner.y = newBox.corner.y + dy
    return newBox

    
bob = Rectangle()
bob.width= 100.0
bob.height = 200.0
bob.corner = Point()
bob.corner.y = 0.0
bob.corner.x = 0.0     

moveRect(bob,2,7)

print "X1 =",bob.corner.x
print "Y1 =",bob.corner.y

print "X2 =",newBox.corner.x
print "Y2 =",newBox.corner.y


```

line 28: print "X2 =",newBox.corner.x,name newBox is undefined.

but as you can see i have returned it and run the deep copy :S what am i doing wrong :(

---

### Post by Jussi Kukkonen on 2006-09-04
You try to use a moveRect local variable outside moveRect. You should be saving the return value and using that:
```
import copy

class Point:
  pass

class Rectangle:
  pass

def moveRect(box,dx,dy):
    newBox = copy.deepcopy(box)
    newBox.corner.x = newBox.corner.x + dx
    newBox.corner.y = newBox.corner.y + dy
    return newBox


bob = Rectangle()
bob.width= 100.0
bob.height = 200.0
bob.corner = Point()
bob.corner.y = 0.0
bob.corner.x = 0.0

bob2 = moveRect(bob,2,7)

print "X1 =",bob.corner.x
print "Y1 =",bob.corner.y

print "X2 =",bob2.corner.x
print "Y2 =",bob2.corner.y

```

---

### Post by frup on 2006-09-04
thankyou very much ;) i knew it would be something simple.

---

