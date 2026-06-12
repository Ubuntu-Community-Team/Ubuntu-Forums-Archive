---
title: "[Python] Seems like a bug in python... or...?"
date: 2008-09-20
forum: Programming Talk
---

### Post by [CPR]-AL.exe on 2008-09-20
Hi there. It seems, that i ran into a bug in Python 2.5

Here's the test code:

```
#!/usr/bin/evn python
# -*- coding: UTF8 -*-
#coding=UTF8



class Test():
    
    def __init__(self,text="",array=[],number=0):
        
        self.text=text
        self.array=array
        
        self.number=number
        
    def compile (self):
        
        output=self.text +" - "
        output+=str(self.array) +" - "
        output+=str(self.number)
        
        return output
    
    def __str__(self):
        
        return self.compile()
    
    
a=Test("something", ['sin','sex','salvation'], 8)
b=Test()
c=Test("",[])
d=Test()
d.number+=1
e=Test()
e.array.append("appendedStuff")

#the output of the following expressions is listed in the comments:
                   
print a            # something - ['sin', 'sex', 'salvation'] - 8
print b            #  - ['appendedStuff'] - 0
print c            #  - [] - 0
print d            #  - ['appendedStuff'] - 1
print e            #  - ['appendedStuff'] - 0



```

So, there are five instances of a class. The **a** instance's properties a initialized in the moment of creation and everything is OK.

The strange thing comes when I append an object to e.array. You can see, that I append String "appendedStuff" only to e.array, but it automatically appends to b.array and d.array!

a.array and c.array stays untouched.

What the hell is going on? :(

UPD: I expect only e.array to be updated after  e.array.append("appendedStuff") expression.

---

### Post by LaRoza on 2008-09-20
I doubt it. You didn't say what the problem was, or what was expected so it is hard to address it.

Most of the time when someone finds a bug in a compiler or interpreter, it is a bug in their program.

---

### Post by [CPR]-AL.exe on 2008-09-20
Srry, I've updated the thread (accidentelly posted it before describing the problem). I hope it's a bug in a program, not in interpreter :)

---

### Post by pmasiar on 2008-09-20
(1) Thats classic mistake when using [] as default (Mutable default argument) : use None. 

(2) array is dangerously close to reserved keyword or module, I would never called my variable so.

```

def __init__(self,text="",arr=None,number=0):
    if not arr: 
        arr = []

```

I dug out all gotchas for Python beginners long time ago on my wiki: [http://learnpython.pbwiki.com/PythonTricks](http://learnpython.pbwiki.com/PythonTricks)

But beginners are especially reluctant to learn from mistakes of others and insist on repeating the same beginner's mistakes like all other beginners did 8-)

---

### Post by y-lee on 2008-09-20
It is a bug in your code. Python is acting in a way that is a bit counter intuitive to you.

As best I can explain it the line 
```
def __init__(self, text="", array=[], number=0):
```

will set array to the same instance of [] if array is not set up the call to__init__ and therefore self.array is set to this very same array.

What you wish instead is to change the line

```
self.array=array
```

to 

```
self.array=array[0:]
```

which will copy the empty list array into a new list and set self.array to this new list.

I hope this makes sense to you because i am really tired and am truthfully new to python myself. :)

Edit: What pmasiar posted above will also work and his advice on not using array as a variable name is a good idea.

---

### Post by [CPR]-AL.exe on 2008-09-21
> (2) array is dangerously close to reserved keyword or module, I would never called my variable so.

Yes, so do I, but this is a sample code to show the mistake, I just had no imagination to name the variable in other way. Strange, that you didn't noticed the same problem with the *number* value ;)


> ```
def __init__(self,text="",arr=None,number=0):
    if not arr: 
        arr = []
```

Thanks, that's an obvious workaround and all my classes are already made in this-like way, but I still suppose it's only a workaround, which is not the real problem solution.

**y-lee**, thanks for reply, I see the interpreter works in this way, but should it? Everything is because Python doesn't have the *new* keyword, like many languages do... And the problem exists only with using lists! Any other object types work normally.

Seems to me, It's an interpreter's bug, 'cause this problem exists only in Python language :-\


My current workaround is very similar to **pmasiar**'s, but a bit more laconic:

```
def __init__(self,arr=None):
    arr = arr or []
```

---

### Post by the_unforgiven on 2008-09-21
Yes, the interpreter should behave as it is.
The reason for that: object referencing.

You could see it in action if you'd just put following statement in your Test.__init__():
```
print 'using arr: 0x%x' % id(array)
```
This will print the address of array - if you see it as the same hex no. for all your objects, then it's obviously referring to the same object in memory.

What you need is a deepcopy:
[http://docs.python.org/lib/module-copy.html](http://docs.python.org/lib/module-copy.html)

So, doing ```
self.array = copy.deepcopy(array)
``` should do the trick.

HTH ;)

---

### Post by [CPR]-AL.exe on 2008-09-21
I've used PyDev debugger to check that lists's hex are not the same... 

Anyway, why Python behave like this? Why should i copy something? There should be a normal way of creating new objects. Why does [] and list() refer to previously created objects? Why do string and dictionaries work in a normal way?

---

### Post by pmasiar on 2008-09-21
> **'[CPR]-AL.exe said:**
> Anyway, why Python behave like this? 

This (anomymous list as default param) is a sneaky way to have static variable accessible only from inside of the function.

> Why should i copy something? 

Copying is confusing workaround. Use immutable values as defaults, and you are fine.

> There should be a normal way of creating new objects. Why does [] and list() refer to previously created objects? Why do string and dictionaries work in a normal way?[/QUOTE]

Was explanation in the links I provided not sufficient? Empty dict {} behaves exactly like  empty list as default arg. Strings are immutable, so they are not subject your confusion.

---

### Post by [CPR]-AL.exe on 2008-09-22
Ok, but why the hell does it mute without any identifier? Why does it mute to [] or list()?

That's stupid. I'll file a bug.

That's the only language I know, that behaves like this.

---

### Post by pmasiar on 2008-09-22
You are free to file that as a bug, but you will waste your time, and what is worse, waste 15 secs of developer's time to read it and close it as NOTABUG WONTFIX.

Because it is not a bug but a feature (static variable), you just not able to understand the explanation for some reason. Oh well.

---

### Post by [CPR]-AL.exe on 2008-09-22
They wasted more of my time to debug my application. Seems like a deal ;)


Static variables should be static variables of a class. Instances variables should be instance variables. This issue ruins the whole paradigm of OOP.
In Russian, there's a word that will sound in English like bugofeature, meaning that an accident bug could be used as a feature, but it also can be annoying.

---

### Post by pmasiar on 2008-09-22
> **'[CPR]-AL.exe said:**
> Static variables should be static variables of a class.

Your mind is poisoned by OOP. Any functions, not only class, could have static variable. But because your mind is poisoned by Java, you cannot imagine any code living outside of the class structure.

> In Russian, there's a word that will sound in English like bugofeature, meaning that an accident bug could be used as a feature, but it also can be annoying.

Let's not go there: In Russia, bugs report YOU!

