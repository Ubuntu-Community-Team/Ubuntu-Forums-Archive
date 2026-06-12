---
title: "[SOLVED] Python return"
date: 2008-12-20
forum: Programming Talk
---

### Post by matmatmat on 2008-12-20
I am trying to make a simple class that takes a string (a, s, m, d) and two numbers and then if the string is a(dd) it adds them together.
Here is the code:
```

class cal(object):
	

	
	def __init__(self, operator, num1, num2):
		self.operator = operator
		self.num1 = num1
		self.num2 = num2
		# if add
		if self.operator == "a":
			self.add(self.num1, self.num2)
		# if subtract
		elif self.operator == "s":
			sub(self.num1, self.num2)
		# if multiply
		elif self.operator == "m":
			mul(self.num1, self.num2)
		# if divide
		elif self.operator == "d":
			div(self.num1, self.num2)

# functions
	def add(self, x, y):
		return x + y
		

a = cal("a", 1, 2)		
print a

```
when I run the script I get this: 
```

<__main__.cal object at 0x9c0ef6c>

```
Whats wrong?

---

### Post by matmatmat on 2008-12-20
Solved by endless searching of forums.
I created a global variable and set the answer to it then printed it.

---

### Post by nvteighen on 2008-12-20
Er... If you want to have your object printed as string, you should create a method for your class called __str__ that accepts no arguments and returns the string you want.

---

