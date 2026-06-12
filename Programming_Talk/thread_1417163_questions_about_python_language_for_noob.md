---
title: "questions about python language for noob"
date: 2010-02-27
forum: Programming Talk
---

### Post by XXMy_Little_ShinigamiXX on 2010-02-27
hey i have a couple of questions about python, some definitions, questions about classes mainly. i really dont understand why they are there and what do they do. im learning right now from an online tutorial but that doesnt explain much. this is a small class i wrote;
[COLOR=RoyalBlue]
class multiply:
 i = 2
 x = int(raw_input('please enter a number'))
 result = x*i
 def multi(x, i): return x, 'multiplied by', i, '=', result[/COLOR]

now this is where things get kind of confusing. i guess classes arent like functions where you input args and kwargs to call them, i guess you use the word self somewhere in there and python not only calls it somehow but auto assumes a value? how does the [COLOR=RoyalBlue]self[/COLOR] function work? also a quesiton about variables. because you have a class hosting a function, both can have variables like stated above. the whole idea behind this class is that once you call it it is going to ask you to input a number for the value of x. after which x is mulitplied by i and then prints the result. as you can see though i have the variables i, x, and result above the function and the function is trying to use them.. can i do this and still have it work? if i did this another way to give you more perspective it would be like this;

[COLOR=RoyalBlue]def multiply(x, i):
 try:
  x = int(raw_input('please enter a number'))
  i = 2
  result = x * i
  print 'when', x, 'is multiplied by', i, 'the result is', result
 except value error as err:
  print 'please enter a number value', err
 finally:
 pass[/COLOR]

looking at the above coding you can see it is a function with no class, however i added the arguments in the function and defined them as well, again below where the function value is being defined not above it. so if i take and add variable values to the class liek the first example does the function inside the class share those values?

this txt comes directly from the online tutorial:
A *namespace* is a mapping from names to objects. Most namespaces are currently implemented as Python dictionaries, but that&#8217;s normally not noticeable in any way (except for performance), and it may change in the future.  Examples of namespaces are: the set of built-in names (functions such as [abs()]("http://docs.python.org/library/functions.html#abs"), and built-in exception names);

what is a namespace? is it like that space in the parenthesis of the built in function abs()? and im assuming by implanted as python dictionaries if lets say i did this;
[COLOR=RoyalBlue]account = {'jack': 40.98, 'mark': 79.03}[/COLOR]
 lets say in this dictionary would in between the {}s everything included be a name space? or do they mean theyre built in as python dicitonaries like you can import them? like how you can import __builtin__ or math?

By the way, I use the word *attribute* for any name following a dot &#8212; for example, in the expression z.real, real is an attribute of the object z.  Strictly speaking, references to names in modules are attribute references: in the expression modname.funcname, modname is a module object and funcname is an attribute of it. 

in this example he explains how he uses the word attribute for anythign with a dot.. naturally im thinking things like str1.append() and str1.insert() im assuming in this case the .insert and append would be called attributes? the term modules how hes using it here throws me off though.. isnt a module like something you import in? like if i said;
import sys or import madeup those would be whole scripts or functions or what not.. and all of that code put together being imported makes a module right?

Attributes may be read-only or writable.  In the latter case, assignment to attributes is possible.  Module attributes are writable: you can write modname.the_answer = 42.  Writable attributes may also be deleted with the [del]("http://docs.python.org/reference/simple_stmts.html#del") statement.  For example, del modname.the_answer will remove the attribute the_answer from the object named by modname.

what is this about? what does he mean module attributes? does he mean like sys.ps1 or sys.ps2? arent those sub modules?

i dont understand the word scope either, it was given in reference like this;

A *scope* is a textual region of a Python program where a namespace is directly accessible.  &#8220;Directly accessible&#8221; here means that an unqualified reference to a name attempts to find the name in the namespace.

Class objects support two kinds of operations: attribute references and instantiation.(reference)
what in the world are instantiation lol.. 
this is what the book has;

