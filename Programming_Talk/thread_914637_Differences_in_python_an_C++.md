---
title: "Differences in python an C++"
date: 2008-09-09
forum: Programming Talk
---

### Post by dagoth_pie on 2008-09-09
I was learning python for a while, but I kept on getting confused when it came to stuff like functions, so I read through a c++ tutorial, and turns out, that a lot of the things that people said python was better for, actually made it slightly harder to understand like the ; at the end of every line and { } around the functions, it seems to make it a easier for a novice to understand, but then i got to the variables in the c++ tutorial, and it seemed to be unnessesarily complicated compared to python, where it was saying all that stuff about unsigned short integars and stuff... meand while with python its as simple as a = 1. so I'm wondering, why is it that they have such a different approach to things like that, or is the tutorial that I've been reading just going into too much detail for a newb like me, and trying to teach me good habbits, while really I could do it as simply as its done in python?

---

### Post by CptPicard on 2008-09-09
From what it sounds like, trust me, stick with python. For example, functions are functions in both languages, and C++ ones will confuse you about as much.

C++ is IMO one of the most (unnecessarily) complicated languages around, and I really wouldn't recommend it for a beginner, for reasons that really are a bit hard to explain to you at the level of your current competence -- for example we'd have to go into a discussion of static vs. dynamic typing (the fact that in C++ you must explicitly declare the type of your variable, as you noticed) :)

However, if you insist on having a feel for "the other kind of language", you might want to look at just C, although it certainly is not my first suggestion here...

---

### Post by CptPicard on 2008-09-09
(accidental double post)

---

### Post by dagoth_pie on 2008-09-09
ok i can see your point, I guess I'll stick to python and if i get stuck then I'll look at the same thing in c++ and see if it clears things up, I understand functions reasonably well now, it was just a lil confusing because of it being decided by whitespace rather than the brackets, thanks for your help

---

### Post by CptPicard on 2008-09-09
> **dagoth_pie said:**
> ok i can see your point, I guess I'll stick to python and if i get stuck then I'll look at the same thing in c++ and see if it clears things up

You're much better reading the docs or asking the Python-relevant question here than trying to learn Python from C++... it really is the wrong way to go, C++ is not going to "clarify" anything in that regard.

> 
I understand functions reasonably well now, it was just a lil confusing because of it being decided by whitespace rather than the brackets

The indentation/whitespace issue is a bone of contention really.. some people like it, some don't. I don't, but one gets used to it.

---

### Post by dagoth_pie on 2008-09-09
yes, i think that with c++ the thing that it came down to was the tutorial i was reading was better at explaing what a function was and how it worked than the python tutorial, after all it did help, which im assuming i have to understand at least that to get anywhere in programming :lolflag: ill just ask here next time I get stuck on something (after reading through the tutorial a few times naturally)

---

### Post by Faolan84 on 2008-09-09
Python runs a little bit slower, but you can if you need integrate C code functions if you need a function that runs a little faster. It's really not noticeable unless you are on a really old computer or are designing a program that is really complex from my understanding.

Python is a good language to start with, so is C++. The advantage to learning C++ is that learning C is easier and vice versa, but they are much more complex.

---

### Post by Erdaron on 2008-09-09
> **Faolan Devyn Aodfin said:**
> Python runs a little bit slower, but you can if you need integrate C code functions if you need a function that runs a little faster. It's really not noticeable unless you are on a really old computer or are designing a program that is really complex from my understanding.
Straight up Python fails pretty badly if you're doing a lot of number crunching (data smoothing, polynomial fits, etc.). Algorithms themselves are pretty simple, but there is a lot of processing involved. That's why its numeric extension (NumPy) is written in C.

For me, the most useful thing in understanding functions in programming was learning functions in mathematics. You give it stuff. Phase 2. Profit.

---

