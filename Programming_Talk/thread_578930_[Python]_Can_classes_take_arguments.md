---
title: "[Python] Can classes take arguments?"
date: 2007-10-17
forum: Programming Talk
---

### Post by Nekiruhs on 2007-10-17
For the sake of learing, I'm writing new classes that reimplement and supply new features to the built in classes. But I have a question. I have a class called matrix, which is essentially a list with multiple columns and rows. I was wondering if when I instantiate the class, I can pass an argument to it so the __init__ function knows how big to start the Matrix. If it helps, heres the relevant code:

[PHP]class Matrix(Type):
	 def __init__(self):
            self.type = "Matrix"
            self.private = False #TODO: Implement private/public type variables and accessor functions          
            self.value = [
            			  [],
            			  [],
            			  [],
            			 ] #Defines the dimensions of the Matrix. Defaults to 3.
	def expand(size):
		for x in size:
			self.value.append([])
	
	def add(value, row):
		self.value[row].append(value)[/PHP]Type is a base class I defined with just some basic functions like delete, duplicate and the such.

I want to use it in this manner:
[PHP]size = 5
newInstance = Matrix(size)[/PHP]
And it starts with 5 columns.

Any help?

---

### Post by foxylad on 2007-10-17
Class instantiation can take arguments - just add arguments to the __init__() class member function. See [http://docs.python.org/tut/node11.html](http://docs.python.org/tut/node11.html).

---

### Post by Jessehk on 2007-10-17
The purpose of the __init__ method is to initiate the class with specific arguments. What you're asking is almost equivelent to: "I love my car's air-conditioning, but is there a way to travel somewhere?". ;)

For example:
```

class Person(object):
    def __init__(self, name, age):
        self.name = name
        self.age = age

person = Person("Joe", 25)

print "%s is %s years old." % (person.name, person.age)

```

Here, the __init__ method of the Person class takes two arguments that allow you to customize the object.

---

### Post by LaRoza on 2007-10-18
To the OP, member functions take "self" as the first argument, you don't have to pass it when you call the function, however. You don't have to use "self", but do so anyway.

---

### Post by pmasiar on 2007-10-18
> **LaRoza said:**
> To the OP, member functions take "self" as the first argument, you don't have to pass it when you call the function, however. You don't have to use "self", but do so anyway.

member "functions" are called methods in OOP. And you do pass 'self' to method: when you call a method of an instance, that instance is passed as 'self'. Call it trickery or magic, but it is just a syntax sugar.

---

### Post by LaRoza on 2007-10-18
> **pmasiar said:**
> member "functions" are called methods in OOP.

OK, methods then. Functions, methods, precedures, subroutines, are all the same to me, if the language makes no distinctions.

---

### Post by pmasiar on 2007-10-18
Well, "method" is proper name for the concept, and language DOES make distinction: method has to have 'self' as first argument (which you do not pass).

In a class, you may have also 'normal' helper functions/subroutines, but they are not 'methods'.

It is matter on proper terminology. Methods get 'self' from instance, functions don't. Both are defined by keyword 'def'.

---

