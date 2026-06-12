---
title: "[SOLVED] for word in"
date: 2008-03-31
forum: Programming Talk
---

### Post by sekinto on 2008-03-31
I have a python script. And I'm trying to do something for every word in a string.

So I have
> for word in [name of my string]:
>>>>[what I want to do]
but for some reason it is reading every single character as a word.

Is "word" the wrong argument?

Say the string was "That ham was delicious!"
I'm trying to do something for "That" "ham" "was" and "delicious!"
Instead it is doing something for "T" "h" "a" "t" " " "h" ...et cetera

---

### Post by LaRoza on 2008-03-31
Variable names can be anything, but they should be descriptive of what they are for humans, not computers.

```

>>> for word in "This is a sentence".split():
...     print word
... 
This
is
a
sentence
>>> 


```

---

### Post by Lord Illidan on 2008-03-31
That's rather obvious.. A string is a list of characters, not a list of words.

Try doing [name of string].split() :D

EDIT : LaRoza beat me to the punch, I'm a newb in Python, so I googled the answer, heh, and tried it out on my box.

---

### Post by LaRoza on 2008-03-31
> **Lord Illidan said:**
> That's rather obvious.. A string is a list of characters, not a list of words.

Try doing [name of string].split() :D

EDIT : LaRoza beat me to the punch, I'm a newb in Python, so I googled the answer, heh, and tried it out on my box.

You are too slow, might as well give up.

Maybe we need a new datatype, the "sentence".

---

### Post by sekinto on 2008-03-31
Thanks for the help, and sorry for being such a noob, but I have another question:

How do I do the same thing with "lines".

---

### Post by LaRoza on 2008-03-31
> **sekinto said:**
> Thanks for the help, and sorry for being such a noob, but I have another question:

How do I do the same thing with "lines".

What is a "lines"?

If this is an external text file:
```

>>> for line in open(".bashrc"):
...     print line
... 

```

For strings with newlines:
```

>>> x = "Line 1\nLine 2"
>>> print x
Line 1
Line 2
>>> for line in x.split('\n'):
...     print line
... 
Line 1
Line 2
>>> 

```

---

### Post by sekinto on 2008-03-31
Actually it is a text file that was converted to a string. But if I do "print [my string]" it still prints each line bellow the other so there must be something telling it that line a is separate from line b.

Edit:
Thanks for the newline thing. I'll try that.

---

### Post by LaRoza on 2008-03-31
> **sekinto said:**
> Actually it is a text file that was converted to a string. But if I do "print [my string]" it still prints each line bellow the other so there must be something telling it that line a is separate from line b.

Edit:
Thanks for the newline thing. I'll try that.

A string is a string, and can have any characters in it.

See my example, that is the character for a Unix newline.

---