[http://uncyclopedia.org/wiki/Russian_reversal_%28joke%29](http://uncyclopedia.org/wiki/Russian_reversal_%28joke%29) 8-)

---

### Post by pp. on 2008-09-22
> **pmasiar said:**
> it is not a bug but a feature (static variable)

It's not a static variable. 

[QUOTE=Corollary to Murphy's Law] Variables won't. Constants aren't.
[/QUOTE]
The thing in the method header is a literal. Every time the method header is executed, the same literal is being used, i.e. the same instance of the object described by the literal.

Let's take the case of a string literal. You would accept it as a matter of course that each time you call the method the literal supplied for the missing actual argument refers to the same instance of the 'same' string. You'd find it quite wasteful to use another instance of the same sequence of characters each time.

I don't know Python all that well ATM. I would think that using a function call instead of a literal as default value for a formal argument might do what OP thinks ought to be done.

Amirite?

---

### Post by pmasiar on 2008-09-22
> **pp. said:**
> It's not a static variable.

Of course it is not. It only can be used that way. It is well-known quirk of the language (one of the few), and beginners like OP would be better off learning the quirks instead of reporting it as a bug (which would be rejected). 

> The thing in the method header is a literal. Every time the method header is executed, the same literal is being used, i.e. the same instance of the object described by the literal.

Let's take the case of a string literal. 

Can you see that there is difference between mutable literal (list) bound to a name as default value and immutable one (string)?

Obviously, if you change mutable one, mutated value is still there.

> You would accept it as a matter of course that each time you call the method the literal supplied for the missing actual argument refers to the same instance of the 'same' string. You'd find it quite wasteful to use another instance of the same sequence of characters each time.

this is exactly what is happening with immutable literals. Even some numbers (integers 1..99) are stored as literal constants.

> I would think that using a function call instead of a literal as default value for a formal argument might do what OP thinks ought to be done.

Why so complicated? I shown OP canonical way to solve his issue, using None as default value.

> Amirite?

Some secret language?

---

### Post by pp. on 2008-09-22
> **pmasiar said:**
> Can you see that there is difference between mutable literal (list) bound to a name as default value and immutable one (string)?

Why so complicated? I shown OP canonical way to solve his issue, using None as default value.

To be quite truthful, there is no difference apart from the fact that some classes are defined to be immutable and some aren't. The mechanism applied in substituting a default value for missing actual values is always the same. For some reason, OP expected Python to treat mutable objects differently from immutable ones.

What you describe as 'canonical' is not all that canonical. It's just a special case. Coding 'NONE' as default value is markedly different from a unique empty list. Passing an UndefinedObject or a special marker object which has to be replaced by the wanted value later in the code is - according to my tastes - a far cry from what had been intended by default values for the parameter. In that case, you'd do better without any default values at all.

The only catch is that I haven't yet bothered to find out whether Python accepts constant expressions only for default values or if expressions evaluated at run time are accepted as well.

'Amirite' is an expression used by some circles for 'Am I right'.

---

### Post by pmasiar on 2008-09-22
> **pp. said:**
> there is no difference apart from the fact that some classes are defined to be immutable and some aren't. The mechanism applied in substituting a default value for missing actual values is always the same. 

Not exactly. Python keeps reference of default value. When immutable object is changed, new object is generated, and reference is reassigned (as always is for immutable values) but if mutable object is changed, reference stays the same, so the "default" (target of the  reference) is changed. 

If your default was defined as arr=['x'] and you will change arr, next time around default value or arr would be changed, exactly as you did it. So if you don't want that, don't use mutable values as default.


> Passing an UndefinedObject or a special marker object which has to be replaced by the wanted value later in the code is - according to my tastes - a far cry from what had been intended by default values for the parameter. 

But if you define that [] if used as default parameter should be immutable (not a subject of change) **that** would be spacial case - and you would disable functionality useful for some useage.


> In that case, you'd do better without any default values at all.

Having simple convenient default values is IMHO much preferable to Java's multiple signatures for same function name, and is substantially more readable.

---

### Post by [CPR]-AL.exe on 2008-09-22
> But because your mind is poisoned by Java

I'm not a Java coder, I'm generally an AS2,AS3 programmer (which is a bit similar, 'cause AS is based on ECMAscript) and i have some experience in C++.

> Your mind is poisoned by OOP.

What do you mean? :) OOP is a paradigm, that is described for any language and should be used in quite similar way, no matter what language you prefer.

> Let's not go there: In Russia, bugs report YOU!
Yes, let's not go in there, because this one-liner is actually not too funny.

> you cannot imagine any code living outside of the class structure.

I can. But not in this weird way. I do not use classes, where i can handle something without them.


**pmasiar**, do you really think, that a class *constructor* should create anything rather than a *new* object? If the constructors like *list()* are not used to create a *new* object, how the hell can you create one?

---

### Post by slavik on 2008-09-22
things like what the OP found in this thread is what annoys me about Python. Imo, anything in the function header has to be declared (as a separate copy).

Correct me if I am wrong, but isn't this a similar situation to when two children inherit a list from a parent, yet one child changes his list and the other child sees it or something of the sort?

---

### Post by pmasiar on 2008-09-22
> **'[CPR]-AL.exe said:**
> 
[CPR]>> Static variables should be static variables of a class.

pmasiar> Your mind is poisoned by OOP.

What do you mean? :) OOP is a paradigm, that is described for any language and should be used in quite similar way, no matter what language you prefer.

I said you cannot imagine static variable outside of a class structure. This is (for me) clear sign of OOP poisoning. Any C hacker can imagine nice static variable, local or global, and default=[] trick makes local static variable in Python possible without flexing any muscles. And mind you, without referring to OOP - if can be static variable of any plain function.

[CPR]>Yes, let's not go in there, because this one-liner is actually not too funny.

Actually, bug reporting you is pretty funny on at least two levels. But I admit possibly only in democratic countries where you would not expect government to but bugs to spy on you. Ooops, USA is becoming unfunny too. :-(

[CPR]> **pmasiar**, do you really think, that a class *constructor* should create anything rather than a *new* object? 

How OOP is relevant? Can you see usage of static local variables outside of OOP? 

[CPR]> If the constructors like *list()* are not used to create a *new* object, how the hell can you create one?

How creating new object is related to static variables? This is why I mentioned "OOP poisoning" 8-)


Edit:
you mean that defining function def foo(arr=[]): should create new list in every call of foo? But you never asked for that: the only time you asked to allocate space for new list is single time when you defined foo. Function is object like any other. That def statement will not be executed again just because you called function foo. Why should it?

---

### Post by pmasiar on 2008-09-22
> **slavik said:**
> things like what the OP found in this thread is what annoys me about Python. 

What is one little quirk for someone who loves Perl, language full of bigger quirks? 8-)

