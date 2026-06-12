---
title: "Python floating numbers"
date: 2010-10-16
forum: Programming Talk
---

### Post by jordanae on 2010-10-16
This is my first attempt at programming since I started reading up on python yesterday, and I have a pretty good grasp on functions and variables, but I cannot figure out how to calculate floating numbers. Here is my program so far:

```

def Interest():
	P = input("What is the principal?")
	r = input("What is the rate as a decimal?")
	t = input("What is the time in years?")
	I = p * r * t
	print I
	
def Rate():
	I = input("What is the interest?")
	P = input("What is the principal?")
	t = input("What is the time in years?")
	r = I / (P * t) * 100
	print r, "%"

Rate()

```

Because I don't know how to calculate floating point numbers in Python the rate, or "r" variable is always zero. So how do I do calculations with floating point numbers?

And don't be making fun of my n00bish skills :P

---

### Post by jordanae on 2010-10-16
I figured it out. Here's my fix:
```

def Interest():
	P = input("What is the principal?")
	r = input("What is the rate as a decimal?")
	t = input("What is the time in years?")
	I = p * r * t
	print I
	
def Rate():
	I = input("What is the interest?")
	P = input("What is the principal?")
	t = input("What is the time in years?")
	r = float(I) / (P * t) * 100
	print float(r), "%"

Rate()

```

Any advice to clean up my code would be appreciated.

---

### Post by luvshines on 2010-10-16
I think you can convert anyone of them as float and that should do it.

```
I=float(I)
r=I/(P*t)*100
print r
```

Edit: Ah! Nice, you figured it out urself while I as posting :)

---

### Post by jordanae on 2010-10-16
If anyone's interested here's my completed project:

> 
def Interest():
	P = input("What is the principal?")
	r = input("What is the rate as a decimal?")
	t = input("What is the time in years?")
	I = P * r * t
	print I

def Principal():
	I = input("What is the interest?")
	r = input("What is the rate as a decimal?")
	t = input("What is the time in years?")
	P = I / (r * t)
	print P

def Rate():
	I = input("What is the interest?")
	P = input("What is the principal?")
	t = input("What is the time in years?")
	r = float(I) / (P * t) * 100
	print float(r), "%"

def Time():
	I = input("What is the interest?")
	P = input("What is the principal?")
	r = input("What is the rate as a decimal?")
	t = I / (P * r)
	print t, "years"
	
def MyQuestion():
	qu = raw_input("Do you need to know the (a) interest, (b) principal, (c) rate, or (d) time in years?")
	if qu == 'a':
		Interest()
	elif qu == 'b':
		Principal()
	elif qu == 'c':
		Rate()
	else:
		Time()

MyQuestion() 


Reading through it is pretty self-explanatory, but it calculates the interest of a loan, the principal, the rate (percentage of the interest), and the time in years that you pay the loan.

---

### Post by luvshines on 2010-10-16
Should not all divisions be float ?

---

### Post by jordanae on 2010-10-16
yeah, I guess so. I didn't really think about it because normally when I do calculations like this I round. Thanks! I'll work on it after work. But when I was looking up solutions to my floating point number situation I read about the decimal module that sounded more accurate for these types of equations. Do you know of any websites that go over the decimal module?

---

### Post by Yarui on 2010-10-16
The only piece of advice I have for you to clean up the code a little bit is that you reuse the same 4 lines multiple times, those being the following:

```

P = input("What is the principal?")
r = input("What is the rate as a decimal?")
t = input("What is the time in years?")
I = input("What is the interest?")

```For a beginner,  if you want things to look a little more neat with fewer repeated lines, it would probably be best to ask these questions in your main function and pass the values into your interest, principle, rate and time functions.  Those functions could then be a single line each like so:

```

def Interest():
       print P * r * t

```modifying the other ones in a similar way.  There is really nothing wrong with the way you did it, it's just preference in style, really.

Making things even more modular, you could also go a little object oriented with this, making a class that stores the 4 variables and contains all the functions to calculate the missing data, and functions for printing the variable values to the screen.  If you are interested in understanding object oriented programming, then this project could be an easy introduction into that.

---

### Post by StephenF on 2010-10-16
```

def floatinput(*args):
    while 1:
       try:
           return float(raw_input(*args))
       except ValueError:
           print "number required"

def rate():
    I = floatinput("What is the interest?")
    P = floatinput("What is the principal?")
    t = floatinput("What is the time in years?")
    r = 100.0 * I / (P * t)
    print "%0.1f%%" % r

rate()

```
By putting the 100 at the beginning and explicitly putting .0 I make the equation use floats but this is a subtle trick. The floatinput function on the other hand is very self documenting, right down to its error handling.

The input function should never be used.

---

### Post by Yarui on 2010-10-16
> **jordanae said:**
> Do you know of any websites that go over the decimal module?
[http://docs.python.org/library/decimal.html](http://docs.python.org/library/decimal.html)

The official python documentation website is a fantastic place to find good information on any python module.  There is a ton of information on most of the pages, but there is nothing wrong with only looking at the parts of the page that are relevant to what you are doing right now.  This is how I have learned most of what I know about python modules.

---

### Post by luvshines on 2010-10-16
> **jordanae said:**
> Do you know of any websites that go over the decimal module?

Python org has everything :D
[http://docs.python.org/library/decimal.html](http://docs.python.org/library/decimal.html)

---

