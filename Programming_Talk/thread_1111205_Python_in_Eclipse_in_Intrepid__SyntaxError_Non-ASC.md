---
title: "Python in Eclipse in Intrepid : SyntaxError: Non-ASCII character"
date: 2009-03-30
forum: Programming Talk
---

### Post by yeehi on 2009-03-30
I try to run hello world, but using the > ¨key causes a syntax error.

Is there some way I can reconfigure the character sets, perhaps for example to UTF, that will let Python use the > ¨key?

---

### Post by -grubby on 2009-03-30
As far as I know Python 2.5 has no support for that.

---

### Post by cmay on 2009-03-30
[PHP]#! /usr/bin/env python
#encoding:UTF-8
print" the '¨'" 
print "the ¨¨ "[/PHP]
if it is this character it works on my machine this way . ubuntu 8.10 and the python version that is installed per default. if not then just ignore my post :)

---

### Post by yeehi on 2009-03-30
I am glad your Python is working! :)

Where would I paste that php code?

---

### Post by The Cog on 2009-03-30
These two lines:
```
#! /usr/bin/env python
#encoding:UTF-8
```
should be the first two lines of your python source code file.
The second line says what character encoding the source file is using.

---

### Post by yeehi on 2009-03-31
Sorry, I don´t understand what the python source code file is. In which directory do I find that file?

Or is it the file containing the program that I am writing?

---

### Post by Arndt on 2009-03-31
> **yeehi said:**
> Sorry, I don´t understand what the python source code file is. In which directory do I find that file?

Or is it the file containing the program that I am writing?

I don't know in what context you want to use that character (in a string? as a command?) but I can use it in a string simply from the command line:

```
$ python
Python 2.5.2 (r252:60911, Oct  5 2008, 19:29:17) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> s = "apa¨hej"
>>> s
'apa\xc2\xa8hej'
>>> print s
apa¨hej
>>> 
```

Does that work for you too? If not, there may be some difference in our environment variables.

---

### Post by Tony Flury on 2009-03-31
> **yeehi said:**
> Sorry, I don´t understand what the python source code file is. In which directory do I find that file?

Or is it the file containing the program that I am writing?

Yes - The "python source code file" is the file which contains the python program that you are writing.

---

