---
title: "python return functions incorrect"
date: 2013-02-05
forum: Programming Talk
---

### Post by wingnut2626 on 2013-02-05
Hi people, this is some python code I have been working on...

def add(a, b):
	return a + b
	
def divide(a, b):
	return a / b

def subtract(a, b):
	return a - b
	
```
print " I will attempt to get 995.6 from computational math.  I hope it works."

print "Give me the first number."

var1 = float(raw_input(">"))

print "Give me number 2."

var2 = float(raw_input(">"))

print "Ok, number 3."

var3 = float(raw_input(">"))

print "Ok, the fourth number."

var4 = float(raw_input(">"))

formula1 = divide(var2, var3)

formula2 = subtract(formula1, var4)

print add(var1, formula2)
```

these are the values I provide:

var1=24
var2=34
var3=100 
var4=1023

i get -998.66 from the program, but the math says the answer should be -995.6

Why is that?

---

### Post by wingnut2626 on 2013-02-05
whoops!  Those function definitions are part of the code too

---

### Post by Bachstelze on 2013-02-05
> **wingnut2626 said:**
> 
i get -998.66 from the program, but the math says the answer should be -995.6


Your math is wrong, Python is right.

---

### Post by micahpage on 2013-02-05
```
metulburr@ubuntu:~$ python3
Python 3.2.3 (default, Oct 19 2012, 20:10:41) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 34 / 100
0.34
>>> 0.34 - 1023
-1022.66
>>> 24 + -1022.66
-998.66
>>> 

```

```
metulburr@ubuntu:~$ python
Python 2.7.3 (default, Aug  1 2012, 05:14:39) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 34 / 100
0
>>> 0 - 1023
-1023
>>> 24 + -1023
-999
>>> 


```

---

### Post by Bachstelze on 2013-02-05
What are you trying to say here?

> **micahpage said:**
> ```
metulburr@ubuntu:~$ python3
Python 3.2.3 (default, Oct 19 2012, 20:10:41) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 34 / 100
0.34
>>> 0.34 - 1023
-1022.66
>>> 24 + -1022.66
-998.66
>>> 

```

```
metulburr@ubuntu:~$ python
Python 2.7.3 (default, Aug  1 2012, 05:14:39) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 34 / 100
0
>>> 0 - 1023
-1023
>>> 24 + -1023
-999
>>> 


```

---

### Post by micahpage on 2013-02-05
was just elaborating more on:
> Your math is wrong, Python is right.

---

### Post by Bachstelze on 2013-02-05
> **micahpage said:**
> was just elaborating more on:

And why the two Python outputs (one of which is incorrect)?

---

### Post by micahpage on 2013-02-05
> And why the two Python outputs (one of which is incorrect)?
wasnt paying attention to the fact he float'd the input values

---

### Post by Vaphell on 2013-02-05
i see two different python versions, does python3 really drop to float during integer division?

---

### Post by micahpage on 2013-02-05
> i see two different python versions, does python3 really drop to float during integer division?in 3.x  the / operator does the floating-point division, and the // operator to do truncating division

---

