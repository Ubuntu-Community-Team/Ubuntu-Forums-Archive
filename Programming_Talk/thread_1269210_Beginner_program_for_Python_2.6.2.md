---
title: "Beginner program for Python 2.6.2"
date: 2009-09-18
forum: Programming Talk
---

### Post by Carpentr on 2009-09-18
I have decided I wanted to get into python programming. I want to make a fairly simple program for my first project. It will be run entirely through the command line.

I want to do is the following;

1.Ask the user's name,
Have the user input it's name.

2.Then ask the user's age,
Have the user input it's age.

3.Then have the program repeat the user's name and age. 

The most complicated part of the program is the following. When the user exits out of the program and restarts it I want it to ask the user it's name again. If the user types the same name as before I want the program to remember age and skip right over part 2 to part 3.

What concepts of python programming  would I need to know to accomplish this? Is this a reasonable first project?

---

### Post by BloGTK on 2009-09-18
Yes, that's a very reasonable first project in Python. 

I would recommend starting with [Dive Into Python]("http://diveintopython.org/"), as it's a great way to get familiar with the language. Or, you can dive right in yourself. The language reference at python.org will be something you'll want to bookmark right away.

Once you get used to doing things the Python way, it's pretty easy to figure out. Like any programming language, it has its oddities, but Python's probably the most beginner-friendly.

---

### Post by BloGTK on 2009-09-18
Also, for the concepts you'll need to know. You'll need to learn about strings, and variable. In Python, those are pretty easy (but powerful) concepts.

You pretty much have your "psuedocode" right there. You want to take in some input, save it as a variable, and then compare it to some other input.

Here's what I would suggest... save the name and the age as a dictionary. Dictionaries are used very frequently in Python, and they're not too difficult to use.

---

### Post by mattyB on 2009-09-18
I'd 2nd using the documentation on python.org, the tutorials cover a lot of basic (but good) material. If you're already familiar with coding the Dive into Python book is great.

---

