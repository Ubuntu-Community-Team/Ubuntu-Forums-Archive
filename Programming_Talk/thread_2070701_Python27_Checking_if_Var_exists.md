---
title: "Python27: Checking if Var exists"
date: 2012-10-13
forum: Programming Talk
---

### Post by Kodeine on 2012-10-13
So I'm trying to say when a function has been called check to see if a variable exists. If not then define it else just continue. But it seems it continually thinks that it isn't defined.

[php]def DrawObjects(dire):
  
  if not 'Thug1X' in dir(): #if not 'Thug1X' AND 'Thug1Y' doesnt seem to work?
    print "Defining var"
    Thug1X = 363
    
  if not 'Thug1Y' in dir():
    Thug1Y = 44
  
  if dire == 'r':
   print Thug1X
   DrawImg('imgs/ThugD.png',(Thug1X-3,Thug1Y))
   Thug1X = Thug1X-3

[/php]

But each time the function is called the Thug1X var always contains 363 as the 'if not 'Thug1X' in dir():' statement is always true?

---

### Post by The Cog on 2012-10-13
Try printing the return value of the dir() function, and look to see if 'Thug1X' really is in there. 
Remember that these test are case sensitive. Like this:


```
def DrawObjects(dire): 
   
    dirresult = dir()
    print "dirresult =", dirresult
    if not 'Thug1X' in dirresult: 
        print "Defining var" 
        Thug1X = 363
```

If you want to check both at once, the syntax is:
```
    if not 'Thug1X' in dirresult and not 'Thug1Y' in dirresult:
```

P.S. brackets make the meaning clearer. These two mean different things:
```
if (not not 'Thug1X' in dirresult) and (not 'Thug1Y' in dirresult):
if not ('Thug1X' in dirresult and 'Thug1Y' in dirresult):
```

---

### Post by trent.josephsen on 2012-10-13
dir() will give different results when called within a function, because the function creates its own namespace. I don't think there's a way to bring external names into this namespace -- 'global' was my guess but it doesn't seem to work that way.

Consider defining it in exactly one place, and initializing it to None, instead of leaving it undefined until you use it. Then it's easy to do

```
def DrawObjects(dire):
    if Thug1X == None:
        print "Defining var"
        Thug1X = 363
    
    ... etc

```

---

### Post by MadCow108 on 2012-10-13
you have to define the variable as global if you want to modify it
else it creates a new one:
```
def DrawObjects(dire):
    global Thug1X
    if 'Thug1X' not in dir():
        Thug1X = 1

```

but this really smells like a bad design

---

### Post by trent.josephsen on 2012-10-13
@MadCow: That was my thought too, but I tested it and "global" doesn't add the name to the list returned by dir(). Creating a closure does, though; the following will print ['var']:

```
def foo():
	var = 'hello, world'
	def _bar():
		print(var)
		print(dir())
	return _bar

bar = foo()
bar()
```

In agreement with you on the second point, though.

---

### Post by MadCow108 on 2012-10-13
true you can't use dir, but probably globals() would work

as we are iterating ugly solutions to a problem you shouldn't really have, here another:

```
def DrawObjects(dire):
    global Thug1X
    try:
        Thug1X = Thug1X
    except NameError:
        Thug1X = 1
```

---