### Post by Greyed on 2008-09-09
> **dagoth_pie said:**
> ok i can see your point, I guess I'll stick to python and if i get stuck then I'll look at the same thing in c++ and see if it clears things up, I understand functions reasonably well now, it was just a lil confusing because of it being decided by whitespace rather than the brackets, thanks for your help

If you feel the linenoi^H^H^H^H^H^H^Hpunctuation helps you understand the concepts I'd say switch gears and go with a comparable scripting language that uses such punctuation.  Perl is a side-step from Python in functionality and general thinking of how to approach problems.  It, however, requires C-esque punctuation in its syntax for block declarations... and pretty much every where else.  Normally I'd eschew Perl for anything (being a former Perl hacker, I'm allowed) but in this case it may help you understand the concepts and get to the point where you can hop back to Python once comfortable.

---

### Post by samjh on 2008-09-09
> **dagoth_pie said:**
> but then i got to the variables in the c++ tutorial, and it seemed to be unnessesarily complicated compared to python, where it was saying all that stuff about unsigned short integars and stuff... meand while with python its as simple as a = 1.

All variables have a data type.  This is true for Python, as it is for C++.

Python uses what is called "duck typing" or "dynamic typing", where the language itself decides what data type a variable is.  In C++, you have to specify what the data type is.

Python and C++ both are what is called "strongly-typed" languages.  That means you cannot use a variable of a particular data type to process other data types not compatible with it.

Example from the next post:
x = '1'
y = 1 + x
...cannot be done because x is a character symbol of '1', and you cannot add the numeric value of 1 to a character symbol of 1.

So when it comes to variables, Python isn't actually much simpler - or simpler at all - than C++.  The only substantial difference is that with Python, the Python interpreter will determine the data type of a variable when you first use it, while in C++ you have to tell the compiler what the data type is when you declare the variable.  Under the hood, Python also has unsigned integers, integers, floats, etc., but the programmer doesn't really get to see it (until they accidentally misuse one and get an error).

Python is simpler than C++ in general, but variables aren't really it. ;)  You'll have to look further into each language before discovering the really significant differences. :D

---

### Post by Greyed on 2008-09-09
> **samjh said:**
> Python and C++ both are what is called "strongly-typed" languages.  That means you cannot use a variable of a particular data type to process different types of data.

Er... you kind of had it here...

> For example, you cannot use a variable named [FONT="Courier New"]x[/FONT] to process an integer (ie. a whole number) in one part of the code, and then a string (ie. a bunch of characters) in another part of the code.

...then slipped here...

> Once [FONT="Courier New"]x[/FONT] is an integer, it has to stay as an integer, and trying to misuse the data in [FONT="Courier New"]x[/FONT] will result in an error (like trying to put the letter "A" in [FONT="Courier New"]x[/FONT] instead of an integer).

And lost it here.

In python this is legal even though your last statement says it is not:
```

var = 'a'
var = 1
var = 1.1
var = [1]
var = {foo: 'bar'}

```

    X in one portion of the code can be something else elsewhere in the code.  I think where you meant to go was that once you declare X as something it cannot be used (or processed as you were heading for) in a manner that "something" cannot be used.  So this would be illegal in both languages:

x = '1'
y = 1 + x

    The catch being the operation being performed is numeric whilst the variable contains a string.  It's the operation that matters in Python, not the assignment.

> So when it comes to variables, Python isn't actually much simpler - or simpler at all - than C++.

It is, really.  Sure one can have lists and dicts in C; CPython implements them so that statement is self evident.  But to build and maintain them is a lot of low-level work a Python developer does not have to reinvent every application.  Also Python goes a long way towards masking pointers.  I mean look at the above example of code and realize that I did not assign a single variable to var.  What I did in Python is sequentially assign a label to a series pointer which hold the address to the variables.  That means when I do something like this...

```

foo(var)

```

I am not passing the variable; I am passing the reference.  Furthermore I don't have to dereference it inside of foo(); I just have another label inside foo() which gets assigned to that same pointer.  I couldn't begin to tell you how to do that in C but to know it all has to be handled manually and woe be until the programming who flubs it.  I also find it mildly amusing that still needed to be explicitly done in Perl the last time I seriously used it.

Automatic memory management, automatic reference/dereferencing and complex data structures all built into the base language does, indeed, make variables far simpler to conceptualize and use in Python as compared to C/C++.

---

### Post by dribeas on 2008-09-09
> **Greyed said:**
> Automatic memory management, automatic reference/dereferencing and complex data structures all built into the base language does, indeed, make variables far simpler to conceptualize and use in Python as compared to C/C++.

I agree in memory management (note that it is NOT resource management, you still have to take care of non-memory resources manually -- as in C++, C++ offers RAII to help there). If you use references (not pointers) you get the same automated 'reference/derreference' you talk about. About data structures, I don't know what you use but I hardly ever had to develop a data structure --if it was not specific to an algorithm.

---

### Post by samjh on 2008-09-09
> **Greyed said:**
> ...

I really didn't want to get to that level of detail for a beginner who doesn't even know what data types are. ;)

