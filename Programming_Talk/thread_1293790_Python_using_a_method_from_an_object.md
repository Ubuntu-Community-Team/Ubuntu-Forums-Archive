---
title: "Python using a method from an object"
date: 2009-10-17
forum: Programming Talk
---

### Post by McWeirdo on 2009-10-17
Hi, I've recently came across a problem,I am programming and C# and kinda new in Python.
 
now I had to do a recursive function that gets a string and reoves all 'X' chars in that string , I've done it in both C# and python, but to test how Classes work I've done the following thing:
 
```
 
Class C:
    def removeX(self,string1):
         # here are a bunch of statements
         # they return the string without the 'x' in the end..
 
obj1=C()
xz=obj1.removeX('XXXXLSLXXOLSXLXL")
print xz
 
 
 

```
it didn't work, I think I'm miss understnading the self thing, cause in C# it works , I mean I know that code is pointless cause I don't need to do a class , but that was just for testing accesing functions in an object... if the function is not inside a class , it works, so it's not the problem in the func...
 
What's the problem?
 
thank you :D

---

### Post by CptPicard on 2009-10-17
The issue seems to be in the code of the function... care to post it?

---

### Post by Can+~ on 2009-10-17
I also would like to see the code inside the RemoveX method.

btw:

[PHP]>>> "XXHelloXWorldXXX!".replace("X", "")
'HelloWorld!'[/PHP]

---

### Post by McWeirdo on 2009-10-17
Well i doubt if it's a problem in the code , cause when I run it without makin it inside a class it runs ok, will post it though in a minute, and I\m aware of the replace thing, but this question is meant for C# which AFAIK doesn't have this option, but it's nice to see the algorithm behind it, so 1 min and ill post the code.
 
thanks

---

### Post by McWeirdo on 2009-10-17
```
 
class C:
 
   def nox(self,string1):
            if string1.find('x')==-1:
                  return string1 
            else:
                  return nox(string1[:string1.index('x')]+string1[string1.index('x')+1:])
 
 
obj=C()
print obj.nox("XLXOLXXLOLX")
 
output:says i have a problem with obj=C()

```
when i run the function wuthout writing it in the class it's fine

---

### Post by McWeirdo on 2009-10-17
the problem with obj=c() is a mistake, I had a "space" before the statement, but the error is still there it says:
global name nox is not defined...

---

### Post by diesch on 2009-10-17
It has to be
```
return self.nox(...)
```
instead of
```
return nox(...)
```

---

### Post by Can+~ on 2009-10-17
When calling methods from inside the class, use the "self" keyword. This is pretty much like the "this" in C# and Java.

[PHP]class C:
	def nox(self,string1):
		if string1.find('x') == -1:
			return string1 
		else:
			return self.nox(string1[:string1.index('x')]+string1[string1.index('x')+1:])

obj = C()
print obj.nox("XLXOLXXLOLX")[/PHP]

Edit: diesch beat me.

---

### Post by McWeirdo on 2009-10-17
Thank You both :)
 
I just want to undrstand what's the point of the self. , cause on C# i don't have to do this.nox in the return statement, so what does it do? informs Mr Python that the method is inside the class?
 
 
Thanks again :D

---

### Post by diesch on 2009-10-17
It's about the same as with obj.nox: It tells Python you want to use self's method. 

In contrast to most other languages Python doesn't use the class as default namespace here.

---

### Post by wmcbrine on 2009-10-17
[http://effbot.org/pyfaq/why-must-self-be-used-explicitly-in-method-definitions-and-calls.htm](http://effbot.org/pyfaq/why-must-self-be-used-explicitly-in-method-definitions-and-calls.htm)

---

### Post by McWeirdo on 2009-10-18
Thank you all~!#!#!

---

### Post by nvteighen on 2009-10-18
The idea is to preserve interface-integrity: Only stuff included in the function's parameters list should affect the function's behaivor. So, that's why self is there.

---

