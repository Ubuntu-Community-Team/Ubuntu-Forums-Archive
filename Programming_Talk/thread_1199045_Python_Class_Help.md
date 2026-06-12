---
title: "Python Class Help"
date: 2009-06-28
forum: Programming Talk
---

### Post by DeadRobot on 2009-06-28
I've written a simple class:
```

FILES = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h']
RANKS = ['1', '2', '3', '4', '5', '6', '7', '8']

class Location:
	def __init__(self, x, y):
		self.x, self.y = x, y
	
	def getAlgNot():
      notation = ''
		notation += FILES[self.x-1] + RANKS[self.y-1]
		return notation
				
if __name__ == '__main__':
	loc = Location(4,5)
	print loc.getAlgNot()


```

A Location represents a square on a chess board.  It has an x and a y coordinate.  
The bottom left square is (0,0).  In Algebraic chess notation, this square is a1.  

In main, I have created a Location at (4,5).  The Algebraic notation should be e6.

The method getAlgNot() is supposed to take the coordinates and turn it into an algebraically notated space.

So it would take (4,5) and return e6.

When I run this I get this error:
```

Traceback (most recent call last):
  File "chess.py", line 23, in <module>
    print loc.getAlgNot()
TypeError: getAlgNot() takes no arguments (1 given)
```

I'm not really sure how to fix this.  Any insight?
Thanks.

---

### Post by simeon87 on 2009-06-28
All normal functions in a class have at least one parameter, namely self. This is the object that the function is operating on. Example:

```

class Foo:
  def bar(self):
    print "lala"

x = Foo()
x.bar()

```

This means the function bar is called with x as argument (so x, an instantiation of the class Foo, is passed as first parameter to bar). So, adding self as parameter should fix your problem.

---

### Post by Can+~ on 2009-06-28
Whenever you call a method inside a class, it will handle the [FONT="Courier New"][COLOR="DeepSkyBlue"]self[/COLOR][/FONT] reference (this or this* to C++/Java programmers). So you must add a self argument on the function.

Also, I would move those global variables to "inside the class".

---

### Post by DeadRobot on 2009-06-28
Thank you guys so much!

I just started learning Python classes today and I'm a tad bit confused...but I think I'll get the hang of it eventually.

---

### Post by Can+~ on 2009-06-28
[PHP]#!/usr/bin/python

class Chesspiece:
	# Class variables
	files = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h']
	ranks = [str(i) for i in xrange(1,9)]
	
	def __init__(self, x, y):
		#Instance variables
		self.x = x
		self.y = y
	
	def __str__(self):
		return Chesspiece.files[self.x] + Chesspiece.ranks[self.y]

mypiece = Chesspiece(4, 5)
print mypiece[/PHP]

Notice the overloading on the __str__ method.

*edit: Now that I come to think it, it's redundant to have a list of characters, that's pretty much a string:

[PHP]
class Chesspiece:
	# Class variables
	files = "abcdefgh"
	ranks = "".join(str(i) for i in xrange(1,9))
	
	def __init__(self, x, y):
		#Instance variables
		self.x = x
		self.y = y
	
	def __str__(self):
		return Chesspiece.files[self.x] + Chesspiece.ranks[self.y]

piece1 = Chesspiece(4, 5)
piece2 = Chesspiece(2, 3)

print piece1, piece2

#Let's overload the father's lettering
Chesspiece.files = "ijklmnopq"

print piece1, piece2
[/PHP]

---

