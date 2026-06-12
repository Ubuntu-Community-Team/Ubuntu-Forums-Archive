---
title: "Packaging and Module Programming"
date: 2008-09-12
forum: Programming Talk
---

### Post by dwhitney67 on 2008-09-12
I see a lot of python code on this forum, typically many class objects thrown into one file (the "kitchen sink" as it is known in the s/w industry).

How does one create a package, or modularize their programs?

I came across this poor reference ([http://docs.python.org/tut/node8.html#SECTION008400000000000000000](http://docs.python.org/tut/node8.html#SECTION008400000000000000000)), and unfortunately it was not very helpful.  It lacks a clear example.

Here's a lame program I wrote that I cannot get to work.  I know where the syntax errors are at but how do I fix them??

Modules.py:
[PHP]#!/usr/bin/python

Sound/
	__init__.py
	Echo.py[/PHP]
Echo.py:
[PHP]#!/usr/bin/python

# Echo
#
class Echo:
	def __init__(self, text):
		self.text = text;

	def test(self):
		print self.text[/PHP]
Main.py:
[PHP]#!/usr/bin/python

from Modules.Sound import *

# Yodel
#
class Yodel:
	def __init__(self, echo):
		self.echo = echo 
		self.echo.test()

# Main
#
e = Echo( "Hello World" )
y = Yodel( e )[/PHP]
I get a syntax error at the line containing "Sound/" in Modules.py when I run Main.py as:
```
python Main.py
```

---

### Post by skullmunky on 2008-09-14
I think "Sound/" is not a python command, it's a directory.  And I totally agree with you, it's hard to find clear tutorials on this.  

Here's a couple examples to play with, see if it makes sense.

0. make a directory for this example.  call it "ModuleExample".
1. put Echo.py into the ModuleExample directory
3. put Main.py in the "ModuleExample" directory.
```

import Echo
e = Echo.Echo ("hellooooo")
e.test()

```

4. in ModuleExample, run Main.py as you have been:
```

python Main.py

```

All this does is let you use a class defined in one file in another file.

Note the weird syntax on line 2: 

e=Echo.Echo()

why not just "e=Echo()" ?  Because Echo by itself is the name of the module imported in line 1.  Echo.Echo refers to the class "Echo" INSIDE the module Echo, which is Echo.py.

to demonstrate this a little more, change "Echo.py", add another class to it.

```

# Echo
#
class Echo:
    def __init__(self, text):
        self.text = text;

    def test(self):
        print self.text  
	
class BigEcho:
    def __init__(self, text):
        self.text = text;

    def test(self):
        print self.text 
	print "    " + self.text 
	print "               " + self.text 

```

back in Main.py, you can say
```

e=Echo.BigEcho("hellooooo")

```

to use the BigEcho class.

Proper Python says you should do it this way, refer to classes in modules explicitly with the name of the module so you're always very clear about what module the class belongs to, and you don't get it confused with a class of the same name that might exist in another module.

But if you like to live on the edge, try this in Main.py:

```

from Echo import *
e = Echo ("hellooooo")
e.test()

e2=BigEcho ("goodbye")
e2.test()

```

"from Echo import *" means import everything from the Echo module (Echo.py), so you don't have to qualify it with the Echo module in front.  More specifically, it means "import everything in the Echo module into this namespace instead of having to qualify it as being in the Echo namespace".

Ok, now next you want to know how to make packages with multiple files, all nicely tucked away into a directory.

1. make a directory called "Sound" inside "ModuleExample".
2. move Echo.py in there
3. let's make some more classes.  make another file called "Amplifier.py":
```

# Amplifier
#

class Amplifier:
    def __init__(self, text):
        self.text = str.upper(text)

    def test(self):
        print self.text  
	
class BigAmplifier:
    def __init__(self, text):
        self.text = str.upper(text)

    def test(self):
        print self.text 
	print "EEEEEEEEEEEEEEEEEEE!!!!!!!!!!!!!"
	print "It's all feeding back! Turn it down!"	

```

4. so now you have two module files in the Sound package, each with 2 classes you can use.  But how do you get to them?  For that, you need one more file.  Personally I don't get this part, it seems needlessly complicated, but whatever.

Create a file called "__init__.py" in the "Sound" directory.

```

from Echo import *
from Amplifier import *

```

this file just imports the classes from Echo and Amplifier into the Sound package namespace.  __init__.py is a special name for a file that does this.

5. now back in Main.py, you can import the Sound module all at once, and use any of the classes in it.

```

from Sound import *
e = Echo ("hellooooo")
e.test()

e2=BigEcho ("goodbye")
e2.test()

amp=BigAmplifier ("hello cleveland!")
amp.test()

```

wow I had way too much fun with that.  good luck!

---

### Post by Wybiral on 2008-09-14
What is Modules.py supposed to be?

Just make a folder with an __init__.py in it and that folder will be treated as a module. Or, any .py file will be treated as a module.

You probably see a lot of non-modular code here because it's easy to post it on the forum that way.

---

### Post by LaRoza on 2008-09-14
For Python module use, check out sysres. I had to figure it out to do it, but it is simple.

[https://code.launchpad.net/sysres](https://code.launchpad.net/sysres)

---

### Post by dwhitney67 on 2008-09-14
Skullmunky, thank you for the informative steps on modular programming in Python.

---

