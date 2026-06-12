---
title: "Begining python question, returning an object"
date: 2007-03-06
forum: Programming Talk
---

### Post by Ramses de Norre on 2007-03-06
Today I started looking into python a bit, after reading many good things about it.
I now have my first question about it, I wrote this little class:
```
#!/usr/bin/env python

class Complex:
	"""Class to represent complex numbers"""
	a=0;b=0
	
	def __init__(self,a,b):
		"""Constructor
			Takes two numbers as arguments, 
			the first is the real part of the complex number, 
			the second the imaginary one."""
		self.__setReal__(a)
		self.__setImaginary__(b)
	
	def getReal(self):
		"""Getter for the real part of this complex number"""
		return self.a
	
	def getImaginary(self):
		"""Getter for the imaginary part of this complex number"""
		return self.b
	
	def __setReal__(self,a):
		"""Setter for the real part of this complex number"""
		self.a=a
		
	def __setImaginary__(self,b):
		"""Setter for the imaginary part of this complex number"""
		self.b=b
		
	def addTo(self,obj):
		"""Returns a new object that is the complex sum of self and obj"""
		return Complex(self.getReal()+Complex(obj).getReal(), self.getImaginary()+Complex(obj).getImaginary())

        def toString(self):
		"""Returns a string representation of this object"""
		return `self.getReal()`+"+"+`self.getImaginary()`+'i'


"""Driver"""	
b=Complex(5,4)
print b.toString()
c=Complex(6,8)
print c.toString()
d=b.addTo(c)
print d.toString()
```
And I get this error when running it: > [COLOR="Red"]Traceback (most recent call last):
  File "/home/ramses/code/java/workspace/FirstPythonTest/src/first/complex.py", line 45, in ?
    d=b.addTo(c)
  File "/home/ramses/code/java/workspace/FirstPythonTest/src/first/complex.py", line 33, in addTo
    return Complex(self.getReal()+Complex(obj).getReal(), self.getImaginary()+Complex(obj).getImaginary())
TypeError: __init__() takes exactly 3 arguments (2 given)[/COLOR]
5+4i
6+8i

Why does it tell me to give three arguments to the constructor?? The first (self) is the object it creates, isn't it? How am I supposed to give that as an argument? And the same construction seems to work in the little driver code?

Can anyone point out what I'm missing?
Ow and I have programming and OOP experience, so I can understand decent explanations.

---

### Post by WW on 2007-03-06
When you say Complex(obj), you are calling the constructor with just one argument (which will become two when self is added).

---

### Post by WW on 2007-03-06
Change the line in addTo to
```

return Complex(self.getReal()+obj.getReal(), self.getImaginary()+obj.getImaginary())

```
and your program works.

---

### Post by Ramses de Norre on 2007-03-06
So no form of typecasting? This seems so unsafe?
Maybe I need to get used a bit more to this dynamic typing stuff... Thanks for helping me out ;)

---

