---
title: "A python doubt...."
date: 2009-08-01
forum: Programming Talk
---

### Post by veda87 on 2009-08-01
I am a newbie for python.... I have implemented a binary tree in C language, now I am trying it to implement in python.... Now i have some basic doubts... 

1. In C, I have define some structure```
struct node {
  char word
  node *left,*right;
};
``` I think in python , I have to implement in Class....```
Class node:
   word = ""
   node left, right
``` But I don't think it will work....

2. Is there, the concept of pointer in python also
Can I represent ```
node *left
``` in python also...

can anyone clear me with this....

---

### Post by Can+~ on 2009-08-01
About 1: It might work, but you should use the constructor

[PHP]class node(object):
    def __init__(self, word=None, left=None, right=None):
        self.word = word
        self.left = left
        self.right = right

x = node("Hello")
y = node("World", x)
z = node("!", right=y)[/PHP]

If you haven't learn about classes, stay away from this for the time being.

About 2: Python does work with pointers, but "under the hood", for example:

[PHP]>>> a = [0, 1, 2, 3]
>>> b = a
>>> a == b
True
>>> a is b
True[/PHP]

(Operator "is" compares references)

"a" is created as a list, and as soon as you do b = a, it passes a reference instead of copying the value, in fact, I could add a list to "a" through "b":

[PHP]>>> b
[0, 1, 2, 3]
>>> b.append(4)
>>> a
[0, 1, 2, 3, 4]
>>> b
[0, 1, 2, 3, 4][/PHP]

Because, semantically, they both refer to the "same object". So to "represent a pointer" you only use the = operator.


*edit: Here's a very simple binary tree based on the above:

[PHP]#!/usr/bin/env python

class node(object):
	def __init__(self, word=None, left=None, right=None):
		self.word = word
		self.left = left
		self.right = right
	
	def print_prenode(self):
		print self,
		
		if self.left != None:
			self.left.print_prenode()
		
		if self.right != None:
			self.right.print_prenode()
	
	def __str__(self):
		return self.word

x = node("!")
y = node("World", x)
z = node("Hello", right=y)  

z.print_prenode()[/PHP]

The tree would look like

```

      Hello
      /   \
   None   World
           / \
          !  None
```

---

### Post by veda87 on 2009-08-01
I am trying to perform strcmp operation... when ```
Traceback (most recent call last):
  File "dict.py", line 70, in <module>
    start()
  File "dict.py", line 54, in start
    x.add_word()
  File "dict.py", line 24, in add_word
    while((strcmp(str, next_ptr.word) != 0) & (next_ptr != None)):
NameError: global name 'strcmp' is not defined

```

It says strcmp is not defined... Can anyone tell me which library to be imported...

---

### Post by Can+~ on 2009-08-01
strcmp? in Python? Seems that you have something mixed up.

Strcmp is a function from <string.h> in C, in python, the string functionality is builtin in the language as [methods of strings]("http://docs.python.org/library/stdtypes.html#string-methods").

And in your case, you can compare strings with == or !=

```
"Hello" == "hello"
```

Seriously, stop trying to guess how to program in python and follow a [tutorial]("http://docs.python.org/tutorial/index.html").

---

### Post by Cyanidepoison on 2009-08-01
> **veda87 said:**
> I am trying to perform strcmp operation... when ```
Traceback (most recent call last):
  File "dict.py", line 70, in <module>
    start()
  File "dict.py", line 54, in start
    x.add_word()
  File "dict.py", line 24, in add_word
    while((strcmp(str, next_ptr.word) != 0) & (next_ptr != None)):
NameError: global name 'strcmp' is not defined

```It says strcmp is not defined... Can anyone tell me which library to be imported...
You're fighting the way Python works.

---

### Post by veda87 on 2009-08-02
i have started working on python tutorial. Based on the tutorial, i tried > Basic usage of the str.format() method looks like this:

>>> print 'We are the {0} who say "{1}!"'.format('knights', 'Ni')
We are the knights who say "Ni!"


but I got an error when I tried that ```
>>> print 'We are the {0} who say "{1}!"'.format('knights', 'Ni')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'str' object has no attribute 'format'
>>> 

```Wat is the error... can anyone help me...

---

### Post by nvteighen on 2009-08-02
> **veda87 said:**
> i have started working on python tutorial. Based on the tutorial, i tried 
but I got an error when I tried that ```
>>> print 'We are the {0} who say "{1}!"'.format('knights', 'Ni')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'str' object has no attribute 'format'
>>> 

```Wat is the error... can anyone help me...

Uh? I seriously never had seen such thing before in Python.

```

print "We are the %s who say %s!" % ("knights", "Ni")

```

The format specifiers are roughly the same as in C's printf().

---

### Post by spupy on 2009-08-02
> **veda87 said:**
> i have started working on python tutorial. Based on the tutorial, i tried 
but I got an error when I tried that ```
>>> print 'We are the {0} who say "{1}!"'.format('knights', 'Ni')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'str' object has no attribute 'format'
>>> 

```Wat is the error... can anyone help me...

What is your Python version? This was first introduced in 2.6 or 3, i think. I have python 2.5 (gentoo) and I get the same error, because this function (format) is not yet implemented. When reading the python docs be alert for version notes, because there are differences between python 2.* and 3 (I don't know how big of a difference, though).

---

### Post by Greyed on 2009-08-03
> **nvteighen said:**
> The format specifiers are roughly the same as in C's printf().

Er, format() and interpolation are two different things.  Yes, Python's (positional) interpolation specifiers are roughly similar to C's printf() specifiers.  However what he is attempting to use is the format() method which was introduced in [PEP 3101]("http://www.python.org/dev/peps/pep-3101/").

Like you, however, I have found no need for the format() method as when positional interpolation fails to meet my needs the named dict method works fine.  EG:

[php]
stuff = {name : 'Greyed', language : 'Python'}
print("Hi, my name is %{name} and I am a %{language} addict." % stuff)
[/php]

Or, a better example of why I would use named dict interpolation...

[php]
paths = {}
paths['home'] = '/home/grey'
paths['docs'] = '%{home}/Documents' % paths
paths['videos'] = '%{docs}/Videos' % paths
paths['pics'] = '%{docs}/Pictures' % paths
[/php]

...constructing strings built one atop the other where each step is meaningful and might be used in some manner independently but making it easy to modify the heirarchy on the fly.  :)

---

### Post by The Cog on 2009-08-03
Works fine in python 2.6 on Jaunty:
```
~ python
Python 2.6.2 (release26-maint, Apr 19 2009, 01:56:41) 
[GCC 4.3.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> print 'We are the {0} who say "{1}!"'.format('knights', 'Ni')
We are the knights who say "Ni!"

```

---

