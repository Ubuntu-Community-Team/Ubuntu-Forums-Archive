---
title: "Beginning Python"
date: 2007-06-25
forum: Programming Talk
---

### Post by era86 on 2007-06-25
Ubuntu

I am starting to learn Python by reading some online books and I am on the part about classes.  Now, I have programmed in C++ many a times so I could just be making a syntactical error with what I'm trying to do.

I want to make a class, Square, with the following methods:
changeHeight
changeWidth
area

and two member variables
height
width

So I have this:

class Square:

	def changeHeight( newHeight ):
		height = newHeight

	def changeWidth( newWidth ):
		width = newWidth

	def area():
		return height * width

	def __init__( self, height = 0, width = 0 ):
		if ( type( height ) == type( 0 ) and type( width ) == type( 0 ) ):
			self.height = height
			self.width = width

Now I try to use 
>>> sqr = Square()
>>> sqr.changeWidth(5)

and it gives an error about having more than one argument.  Any help would be nice!  Thanks!

---

### Post by pmasiar on 2007-06-25
1) methods in Python need instance reference, by convention called self:

```

    def changeHeight(self, newHeight):
        self.height = newHeight

```

2) Python is usually not anal about protecting properties: instead of getters and setters, you just assign. It's called "programmers are consenting adults", but of course you can do setters if you need them.

3) Code, and especially Python code, looks better aligned, use [ code ] tags

4) "Dive into Python" is book for experienced programmers - try it. Wiki in my sig had many links for Python learners - try pythonchallenge: up to 3 months of increasingly more complicated python tasks to solve.

enjoy!

---

### Post by era86 on 2007-06-26
pmasiar

Thank you so much for your help!  I will definately look into the readings you mentioned.  The book I am currently reading is very basic and many of the techniques are general programming tricks and tips.

era

---

