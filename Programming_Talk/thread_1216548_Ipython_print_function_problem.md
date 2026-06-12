---
title: "Ipython print function problem"
date: 2009-07-18
forum: Programming Talk
---

### Post by Dirk13 on 2009-07-18
Hi everyone, 

I am a complete noob at Ipython and have run across a problem. 
If I type a simple code into the regular python terminal I get this output: 

>>> x=1 
>>> y=2 
>>> print x, "+", y, "=", x+y 
1 + 2 = 3 

However in Ipython the same input yields: 
In [1]: x=1 

In [2]: y=2 

In [3]: print x, "+", y, "=", x+y 
------> print(x, "+", y, "=", x+y) 
(1, '+', 2, '=', 3)     

Is it possible to configure Ipython to output without the syntax? 
 1 + 2 = 3 instead of (1, '+', 2, '=', 3) 

Thanks D

---

### Post by smartbei on 2009-07-18
You can always use ''.join():
```

print ''.join(str(a) for a in [x, "+", y, "=", x+y ])

```
By the way - why are you using IPython? This is the first time I heard of it, and while it looks interesting, I think idle (also available from the repos) is a simpler and more conveniant choice as a programming/playing around environment.

---

### Post by benj1 on 2009-07-18
what versions of python and ipython are you using i just tried it and it worked fine for me ( im using ipython 0.8.1 and python 2.5.2)

@ smartbei
ipython is like the python shell but much more, it is basically a full shell, i would use it full time for that purpose if it weren't for minor things like ctrl - c not working. you should check it out

---

### Post by Dirk13 on 2009-07-20
I am using Ipython 0.9.1 on top of python 2.6.2
It is the lastest package in the Jaunty repos.

---

### Post by benj1 on 2009-07-20
i suspect its something to do with the changes in python (print foo will be replaced by print(foo)) judging by this line that you posted
```
------> print(x, "+", y, "=", x+y)
```

if i add brackets to my print statement it gives me a tuple, so im guessing either ipython has changed its implementation which isn't enforced in python 2.6 or python is making the change automatically which isn't playing well with ipython.

it might be a good idea to file a bug report with ipython on launchpad.

---

### Post by BeardlessForeigner on 2009-07-25
IPython has a feature where it adds in parentheses after a function call, i.e., if you enter "my_function 214" it will send my_function(214) to the python interpreter. So you would get something like:

In [1]: my_function 214
------> my_function(214)
OUTPUT OF my_function(214)

This is meant as a convenience, but since "print" has nonstandard syntax in python prior to version 3.0, IPython is actually misinterpreting your input. It is actually running what is after the arrow (the "------>"), and thus printing the tuple (x, "+", y, "=", x+y).

smartbei's solution is nice, or string formatting, such as

print "%d + %d = %d" % (x,y,x+y)

This shouldn't matter with python3, but it seems to be a ways off before IPython and most libraries will work python3.

Update: in IPython, you can type "%autocall" to turn off this feature. Then ' print x, "+", y, "=", x+y ' returns just as it does in the vanilla python interpreter. Type %quickref or $magic in IPython for more information.

---

