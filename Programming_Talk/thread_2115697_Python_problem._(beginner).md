---
title: "Python problem. (beginner)"
date: 2013-02-13
forum: Programming Talk
---

### Post by R3dW00t on 2013-02-13
Hello everybody. ):P

First post here, so i'll make it as short as possible..

class Dog():
def __init__(self,dogname,dogcolor,dogheight,dogbuild,dogmood,dogage):
#here we setup the attributes of our dog
self.name = dogname
self.color = dogcolor
self.height = dogheight
self.build = dogbuild
self.mood = dogmood
self.age = dogage
self.Hungry = False
self.Tired = False
def Eat(self):
if self.Hungry:
print 'Yum Yum...Num Num'
self.Hungry = False
else:
print 'Sniff Sniff...Not Hungry'
def Sleep(self):
print 'ZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZ'
self.Tired = False
def Bark(self):
if self.mood == 'Grumpy':
print 'GRRRRR...Woof Woof'
elif self.mood == 'Laid Back':
print 'Yawn...ok...Woof'
elif self.mood == 'Crazy':
print 'Bark Bark Bark Bark Bark Bark Bark'
else:
print 'Woof Woof'
Beagle = Dog('Archie','Brown','Short','Chubby','Grumpy',12)
print 'My name is %s' % Beagle.name
print 'My color is %s' % Beagle.color
print 'My mood is %s' % Beagle.mood
print 'I am hungry = %s' % Beagle.Hungry
Beagle.Eat()
Beagle.Hungry = True
Beagle.Eat()
Beagle.Bark()

My problem: running this code in a terminal gives a error in line 1
It says there's an unexpected symbol. '('
But when i run this in DrPython, all is well.

What's going on here?

---

### Post by The Cog on 2013-02-13
It should just read
```
class Dog:
```
No brackets.

Please use code tags (# button on the advanced edit screen) to preserve indentation.

---

### Post by R3dW00t on 2013-02-13
The Cog,

thanks for the reply. 
I'll do that in the future.

Now, i've done what you said and, again, in DrPython, no problem, but now there are 3 errors in the terminal.

How is it that DrPython works but not the terminal? It's the same script. ( i think).
Fyi, i'm using the FullCircle magazine Python tutorials. Maybe that's some help.

---

### Post by iMac71 on 2013-02-13
the following link might help you about how to create a python class:
[Class Definition Syntax](http://docs.python.org/2.7/tutorial/classes.html#class-definition-syntax)

---

### Post by Tony Flury on 2013-02-14
> **R3dW00t said:**
> The Cog,

thanks for the reply. 
I'll do that in the future.

Now, i've done what you said and, again, in DrPython, no problem, but now there are 3 errors in the terminal.

How is it that DrPython works but not the terminal? It's the same script. ( i think).
Fyi, i'm using the FullCircle magazine Python tutorials. Maybe that's some help.

I can only assume that DRPython for some reason does not conform exactly to the official spec and allows brackets in Class definitions when you have no parent class, where as the python terminal is the definitive version and strictly enforces the syntax definition.

---

### Post by r-senior on 2013-02-14
According to the grammar spec, the content of the parentheses is optional:

*Python 2.7.3*
```
classdef: 'class' NAME ['(' [COLOR="Red"][testlist][/COLOR] ')'] ':' suite
```

*Python 3.4 (dev)*
```
classdef: 'class' NAME ['(' [COLOR="red"][arglist][/COLOR] ')'] ':' suite
```

And that checks out with a quick test:

```
$ cat circle.py 
class Circle:

    def __init__(self, radius=0):
        self.radius = radius        
        
c = Circle(20)
print c.radius
$ python circle.py 
20
$ vi circle.py 
$ cat circle.py 
class Circle[COLOR="red"]()[/COLOR]:

    def __init__(self, radius=0):
        self.radius = radius        
        
c = Circle(20)
print c.radius
$ python circle.py 
20
```

So something else is at work here, perhaps the way the script is being invoked. Perhaps the OP forgot the shebang?

```
$ ./circle.py 
./circle.py: line 1: syntax error near unexpected token `('
./circle.py: line 1: `class Circle():'
$ vi circle.py 
$ cat circle.py 
#!/usr/bin/env python

class Circle():

    def __init__(self, radius=0):
        self.radius = radius        
	            
c = Circle(20)
print c.radius
$ ./circle.py 
20

```

The OP doesn't say what the errors were when the parentheses were removed but I suspect that explains it.

---

### Post by R3dW00t on 2013-02-15
Woow guys.... thx for the help.

But i must say, i'm a beginner at python, so i'm struggling to understand what has been written here.
It'll take some time, but i'll get to understanding the language. 

From what i can tell right now, the terminal is better to write/learn python, as it enforces the rules?

---

### Post by r-senior on 2013-02-15
> **R3dW00t said:**
> From what i can tell right now, the terminal is better to write/learn python, as it enforces the rules?
I don't think so. I think all you have missed by using the IDE is the way Python scripts can be invoked from a command line on a Unix-like system such as Ubuntu or Mac OS.

A simple Python script such as this:

*hello.py*
```
print 'Hello World'
```

can be invoked from a terminal like this:

```
python hello.py
```

On a Unix-like system, you can add a line at the top which allows it to run like any other shell script:

*hello.py*
```
#!/usr/bin/env python

print 'Hello World'
```

You can run then run it by doing the following:

```
chmod +x hello.py
./hello.py
```

Note that you only need the chmod command once, to make the file executable. Subsequently you just need the ./hello.py command to run it.

As long as you understand that, I see no evidence of a problem in continuing in the DRPython environment if you are comfortable with it.

---

### Post by R3dW00t on 2013-02-15
I like DrPython as it helps me with indentation. (to name one...)
I understand that this is a very important subject in Python. Get it wrong and the code won't work. Writing a script in DrPython is much easier for me.

From what i've learned already, a script always need to start with this line:
#!/usr/bin/env python

But this is optional? Can a script start without this line?
If a simple script can start with as much as print; "Hello World" , maybe more complicated ones will too?

Or do i have it wrong. (i'm guessing i have it all wrong, but i'm asking anyway)

---

### Post by r-senior on 2013-02-15
It is optional. It is a convenience that allows you to run it from a command line like any other program. A Python program can always be invoked by passing it as a command line argument to the Python interpreter:

```
python hello.py
```

It doesn't need the shebang line to run like that.

---

### Post by R3dW00t on 2013-02-15
Ok, got it.

Thanks for the info!

---