The instantiation operation (&#8220;calling&#8221; a class object) creates an empty object. Many classes like to create objects with instances customized to a specific initial state. Therefore a class may define a special method named [__init__()]("http://docs.python.org/reference/datamodel.html#object.__init__"), like this:
 def __init__(self):
    self.data = []

 
 When a class defines an [__init__()]("http://docs.python.org/reference/datamodel.html#object.__init__") method, class instantiation automatically invokes [__init__()]("http://docs.python.org/reference/datamodel.html#object.__init__") for the newly-created class instance.  So in this example, a new, initialized instance can be obtained by:
 x = MyClass()

 
 Of course, the [__init__()]("http://docs.python.org/reference/datamodel.html#object.__init__") method may have arguments for greater flexibility.  In that case, arguments given to the class instantiation operator are passed on to [__init__()]("http://docs.python.org/reference/datamodel.html#object.__init__").  For example,
 >>> class Complex:
...     def __init__(self, realpart, imagpart):
...         self.r = realpart
...         self.i = imagpart
...
>>> x = Complex(3.0, -4.5)
>>> x.r, x.i
(3.0, -4.5)


 
theyres 2 differnt examples using the __init__.. are those related in someway to calling your class cause it sounds like they are. also what are instance objects?

im very sorry for the long list of questions however this is my first programming language attempt to learn and more of all im a sheltered windows user turned ubuntu so be gentle lol. seriously though if you cant answer them all any helpful insight will be much appreciated :popcorn: thank you.

---

### Post by JDShu on 2010-02-27
Classes are part of a somewhat abstract concept called Object Orientated Programming (OOP), which makes programming easier in some cases. I would advise that you figure out what OOP is before diving into the implementation in Python.

wiki might be a good place to start:
[http://en.wikipedia.org/wiki/Object-oriented_programming](http://en.wikipedia.org/wiki/Object-oriented_programming)

Alternatively, if you're new to programming, you can skip the OOP part of python for now and go ahead and write programs with what you know. Once you get comfortable with imperative programming (the straightforward way), then you can move on to OOP.

---

### Post by CptPicard on 2010-02-27
Python as a language is actually thoroughly OOP even if you did not create your own types of objects... which is what the class stuff is for, definition of new "types" -- think about how integers, strings, lists are objects in the language, but if you wanted to create something like a rational number with operations on it -- you'd want some definition mechanism to store both the associated data and the operations on that data. This is where you'd need to define your own class.

If I were you I would not worry too much yet about the modules/namespaces/classes/hashes issues... they are very nicely integrated in Python which is one of the reasons why I've always considered Python to be "nicely designed", but understanding it all right now is not needed for you... you'll get it over time.

Quickly described though, a namespace is a collection of names (think variable, function, class names) such that they are distinct from the names in another namespace. That is, "cat" in namespace X is not the same "cat" as the one in namespace Y. This prevents clashes and allows for modularity. In Python, modules and classes provide for the namespacing mechanism, and the reason why they are implemented as hashes is just very natural -- if you're mapping from names to "things", a hash is the abstraction to use.

The concept of "scope" can be viewed in a couple of different ways... if some particular definition for a name is available at some particular place in a program, it's said to be "in scope". If it is not in scope, you'll get an error saying that "symbol can't be resolved" or something to that effect. From the variable's point of view, its scope is the extent to which it is effective in the program. At maximum we're talking about globals, at minimum we are in some small nested scope inside a loop...

About the "self" variable -- in a lot of OOP languages the self is "implicit", that is, when you are inside a method call, say,

```

object.method()

```

inside the code of "method" you have automatic access to the object "object" which the method was invoked on. In languages like Java and C++, this is called the "this" object. In Python however the coupling between methods and classes is a bit looser (methods can be used independently, functions can be added as methods) so it has been designed so that a Python method explicitly takes the "object the method was invoked on" parameter as the first parameter of the method. So we need to have

```

def method(self):
  ...
  self.x  # this x here is a member of "object"
  ...

```

---

### Post by XXMy_Little_ShinigamiXX on 2010-02-27
oh my gosh thank you so much for taking the time for such a long response. :KS
im just going to verify real quick to make sure i understand some of them lol.

> **CptPicard said:**
> [COLOR=RoyalBlue]Python as a language is actually thoroughly OOP even if you did not create your own types of objects... which is what the class stuff is for, definition of new "types" -- think about how integers, strings, lists are objects in the language, but if you wanted to create something like a rational number with operations on it -- you'd want some definition mechanism to store both the associated data and the operations on that data. This is where you'd need to define your own class.

If I were you I would not worry too much yet about the modules/namespaces/classes/hashes issues... they are very nicely integrated in Python which is one of the reasons why I've always considered Python to be "nicely designed", but understanding it all right now is not needed for you... you'll get it over time.[/COLOR]

so OOP is object oriented, and from what ive researched python is mostly a scripting language, like web development, maybe some desktop scripts. so to have it be part an OOP language to is kind shocking but thats good right because it means more power. ive also looked up OOP to get an idea of what it is and the difference and from what ive found one of the most popular out there and easiest to learn is a language called visual basic. i suppose in OOP you can design things a lot faster?  so objects in general is almost any piece of code storing something, hence the strings, lists, im assuming among those are dictionaries and tuples as well? as for the get it over time thats great because i have been obsessing with understanding everything in a chapter before i move on, so ill just move forward with the knowledge i have right now thank you.



> **CptPicard said:**
> [COLOR=RoyalBlue]Quickly described though, a namespace is a collection of names (think variable, function, class names) such that they are distinct from the names in another namespace. That is, "cat" in namespace X is not the same "cat" as the one in namespace Y. This prevents clashes and allows for modularity. In Python, modules and classes provide for the namespacing mechanism, and the reason why they are implemented as hashes is just very natural -- if you're mapping from names to "things", a hash is the abstraction to use.[/COLOR]

so a namespace being a collection of names is why the tutorial said that most name spaces are dictionaries but dont have to be? so if i had for example;
```

[COLOR=RoyalBlue]def function1(cat, dog):
 pass

and 

def function2(cat, dog):
 pass[/COLOR] 

```the cat, dog in the function are called arguments correct? arguments are used in the calling of a function. however function1 and function2 are functions as they are defined but are also namespaces because they hold a collection of names? the cat and dog in function 1 completely are different from function 2 and will be given values when you call the function right? like for example;

[COLOR=RoyalBlue]function1('cat', 'dog')[/COLOR]

now obviously the code isnt going to do anything other than just pass because thats what its supposed to do, but the cat, dog arguments are unique to each namespace? did i say that right? lol also could the cat, dog be called a variable?


> **CptPicard said:**
> [COLOR=RoyalBlue]The concept of "scope" can be viewed in a couple of different ways... if some particular definition for a name is available at some particular place in a program, it's said to be "in scope". If it is not in scope, you'll get an error saying that "symbol can't be resolved" or something to that effect. From the variable's point of view, its scope is the extent to which it is effective in the program. At maximum we're talking about globals, at minimum we are in some small nested scope inside a loop...[/COLOR]

ok so starting extremely simple if i had a dictionary of a list of accounts;
```

[COLOR=RoyalBlue]accounts = {'jack': 40.98, 'mark': 90.29}
[/COLOR]
```the name would be for example jack or mark and the definition for those names would be how much they owe, so that would be in scope right?/ im not sure what globals are too but im sure in time i will. 


> **CptPicard said:**
> [COLOR=RoyalBlue]About the "self" variable -- in a lot of OOP languages the self is "implicit", that is, when you are inside a method call, say,

```

object.method()

```inside the code of "method" you have automatic access to the object "object" which the method was invoked on. In languages like Java and C++, this is called the "this" object. In Python however the coupling between methods and classes is a bit looser (methods can be used independently, functions can be added as methods) so it has been designed so that a Python method explicitly takes the "object the method was invoked on" parameter as the first parameter of the method. So we need to have

```

def method(self):
  ...
  self.x  # this x here is a member of "object"
  ...

```[/COLOR]  

when you said you have automatic access to the object 'object' which the method was invoked on, you mean that method meaning like .append() or .insert()? those are called methods right? the object meaning like lets say i did this;
```

x = ['this', 'is', 'a']

and then i said 

x.append('list')

the result would be 

x = ['this', 'is', 'a', 'list']

```now the object would be the list and the method i used would be the .append('list') right? i read the self has no special meaning in python even though it always shows up blue when im reading the tutorial code, so its obviously very important. by methods can be used independently, you mean things like .append('list') can be used independently? if so how can this be because the .append() has to go to something because it has to have an object to assign the method value to right?.. or am i just wrong on the method idea? is the .append() called something else?
obviously i must have it wrong because you said functions can be added as methods, so how does a function get to be a method? 

EDIT-------------------------
ok a little more info on the method thing lol. turns out the .append and .remove etc.are methods so scratch that lol. this is like a different kind of method i found this example on the internet maybe i can show you im sure this is what you mean.

class MyClass:
    """A simple example class"""
    i = 12345
    def f(self):
        return 'hello world'
then we said

x = MyClass
and x.f() 

this of course makes sense because the value i is defined under MyClass. also the f comes in as that is the function we have chosen to define in MyClass. now because defining a funciton requires an argument we gave it the self argument. now were going to do this.

xf = x.f
while True:
    print xf()


now in this were saying that xf is now equal to our value x.f. now the 
thing here is that we arent giving the function f any arguments when we call
it. were doing that to MyClass.f(x) correct? so technically it does have an 
argument. this is what i found, 

In general, calling a method with a list of *n* arguments is equivalent to calling
the corresponding function with an argument list that is created by inserting
the method&#8217;s object before the first argument.

so is x or f the method and which is the object? if im reading this right, 
x is the object and f the method? or is it reverse lol.


thank you for your responses they are much appreciated :popcorn:

---