Look at the OP.  He's getting confused about unsigned ints.  Memory management, lists, dictionaries, scoping, etc., will go completely over his head.

Although, yes I slipped up on the thing about variable assignment.  In my defence, I was trying to explain it in a generic way compatible with both C++ and Python, not just Python.  My bad. :(

Now, can we get back to a level of discussion understandable to complete novices? ;)

---

### Post by CptPicard on 2008-09-09
IMO samjh's explanation was about what x refers to, not the symbol 'x' itself. Could have been pointed out though :)

---

### Post by samjh on 2008-09-09
Greyed caught me out fair and square.  I was referring to variable name x.

I've corrected my post and cited Greyed's example. :)

However, I stand by the remainder of my post in the context of explaining an essentially complex topic in the simplest text possible. ;)

---

### Post by pmasiar on 2008-09-09
> **Greyed said:**
> If you feel the linenoi^H^H^H^H^H^H^Hpunctuation helps you understand the concepts I'd say switch gears and go with a comparable scripting language that uses such punctuation.  Perl[...] may help you understand the concepts and get to the point where you can hop back to Python once comfortable.

While i used to like Perl, I would hesitate to suggest it to beginner, because of all the quirks (scalar vs list context, default variables, sigils ~= "line noise" etc).

OP: before jumping, read "why to love/hate" threads for both Perl and Python, to see what you are going to dive into.

My suggestions would be to try to read couple different tutorials for Python. I found that each one succeeds in describing some parts better - and even if not, describing the same part in different words is better than reading about similar concept in different language.

Wiki in my sig has many links to free learning sources. Also, try to solve simple problems: experimenting in python shell is best way to learn, just try how it works.

---

### Post by pmasiar on 2008-09-09
> **samjh said:**
> All variables have a data type.  This is true for Python, as it is for C++.

Python uses what is called "duck typing" or "dynamic typing", where the language itself decides what data type a variable is.  In C++, you have to specify what the data type is.

Main difference (as Greyed correctly mentioned) mentioned is that in C, type is associated with variable, but in Python, type is associated with value. So in Python you don't "assign" value to variable, but "bind" a name with a value. You can bind name with a string, later with number, and later with function. If your code can handle it, all is peachy, and there are no type nazis giving you compile errors (language trust you and expects you to know what you are doing. C++ does not trust you). Of course if you don't, you have runtime error when you want to split a number, or call a string with parameters :-)

So this simple (almost invisible) tracking of type makes Python much simpler for beginner: computer does most of the work of making sure that different (and correct) operation is called for + when x+y are **both** numbers, or strings.

---

### Post by cmay on 2008-09-09
> My suggestions would be to try to read couple different tutorials for Python. I found that each one succeeds in describing some parts better - and even if not, describing the same part in different words is better than reading about similar concept in different language.
good idea. you could maybe also use the library. i for one  had to use more than one book to grasp certain things.

---

