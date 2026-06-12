---
title: "Whatever Happened to Type Checking?"
date: 2005-11-11
forum: Programming Talk
---

### Post by Ubuntist on 2005-11-11
A long time ago, I used to do a lot of scientific programming in F*****N (I realize that among computer sophisticates, the very mention of that archaic language is offensive).  It involved much number crunching and little in the way of graphics, etc.

Now I'm looking forward to doing a little more such programming for the first time in years, and I'm having a look at the available tools.  I like the look of Python and Ruby, in particular.

I've noticed, though, that neither of these languages seems to have any concept of variable type, e.g., integer, float, or character.  While for quick and dirty applications it is certainly handy to not have to bother with variable declarations, in my experience type checking is very helpful for large projects and saves time in the long run.

Another thing I miss from the old days is having variables initially undefined, so that if you used a variable without having set it first, you'd get an error message.  That too was a nuisance for small projects but valuable for large ones.

Why have these two concepts faded away?

A second question: for number-crunching applications, are there other modern languages that would be better suited than Python or Ruby?

Third question: how much in speed does one sacrifice in, say Python compared to C++?  When I started looking at languages, I started with C++, but my impression is that unless you really need to be close to the machine (i.e., are doing systems programming), C++ forces the programmer to mess around with many more details than he would really want to.

---

### Post by ow50 on 2005-11-11
Answers ragarding Python:

[QUOTE=Ubuntist]I've noticed, though, that neither of these languages seems to have any concept of variable type, e.g., integer, float, or character.  While for quick and dirty applications it is certainly handy to not have to bother with variable declarations, in my experience type checking is very helpful for large projects and saves time in the long run.[/quote]
You can still do type-checking in Python by overriding the attribute access. For example
```
#!/usr/bin/env python

class Foo(object):

    def __init__(self):

        object.__setattr__(self, 'some_list'  , [])
        object.__setattr__(self, 'some_string', '')

    def __setattr__(self, name, value):

        type_attr  = type(getattr(self, name))
        type_value = type(value)

        if type_attr != type_value:
            raise TypeError
        else:
            object.__setattr__(self, name, value)

foo = Foo()

# Correct types
foo.some_list   = [1, 2]
foo.some_string = 'value'

# Incorrect types
try:
    foo.some_list = 12
except TypeError:
    print 'Incorrect variable type'
try:
    foo.some_string = 12
except TypeError:
    print 'Incorrect variable type'

```
The above was quickly written and not well tested.

[QUOTE=Ubuntist]Another thing I miss from the old days is having variables initially undefined, so that if you used a variable without having set it first, you'd get an error message.  That too was a nuisance for small projects but valuable for large ones.[/quote]
The above code does that. When it checks the attribute type, the attribute is assumed to exist, if not it'll raise an AttributeError. In this example the attrbutes were defined via the super class's __setattr__ method.

All of this applies only to instance variables.