> Imo, anything in the function header has to be declared (as a separate copy).

it is, but list is mutable. Mutability of object is important concept for flexible OOP language like Python.

> Correct me if I am wrong, but isn't this a similar situation to when two children inherit a list from a parent, yet one child changes his list and the other child sees it or something of the sort?

descendant will get own copy of public properties. And even private properties can be inherited in a safe but maleable manner if namemangling is used (double-underscore prefix).

Difference between strict OOP language like Java and flexible one like Python is in assumptions: Python (like Perl) trusts programmer not to do dangerous things, but allows flexibility if you need it. Java instead rigidly does not allow anything what has more than shade of doubt, regardless of penalty or consequences, so developers use tricky patterns, dependency injections and crap like that, to find workarounds.

You, as Perl acolyte, should be more familiar or welcoming with that more flexible approach. :-)

---

### Post by [CPR]-AL.exe on 2008-09-29
> Java instead rigidly does not allow anything what has more than shade of doubt, regardless of penalty or consequences, so developers use tricky patterns, dependency injections and crap like that, to find workarounds.

I duon't know about Java, but AS-developers (language still based on ECMAscript) don't run into problems with that strictness. It only helps you to find mistakes.

---

### Post by pmasiar on 2008-09-29
> **'[CPR]-AL.exe said:**
> I duon't know about Java, but AS-developers (language still based on ECMAscript) don't run into problems with that strictness. It only helps you to find mistakes.

You don't run into problems because as blub programmer you are perfectly happy with shackles provided by AS, and obviously you cannot miss the freedom if you never experienced it. Try it sometimes, and your thinking about what is essence of programming will never be the same!

---

### Post by [CPR]-AL.exe on 2008-09-30
Don't really think so. The freedom, you're talking about is a freedom of making mistakes. And that freedom cannot provide you the full control of the CPU and memory while running your program.

You're talking like you like PHP.

Maybe, you suppose, that C doesn't give much freedom and sucks, too?

---

### Post by slavik on 2008-09-30
> **pmasiar said:**
> What is one little quirk for someone who loves Perl, language full of bigger quirks? 8-)

care to give examples?

as for the "flexibility" that is "given" here, sorry, that's not what I expect to happen in an OO language

---

### Post by [CPR]-AL.exe on 2008-09-30
**Slavik**, thanks, I'm glad that someone supports my point of view.

I was starting to think, that i am kind of alone in this Holy War :D

---

### Post by LaRoza on 2008-09-30
> **'[CPR]-AL.exe said:**
> **Slavik**, thanks, I'm glad that someone supports my point of view.

I was starting to think, that i am kind of alone in this Holy War :D

He doesn't, he just doesn't want to agree with pmasiar.

---

### Post by pmasiar on 2008-09-30
> **'[CPR]-AL.exe said:**
> Don't really think so. The freedom, you're talking about is a freedom of making mistakes. And that freedom cannot provide you the full control of the CPU and memory while running your program.