### Post by sunchiqua on 2009-09-18
[http://www.penzilla.net/tutorials/python/fileio/](http://www.penzilla.net/tutorials/python/fileio/) - as you are a beginner ( no offense ), learn how to read/write files ( that's pretty much all you need for this project ).

---

### Post by Tony Flury on 2009-09-18
You could read the data out o and write into a text file, but you might find you run into formatting challenges (for instance what marks the end of someones name).

I would suggest that you use a dictionary to store the data while the programm is running and use the pickle module to save your dictionary (and read it next time your program starts up).

Pickle is one of those very powerful things that just work out of the box with python, and it does not just work on dictionaries. Worst case you need 3 or 4 lines to read data in and out (and that is any data - string, number, object, dictionary, list etc etc etc).

---

### Post by Carpentr on 2009-09-19
Thank you all for the help. It's the weekend so I'm going to try and start reading today. Hopefully this project will not be difficult for me. 

Thanks again.

---

### Post by gordintoronto on 2009-09-19
Issue 27 of Full Circle Magazine started a series called Programming in Python.  It might help you get started.

---

### Post by Carpentr on 2009-09-19
> **gordintoronto said:**
> Issue 27 of Full Circle Magazine started a series called Programming in Python.  It might help you get started.

Thanks for the info. I'll look into it.

Another question. Is it worth moving up to Python 3.x , or just staying with Python 2.x?

---

### Post by unutbu on 2009-09-19
Carpentr, there was a "Beginners Programming Challenge" which was quite similar to the problem you've posed for yourself: [http://ubuntuforums.org/showthread.php?t=881152](http://ubuntuforums.org/showthread.php?t=881152)

You may find it useful to study the code there.

---

### Post by linkmaster03 on 2009-09-20
> **Carpentr said:**
> Thanks for the info. I'll look into it.

Another question. Is it worth moving up to Python 3.x , or just staying with Python 2.x?

Stick with 2.x for now, but learn the [changes in 3](http://docs.python.org/dev/3.0/whatsnew/3.0.html), because 2.6 supports some of them.

If you run your programs with the -3 switch (e.g. "python -3 program.py") then the interpreter will tell you if you are running code that is not compatible with Python 3.

---

### Post by Carpentr on 2009-09-22
Alright. I'll stick with Python 2.6.2 for now then. I just downloaded the documentation off of python.org, so hopefully in the next few days I can familiarise myself with the basic concepts of the language.

---

### Post by ve4cib on 2009-09-22
When I was teaching myself Python I found that the two most useful things to know were the dir function and docstrings.

dir (if you don't know already) tells you what functions and variables are contained within a given module/namespace/object/etc...  So for example dir("hello") will tell you every member of that string.

```
>>> dir("hello")
['__add__', '__class__', '__contains__', '__delattr__', '__doc__', '__eq__', '__ge__', '__getattribute__', '__getitem__', '__getnewargs__', '__getslice__', '__gt__', '__hash__', '__init__', '__le__', '__len__', '__lt__', '__mod__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__rmod__', '__rmul__', '__setattr__', '__str__', 'capitalize', 'center', 'count', 'decode', 'encode', 'endswith', 'expandtabs', 'find', 'index', 'isalnum', 'isalpha', 'isdigit', 'islower', 'isspace', 'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'partition', 'replace', 'rfind', 'rindex', 'rjust', 'rpartition', 'rsplit', 'rstrip', 'split', 'splitlines', 'startswith', 'strip', 'swapcase', 'title', 'translate', 'upper', 'zfill']
>>>

```

Likewise you can see what's in the sys module:

```

>>> import sys
>>> dir(sys)

['__displayhook__', '__doc__', '__excepthook__', '__name__', '__stderr__', '__stdin__', '__stdout__', '_current_frames', '_getframe', 'api_version', 'argv', 'builtin_module_names', 'byteorder', 'call_tracing', 'callstats', 'copyright', 'displayhook', 'exc_clear', 'exc_info', 'exc_type', 'excepthook', 'exec_prefix', 'executable', 'exit', 'getcheckinterval', 'getdefaultencoding', 'getdlopenflags', 'getfilesystemencoding', 'getrecursionlimit', 'getrefcount', 'hexversion', 'maxint', 'maxunicode', 'meta_path', 'modules', 'path', 'path_hooks', 'path_importer_cache', 'platform', 'prefix', 'ps1', 'ps2', 'setcheckinterval', 'setdlopenflags', 'setprofile', 'setrecursionlimit', 'settrace', 'stderr', 'stdin', 'stdout', 'subversion', 'version', 'version_info', 'warnoptions']
>>>

```

Once you see the list of member names you can easily find out what they do by looking up its docstring:

```

>>> print "hello".rfind.__doc__
S.rfind(sub [,start [,end]]) -> int

Return the highest index in S where substring sub is found,
such that sub is contained within s[start:end].  Optional
arguments start and end are interpreted as in slice notation.

Return -1 on failure.
>>>

```

Pretty much all of the standard packages and their contents have proper docstrings.  User-made packages are a little more erratic, but many have them.

To include docstrings in your own functions/classes/modules simply put a string (any text enclosed by '...', "...", '''...''', or """...""") as the very first line inside the block:

MyModule.py
```

#!/usr/bin/python
"""
My very first Python Module!
"""

def helloWorld():
    "Prints the text 'Hello'"
    print "Hello"

```

```

>>> import MyModule
>>> dir(MyModule)
>>> ['__builtins__', '__doc__', '__file__', '__name__', 'helloWorld']
>>> print MyModule.__doc__

My very first Python Module!

>>> print MyModule.helloWorld.__doc__
Prints the text 'Hello'
>>>

```

Even now whenever I'm doing anything big in Python I pretty much always have the interpreter open and make very heavy use of dir and __doc__.  They're amazingly useful features, especially when you're starting out or using modules you're unfamiliar with.

---

