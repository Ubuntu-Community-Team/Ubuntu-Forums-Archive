---
title: "Python Shebang"
date: 2010-12-18
forum: Programming Talk
---

### Post by rcktsingh on 2010-12-18
Hi All, 

I have done quite a bit of Python programming. But never have I used the shebang - 

```
#!/usr/bin/python
```

1) What's the exact purpose of this piece of code ?

2) How does this line accomplish its task ?

3) As I said, I have never used it. But I was going through a tutorial and they said we must put it as our 1st line in any python code. Why didn't it affect me ?

4) Hows it different from 
```
#!/usr/bin/env python
```

Any help is highly appreciated. I did go thru wikipedia stuffs but didn't quite get a hold of it. 

Cheers and Happy Holidays people. 
TIA:guitar:

---

### Post by scottykal12 on 2010-12-18
From the little programming I've done, both do the same thing.
They tell Ubuntu what program to use (python) when running the program.

But what is also interesting if you have different versions of python and want to use a older version just and the version number to the end 
like if you want to use python 2.4
#!/usr/bin/python2.4
or
#!/usr/bin/env python2.4

---

### Post by surfer on 2010-12-18
if you have an executable file, your shell (usually bash) will look at its first line. if it encounters #! it will expect the remaining part of that line to be an executable binary. bash will start this (the python interpreter in your case) and pass the file to it.

the variant 4) may be a little more portable, as other distributions may not install python under /usr/bin/. i prefer the /usr/bin/python version...

---

### Post by surfer on 2010-12-18
just as an example: make this file executable and run it in bash:
```
#!/bin/cat

hello world

```

---

### Post by wmcbrine on 2010-12-18
In short, it's a Unix thing rather than a Python thing. But it's part of Python's heritage as a "scripting language", and it's the reason that "#" is the comment marker in Python.

The only purpose of this line is to allow direct execution of the script from the shell; i.e.:

```
./script.py
```

as opposed to:

```
python script.py
```

You also have to mark the file as executable for this to work. 

It's most useful in the context of adding a new command to the system, where you'd put it somewhere in the PATH (eliminating the need for "./"), and probably leave off the ".py" -- so you'd start it just by typing:

```
script
```

---

### Post by roccivic on 2010-12-18
There is almost no difference. Try:

```
env --help
```

---

### Post by rcktsingh on 2010-12-18
Awesome guys. Thanks. That was helpful. Ofcourse, I would love to have more answers. :D

---

### Post by diesch on 2010-12-19
> **surfer said:**
> if you have an executable file, your shell (usually bash) will look at its first line. if it encounters #! it will expect the remaining part of that line to be an executable binary. bash will start this (the python interpreter in your case) and pass the file to it.


It's not the shell but the kernel that evaluates the shebang line.

---

### Post by Vox754 on 2010-12-19
> **wmcbrine said:**
> In short, it's a Unix thing rather than a Python thing. But it's part of Python's heritage as a "scripting language", and it's the reason that "#" is the comment marker in Python.

The only purpose of this line is to allow direct execution of the script from the shell; i.e.:

```
./script.py
```

as opposed to:

```
python script.py
```

You also have to mark the file as executable for this to work. 

It's most useful in the context of **adding a new command to the system,** where you'd put it somewhere in the PATH (eliminating the need for "./"), and probably leave off the ".py" -- so you'd start it just by typing:

```
script
```

Wonderful. This is the best explanation I've read in a while.

Essentially, the shebang makes a script (bash, python, perl, whatever) behave like any other binary executable.

In order to run a file you give it's full path name
```

/usr/bin/executable

```

If it's in one of the directories that appear in $PATH, you only give the executable name
```

executable

```

As long as "executable" has a shebang, it will be run by its appropriate interpreter. So, from an outside perspective, it doesn't matter if "executable" is a binary file produced by a C, C++, Fortran, etc. compiler, or if it's a script.

---

### Post by surfer on 2010-12-20
> **diesch said:**
> It's not the shell but the kernel that evaluates the shebang line.

you're right of course! my mistake!

---

