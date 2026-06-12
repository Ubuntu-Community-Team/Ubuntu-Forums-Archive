---
title: "Python noob"
date: 2010-12-03
forum: Programming Talk
---

### Post by olddai on 2010-12-03
```

>>> print( 'The total is: ', 23+45)

```

Could someone put this noob out of his misery and tell him why he keeps getting a syntax error instead of
The total is: 68

Thanks in advance

---

### Post by Zugzwang on 2010-12-03
Could you copy&paste the syntax error? You are not pasting the ">>>"'s into the python shell, right?

Note that the syntax of the print command changed between Python 2.6 and Python 3.0, but neither should give a syntax error in this case.

---

### Post by Arndt on 2010-12-03
> **olddai said:**
> ```

>>> print( 'The total is: ', 23+45)

```

Could someone put this noob out of his misery and tell him why he keeps getting a syntax error instead of
The total is: 68

Thanks in advance

```
$ python
Python 2.6.5 (r265:79063, Apr 16 2010, 13:57:41) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> print( 'The total is: ', 23+45)
('The total is: ', 68)
>>> print 'The total is: %d' % (23+45,)
The total is: 68
>>> 
```

You don't state clearly what your exact input is, but I guess that you input the >>> characters too. If so, that's the reason. Skip them. They are for python to output, not for you to input.

As you can see, to get what you expected you need to input something slightly different.

Others have had that problem recently. Does perhaps some course material fail to explain the function and form of the python input prompt?

---

### Post by talonmies on 2010-12-03
> **olddai said:**
> ```

>>> print( 'The total is: ', 23+45)

```Could someone put this noob out of his misery and tell him why he keeps getting a syntax error instead of
The total is: 68

Even when you fix the syntax, it won't print that out. This, however, will:

```
>>> print( 'The total is: %d'%(23+45) )
The total is: 68

```

---

### Post by Vaphell on 2010-12-03
confusion may stem from changes between python 2.x and 3.x, print is a function in 3.x

[http://docs.python.org/release/3.0.1/whatsnew/3.0.html](http://docs.python.org/release/3.0.1/whatsnew/3.0.html)
> Old: print "The answer is", 2*2
New: print("The answer is", 2*2)



according to that page OP's example should work though (assuming he uses 3.x)

---

### Post by olddai on 2010-12-03
Ok, the tutorial i was using is at [http://www.alan-g.me.uk/l2p/index.htm](http://www.alan-g.me.uk/l2p/index.htm)

This is the problem:
When i open the terminal and python i typed in the following:

print( 'The total is: ', 23+45) and the output is
('The total is: ', 68

So i suppose the tutorial is out of date? As well as the solution could someone point me to some up-to-date tutorials as well please.

---

### Post by cgroza on 2010-12-03
Go on Youtube and search for : Python Tutorial thenewboston . 
He teaches you the basics and after about 50 videos or so he has a wxPython series for GUI programming.

---

### Post by Zugzwang on 2010-12-03
> **olddai said:**
> So i suppose the tutorial is out of date? As well as the solution could someone point me to some up-to-date tutorials as well please.

No, it isn't. In fact, the tutorial you are using is already based on Python 3, while by detault, if you type "python" in Ubuntu, you start version 2.6, which is older - so install python v.3 and run the respective interpreter instead.

---

### Post by Arndt on 2010-12-03
> **Zugzwang said:**
> No, it isn't. In fact, the tutorial you are using is already based on Python 3, while by detault, if you type "python" in Ubuntu, you start version 2.6, which is older - so install python v.3 and run the respective interpreter instead.

Would you say that dealing with python 2 is only sensible for legacy systems (including helping people having problems with such systems), but all new coding is better done with python 3? Or is the transition period only starting?

I have no idea myself, really, since I have never been a heavy user of python (although feeling competent enough to try to solve others' simple problems).

---

### Post by Vaphell on 2010-12-03
imo it shouldn't really matter, list of changes is not that long
[http://docs.python.org/release/3.0.1/whatsnew/3.0.html](http://docs.python.org/release/3.0.1/whatsnew/3.0.html)

on top of that there is a tool that upgrades the code to v3

> For porting existing Python 2.5 or 2.6 source code to Python 3.0, the best strategy is the following:

   0. (Prerequisite:) Start with excellent test coverage.
   1. Port to Python 2.6. This should be no more work than the average port from Python 2.x to Python 2.(x+1). Make sure all your tests pass.
   2. (Still using 2.6:) Turn on the -3 command line switch. This enables warnings about features that will be removed (or change) in 3.0. Run your test suite again, and fix code that you get warnings about until there are no warnings left, and all your tests still pass.
   3. Run the 2to3 source-to-source translator over your source code tree. (See 2to3 - Automated Python 2 to 3 code translation for more on this tool.) Run the result of the translation under Python 3.0. Manually fix up any remaining issues, fixing problems until all tests pass again.

It is not recommended to try to write source code that runs unchanged under both Python 2.6 and 3.0; you&#8217;d have to use a very contorted coding style, e.g. avoiding print statements, metaclasses, and much more. If you are maintaining a library that needs to support both Python 2.6 and Python 3.0, the best approach is to modify step 3 above by editing the 2.6 version of the source code and running the 2to3 translator again, rather than editing the 3.0 version of the source code.


---

### Post by MadCow108 on 2010-12-03
> **Arndt said:**
> Would you say that dealing with python 2 is only sensible for legacy systems (including helping people having problems with such systems), but all new coding is better done with python 3? Or is the transition period only starting?

I have no idea myself, really, since I have never been a heavy user of python (although feeling competent enough to try to solve others' simple problems).

this summarizes it well:
[http://wiki.python.org/moin/Python2orPython3](http://wiki.python.org/moin/Python2orPython3)

cliffnotes:
if you don't need non-ported libraries and do not have to support python2 only systems, use python 3
if not code newest 2.X version possible. 2.6 and 2.7 have many features of python 3 backported (thus easier transition to 3 if eventually required) and will still be supported for a long time.

---