[QUOTE=Ubuntist]Third question: how much in speed does one sacrifice in, say Python compared to C++?  When I started looking at languages, I started with C++, but my impression is that unless you really need to be close to the machine (i.e., are doing systems programming), C++ forces the programmer to mess around with many more details than he would really want to.[/QUOTE]
Take a look at [Psyco](http://psyco.sourceforge.net/). It speeds up some code and some it doesn't. You'd need to benchmark it to see it works for your number crunching or other needs.

---

### Post by p1r0 on 2005-11-11
Hi

In my opinion C++ is a great programming language. It's my personal favourtite at least. 
Python and Ruby I don't know muca about them, so I'll talk about what I do know.

Type checking and variables declaration is a great thing that should not fade away. I agree with you on that. 
I myself at work, use PHP no types either there. And yes in the short run that's great indeed but in the long run it's defenitely not good at all.
 
In what I do not agree with you is that "you really need to be close to the machine ". As I see C++ is not that close to the machine, it's just as close as it needs to be. Assembler is close to the machine.

Well all I can tell now is that in my opinion you should take up C/C++.

p1r0

---

### Post by Van_Gogh on 2005-11-11
Why not just still use Fortran? It's still around and as you say easier to use for number crunching than C(++). It's also a piece of cake to link it with Python with a module called f2py(google for its homepage), for any non-numeric work.

I myself am writing a chess program as a hobby. I started doing it in Python(bad idea, recursion is woefully slow in Python because of the overhead of dynamic typing) and searched for another language to do it in. I stumbled upon Fortran and really like it, very Pythonic in its structure. I later tried learning C instead because Fortran seems to have a very small community and hence has few tutorials, but C's alien syntax, excessive use of braces and semi-colons, and *especially* its large use of pointers made me change back to Fortran. C seems a language for only people willing to invest a large time to studying it. So now, I use Fortran 95 for calculations and Python for the GUI. Works like a charm.

Anyway, why not use Fortran to do numeric stuff and then everything else in another language? Seems an ideal combination to me if you're already proficient in Fortran.

BTW, some numeric work can be done very fast in Python too, if you know what modules to use. So try take a look at the SciPy and Numarray modules. They might be excactly what you're looking for.

---

### Post by thumper on 2005-11-11
From what I understand of learning C++ these days, it all depends on what you are learning from.  

One place to get good reviews of technical books is the [http://www.accu.org/](http://www.accu.org/).

One of the guys that reviews a lot of these books came across one really bad one.  One so bad that he felt he should call the publisher and get them to take it out of print.  However the publisher effectively said "Sorry, but that book is the required text for a university programming paper and we sell 3000 copies every year".  So be careful what you learn from.

Modern C++ has come a long way since when I started learning it (1994), and it is easier to use now given that it has an ISO standard.

I also use python a lot, and my general rule is use the right tool for the job.  If you are doing a lot of numerical calculations, use something that is good for that, Fortran, C or C++, but python makes great glue.

---

### Post by LordHunter317 on 2005-11-11
Python does have type-checking, it's just not static.

---

### Post by dogen on 2005-11-13
"I've noticed, though, that neither of these languages seems to have any concept of variable type, e.g., integer, float, or character."
--------------
I think you're exagerating a bit. Python and Ruby do always keep track of integers, floats and strings, but not explicitly and not in-your-face. 

You can pretty much ignore them when it comes to typing in code, but, at least for myself, I always know that "myFileName" is a string and "myIndex" is an integer. I just don't have to tell the compiler because Python can figure it out. 

Some people think the de-emphasizing types like this is a mark of genius, other people think it sucks and invites errors. I think it could be confusing becuase inside your head you really still have to know what types your variables are.

---

### Post by nszabolcs on 2005-11-13
[QUOTE=Ubuntist]
I've noticed, though, that neither of these languages seems to have any concept of variable type, e.g., integer, float, or character.  While for quick and dirty applications it is certainly handy to not have to bother with variable declarations, in my experience type checking is very helpful for large projects and saves time in the long run.
[/QUOTE]

python have dynamic type checking:
```

>>> s = '12'
>>> n = 3
>>> n+s
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
TypeError: unsupported operand type(s) for +: 'int' and 'str'

```

[QUOTE=Ubuntist]
Another thing I miss from the old days is having variables initially undefined, so that if you used a variable without having set it first, you'd get an error message.  That too was a nuisance for small projects but valuable for large ones.
[/QUOTE]

of course you'll get error message if a variable is not initialized:
```

>>> b = 5
>>> a + b
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
NameError: name 'a' is not defined

```


[QUOTE=Ubuntist]
A second question: for number-crunching applications, are there other modern languages that would be better suited than Python or Ruby?
[/QUOTE]
low level languages (like C) are the best, but both ruby and python can be extended via C/C++. eg. the scipy python package is a pretty good competitor of matlab in efficiency.

[QUOTE=Ubuntist]
Third question: how much in speed does one sacrifice in, say Python compared to C++?  When I started looking at languages, I started with C++, but my impression is that unless you really need to be close to the machine (i.e., are doing systems programming), C++ forces the programmer to mess around with many more details than he would really want to.
[/QUOTE]
C++ can be much faster when you do numerical computations, but as said above python lets you do the slow parts with extarnal lowlevel code (for a benchmark see the bottom of this page : [http://www.scipy.org/documentation/weave/weaveperformance.html](http://www.scipy.org/documentation/weave/weaveperformance.html))
C++ is a great language, but not so easy to learn (and batteries are not included).

---

### Post by Ubuntist on 2005-11-14
Thanks to all for the large amount of helpful info.  I'm definitely going to have a look at SciPy/NumPy and the ways of embedding other languages into Python programs.

Do any such embedding facilities this exist for Ruby?

I see I was wrong to say that Python doesn't do any type checking.  Still, it looks like you have to code your own type checking.  That would detract rather a lot from one of Python's major advantages, namely the clean, simple syntax that seems to allow you to code as fast as you can think.  So I imagine I would give up on type checking and just hope for the best.

I had not realized how much Fortran had moved on since I last used it.  Speaking of Fortran, does anyone have any comments on Eiffel?

I've come across a development from Sun's Guy Steele (he of Java and Scheme fame) called Fortress:

[http://research.sun.com/sunlabsday/talks.php?id=55](http://research.sun.com/sunlabsday/talks.php?id=55)
[http://www.ahpcrc.org/conferences/PGAS/presentations/Maessen_Fortress.pdf](http://www.ahpcrc.org/conferences/PGAS/presentations/Maessen_Fortress.pdf)

It is specifically designed for scientific computing and is intended to replace Fortran.  Among other things, its approach to typing is that a type needn't be declared if it can be inferred.  If I code "x=34.3", then x is floating, and a subsequent statement "x = 'Fred'" will generate an error (unlike Python).  It's also suppose to allow the use of standard mathematical notation.  Unfortunately, it's not going to be ready for quite some time, if ever.

---