You're talking like you like PHP.

Maybe, you suppose, that C doesn't give much freedom and sucks, too?

Do you care to mention which programming languages you fully grok? You seems vary close to a blub programmer. Do you know any languages outside of C family? Do you know any non-procedural language?

Python gives me freedom to focus on solving my problem, by taking care of irrelevant details like types of my variables, and adding powerful syntactic sugar which eliminates lots of textual noise required when programming in languages like C++ or Java. I need full control  of models build from language primitives: the more help I can get from compiler and runtime, the better for me.

BTW I hate PHP, and I loved C 25 years ago when I learned it: it was excellent replacement of ASM back then. But since then, plenty of better languages were designed, and also there is less focus on CPU efficiency, and more focus on efficient use of programmer's time.

C gives you *some* freedom, but ASM gives you more. And Forth gives you both more freedom and more power, but you obviously do not know something as powerful and dangerous as Forth, so it's hard to argue about it - all arguments go high above your head.

Attitude is not a valid replacement for experience 8-)

---

### Post by y-lee on 2008-09-30
> **LaRoza said:**
> He doesn't, he just doesn't want to agree with pmasiar.

:guitar:

> as for the "flexibility" that is "given" here, sorry, that's not what I expect to happen in an OO language

Slavik and [CPR]-AL.exe I am at a complete lose to understand what the problem is here. So python doesn't act as you would think it should, such is life. Object Oriented program does not even have a universally agreed upon **formal** definition and python only supports some of what people consider OO, it is certainly never considered a pure OO language by anyone as far as I know. One is always free to create or use another language. I am just now learning python and I happen to like it, weirdnesses and idioms like this make perfect sense within the context of the language. And in cases where i have felt they didn't make  sense it was me at fault not the language.

---

### Post by [CPR]-AL.exe on 2008-10-05
> You seems vary close to a blub programmer
Pmasiar, you cannot offend me. Even if you would like to.

I just don't know english :D

> BTW I hate PHP
That's enough to respect someone.

~ ~ ~

Anyway, thanks to all of you for the discussion and this small war here. Of course, it changed nothing, but it was fun for a moment here, so I'm quitting that argumentation.


* i just gotta get used to Python *

---

### Post by Wybiral on 2008-10-05
> **slavik said:**
> things like what the OP found in this thread is what annoys me about Python. Imo, anything in the function header has to be declared (as a separate copy).

Correct me if I am wrong, but isn't this a similar situation to when two children inherit a list from a parent, yet one child changes his list and the other child sees it or something of the sort?

No, this isn't a problem with Python, it's a problem with state. This problem exists in all languages. The argument is assigned to an object as a default value... Unfortunately, that object can change, so any time the default value is being used, the mutable object is being used. This is bad. As pmasiar suggested, a better solution is to use a non-mutable object to flag that nothing was passed in (usually the None object).

Or, perhaps the misunderstanding here is the moment in which the code '[]' is executed. Hint: during function-creation, not during each function call, which is what moving the assignment inside the function does (as pmasiar suggested).

---

### Post by pmasiar on 2008-10-05
pmasiar> You seems vary close to a blub programmer

> **'[CPR]-AL.exe said:**
> Pmasiar, you cannot offend me. Even if you would like to.


No, I would not waste time to offend you: I am trying to show you that your approach to understanding new languages limits your use of their features which are new compared to languages you already know. Read the essay (see wikipedia) and become better, more flexible programmer.

---

### Post by pmasiar on 2008-10-05
> **Wybiral said:**
> misunderstanding here is the moment in which the code '[]' is executed. Hint: during function-creation, not during each function call, which is what moving the assignment inside the function does (as pmasiar suggested).

Exactly. Understanding that def statement is also interpreted, and exactly when, is very important to understand how Python works.

---

### Post by [CPR]-AL.exe on 2008-10-06
I've already understand why does it occur :))) There's no need to speak more about it.

But i will leave my point of view with me - i don't like that thing. But rules are rules. Maybe, I'll find some usage for that in future, maybe not. I'll see.


**pmasiar**, thank you. It was some problem of my understanding.



> This problem exists *in all* languages.

Hell, no. As i already said, that that's not the problem (problem or not) of all existing languages.

---

