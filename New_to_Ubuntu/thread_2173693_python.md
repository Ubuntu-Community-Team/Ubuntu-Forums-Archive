---
title: "python"
date: 2013-09-10
forum: New to Ubuntu
---

### Post by Estefi on 2013-09-10
Hi, I'm learning how to program in python and I'm using a package that allows me to see in screen pictures, videos, hear sounds (stimuli). I did a couple of functions with those sitimuli and now I need to do and array with those functions and shuffle the array. If I try something like

x=[func1(),func2(),func3()]
y=shuffle(x)

It does not do anything, if I do the same with an array of numbers it works just fine, I think I have a problem because it's an array of functions but I don't seem to find how to do that. Could anyone help me?

---

### Post by Vaphell on 2013-09-11
what do these functions do/return?
```
$ python
Python 2.6.5 (r265:79063, Oct  1 2012, 22:04:36) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import random
>>> def f1(): return 1
... 
>>> def f2(): return 2
... 
>>> def f3(): return 3
... 
>>> arr=[ f1(), f2(), f3() ]
>>> arr
[1, 2, 3]
>>> random.shuffle(arr)
>>> arr
[3, 1, 2]
```
random.shuffle(array) modifies the input array in place and doesn't return anything, so your y will store nothing.

---

### Post by Estefi on 2013-09-11
Hi, 
well that code works for arrays with numbers and letters, but not for my functions. My functions don't return anything, they show something on screen. Something like this:

def func1():
visual=stimuli.visual("hello world") #with the package I use, when I write that line, it shows "hello world" in a grey screen and I can change size and color of the letters
    return

I define a couple of functions like this for sounds and videos. When I try random.shuffle(arr) it's not doing anything, I think because the functions don't return anything, 

def func1():
visual
   return

def func2():
video
  return

def func3()
sound
  return

y=[func1(),func2(),func3()]
x=random.shuffle(y)

when I run the code it shows me y in order: first func1(), then func2(), then func3(), but always in that order.
If I write print x is shows in the terminar [none, none, none]. I think that is because my functions don't have a return!

Thanks!

---

### Post by Vaphell on 2013-09-11
```
>>> def func1(): print "visual"
... 
>>> def func2(): print "video"
... 
>>> def func3(): print "sound"
... 
>>> arr = [ func1, func2, func3 ]  [COLOR="#0000FF"]# notice lack of (), array stores functions themselves not their returned values[/COLOR]
>>> arr
[<function func1 at 0x15aa050>, <function func2 at 0x15aa230>, <function func3 at 0x15aa320>]
>>> random.shuffle( arr )  [COLOR="#0000FF"]# shuffle functions[/COLOR]
>>> arr
[<function func3 at 0x15aa320>, <function func1 at 0x15aa050>, <function func2 at 0x15aa230>]
>>> for f in arr: f()   [COLOR="#0000FF"]# run functions from arr in reshuffled order[/COLOR]
... 
sound
visual
video
```

---

