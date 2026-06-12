---
title: "Python Question."
date: 2010-05-01
forum: Programming Talk
---

### Post by AlexanderAzimov on 2010-05-01
Hello all I was wondering if I might get a hand with an issue I'm having. I am in the basics of learning to use python3. The issue I'm having is that I make a basic program:

```
#! /usr/bin/python
print("HelloWorld")
```After I go through the saving and so on I try to run it in the interpretor. I get:
```
>>> hello.py
Traceback (most recent call last):
  File "<pyshell#0>", line 1, in <module>
    hello.py
NameError: name 'hello' is not defined
```when I should be able to just run it in the interpretor no problem.

Now If I quick run (f5 in idle) it runs no problem. If I call it from the terminal (python3 /path/to/program/hello.py) it runs no problem. Any suggestions or tips? Its not that I cant live with out running from the interpretor, it would just be way more convenient to be able to type in the program. I know its valid since it runs peachy any other way.

Thanks for your time-

---

### Post by StephenF on 2010-05-01
run it from bash with
$ python hello.py

or set the executable flag on the file with

$ chmod +x hello.py

then run it with

$ ./hello.py

---

### Post by KdotJ on 2010-05-01
Have minimal experience with python, but is it even possible to run the file name from for python console? Don't you have to run the file name from the normal shell?

---

### Post by Tony Flury on 2010-05-01
When you are in the python Interpreter, you can do an import of your module, and in your case your module will execute immediately - if your module defines variables or classes etc - they then become available to your interpreter session


```

>>> import hello

```

The ".py" is not required.

---

### Post by Bachstelze on 2010-05-01
> **KdotJ said:**
> Have minimal experience with python, but is it even possible to run the file name from for python console?

Yes, in Python 2 you can do

```
execfile('path/to/file.py')
```

It has been removed in PYthon 3, however, so if you want to do the same thing you will have to use open/read/exec.

---

### Post by Bachstelze on 2010-05-01
> **Tony Flury said:**
> 
The ".py" is not required.

It won't work with it anyway. ;) If you do [font=monospace]import hello.py[/font], you're trying to import the [font=monospace]py[/font] submodule of the [font=monospace]hello[/font] module. The right way is

```
import hello
```

---

### Post by Tony Flury on 2010-05-01
which is exactly what i put :-)

---

### Post by Bachstelze on 2010-05-01
> **Tony Flury said:**
> which is exactly what i put :-)

I see what you did there. :D

---

### Post by AlexanderAzimov on 2010-05-01
Now I'm to guess if I have it saved to a different folder then my home folder I need to import the path with the program in it?

---

### Post by Nebelhom on 2010-05-03
You could use

```
import os

os.chdir('path/to/the/directory/with/file/in/it')
```

This should allow you to get to the folder you have your files in. To check in what folder you are with the interpreter use

```
os.getcwd()
```

that will give you your current path. for more info on the os module I would look at the [_documentation_]("http://docs.python.org/library/os.html") 

Example from my interpreter:

```
Python 3.1.1+ (r311:74480, Nov  2 2009, 15:45:00) 
[GCC 4.4.1] on linux2
Type "copyright", "credits" or "license()" for more information.
==== No Subprocess ====
>>> import os
>>> os.getcwd()
'/home/nebelhom'
>>> os.chdir('/home/nebelhom/PythonScripts')
>>> os.getcwd()
'/home/nebelhom/PythonScripts'

```

Note: getcwd = get current working directory

chdir = change directory

Hope that helps.

---

### Post by Portmanteaufu on 2010-05-04
It looks like this isn't a problem, but I just wanted to mention it because it's a common stumbling block.

At the moment, Python 3.1 is the latest and greatest version of Python. However, because Python 3.0 broke backwards compatability with 2.6, 2.6 is still considered the standard version right now. (To give people time to migrate their code to python 3+.) This means that on many systems, '#!/usr/bin/python' will be Python 2.6.

If you want to specifically use Python 3, you'll probably have to say so in the path to the interpreter.

Try running:```
which python
``` to see which interpreter it's pointing to and ```
python -V
``` to have it print out its version number.

Fortunately, ```
print("Hello, World")
``` is valid code in both 2.6 and 3+. :)

Have fun!

---

### Post by AlexanderAzimov on 2010-05-06
Thanks for all the help guys. Its good bit of info I need to absorb. Sorry for taking so long to get back to you all.

---

