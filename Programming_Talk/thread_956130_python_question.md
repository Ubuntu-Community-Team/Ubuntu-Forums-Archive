---
title: "python question"
date: 2008-10-22
forum: Programming Talk
---

### Post by mosty friedman on 2008-10-22
hey everyone,
i'm currently learning python and i have known that it doesnt enforce you to specify a data type for your variables unlike java or C/C++ for example.. so i have this question what if i want to write a function in python that would work with integers, if the user passes a String as an argument the interpreter will not issue an error but the output will be incorrect, so isnt it a good thing after all to enforce the user to declare a data type???..

---

### Post by LaRoza on 2008-10-22
> **mosty friedman said:**
> hey everyone,
i'm currently learning python and i have known that it doesnt enforce you to specify a data type for your variables unlike java or C/C++ for example.. so i have this question what if i want to write a function in python that would work with integers, if the user passes a String as an argument the interpreter will not issue an error but the output will be incorrect, so isnt it a good thing after all to enforce the user to declare a data type???..

No.

Python is dynamically typed and strictly typed.

If you try to do things that don't work with a type, it will throw an exception, a "TypeError".

C doesn't enforce datatypes, which is weak typing (Perl and PHP do this as well).

---

### Post by y-lee on 2008-10-22
> **mosty friedman said:**
> ...so i have this question what if i want to write a function in python that would work with integers, if the user passes a String as an argument the interpreter will not issue an error but the output will be incorrect, so isnt it a good thing after all to enforce the user to declare a data type???..

you actually can test the type of a variable in python 

```
>>> a = 12
>>> b = 12.5
>>> c = "hello"
>>> print type(a), type(b), type(c)
<type 'int'> <type 'float'> <type 'str'>
>>> print isinstance(a, int)
True
>>>

```

But in reality there are *very few occasions* where this is a good idea. It is considered unpythonic and coding like that is coding in a C or C++ style in python. It is far better to avoid it and learn to code in a python like style. I wanted to do that too at first, check types and code in a C style. Now i love the freedom python gives :)

---

### Post by LaRoza on 2008-10-22
> **y-lee said:**
> you actually can test the type of a variable in python 


And that shows that the Python way is somewhat better than the C way.

In C:
```

int x; 

```
means that enough memory was allocated for an int (which varies). That doesn't meant it will be enforced.

In Python:

```

x = 1

```
means that x is an integer and equals 1. It has a type and that type is enforced. The fact you don't explitly declare the type doesn't mean anything. When you use the variables you just use "x" anyway. Declaring data types is for the compiler, not the programmer.

---

### Post by ghostdog74 on 2008-10-22
> **LaRoza said:**
> And that shows that the Python way is somewhat better than the C way.

what do you mean by that? static and dynamic types both have their pros and cons. There's really no way to tell which is better

---

### Post by y-lee on 2008-10-22
> **LaRoza said:**
> And that shows that the Python way is somewhat better than the C way.


Well I am believer and think dynamically typed languages are far easier to code in. C does what it was designed to do very well but it can make it very hard on the programmer. Python while not perfect is one the best and easiest languages I have ever coded in :)

---

### Post by LaRoza on 2008-10-22
> **ghostdog74 said:**
> what do you mean by that? static and dynamic types both have their pros and cons. There's really no way to tell which is better
I said "somewhat", meaning "can be". Dynamic typing is preferable to static typing, unless you need static typing IMO. There is no need to explicitly give types to variable when the type can be determined by the data, and such a feature wouldn't lead to issues.

---

### Post by newbuntuxx on 2008-10-23
i recommend that you always treat the user's input as String, even though what is being asked is an integer. I think its easier for checking syntax if the input is correct. And you can easily extract your int by type casting..

int(string)

---

### Post by nvteighen on 2008-10-23
> **mosty friedman said:**
> hey everyone,
i'm currently learning python and i have known that it doesnt enforce you to specify a data type for your variables unlike java or C/C++ for example.. so i have this question what if i want to write a function in python that would work with integers, if the user passes a String as an argument the interpreter will not issue an error but the output will be incorrect, so isnt it a good thing after all to enforce the user to declare a data type???..

Python will raise an exception whenever you do something not permitted, and you can always prevent that to crash the program by catching the exception. But I fear that if your function uses an operator like +, which is overloaded to work with several data types, maybe you could end up with weird results... In those (few) cases, maybe using type() to detect data type and raising an exception when you consider them not correct may be the way to go.

---

### Post by mosty friedman on 2008-10-23
what i'm talking about guys is, lets say i want to write a method that would take two arguments
```

def function( a, b ):
    return a*b

```
if i pass a string and an integer to the method, it will give me an output which is just the String repeated 'b' times..and if i pass in two integers, it will return the multiplication of both integers..which means that the function will produce an output either ways but it will not always return a valid output, depending on the inputs.. and as far as i know the user can pass any inputs..when i used to code in java, the arguments to a method had to match the elements in the parameter list so the output was always valid...how do i ensure a valid output in python??

---

### Post by LaRoza on 2008-10-23
> **mosty friedman said:**
> what i'm talking about guys is, lets say i want to write a method that would take two arguments
```

def function( a, b ):
    return a*b

```
if i pass a string and an integer to the method, it will give me an output which is just the String repeated 'b' times..and if i pass in two integers, it will return the multiplication of both integers..which means that the function will produce an output either ways but it will not always return a valid output, depending on the inputs.. and as far as i know the user can pass any inputs..when i used to code in java, the arguments to a method had to match the elements in the parameter list so the output was always valid...how do i ensure a valid output in python??

* and + work with strings. * will multiply the string, and + will concatenate. This isn't a type fail, but an overloaded operator. 

Check types before using the data. 

[http://www.python.org/doc/2.5.2/lib/string-methods.html](http://www.python.org/doc/2.5.2/lib/string-methods.html)

You can use exceptions also.

---

### Post by Vox754 on 2008-10-23
> **mosty friedman said:**
> 
...
..which means that the function will produce an output either ways but **it will not always return a valid output**, depending on the inputs.. and as far as i know the user can pass any inputs..when i used to code in java, the arguments to a method had to match the elements in the parameter list **so the output was always valid...how do i ensure a valid output in python??**

YOU ARE WRONG!!!

Why do you think the result is invalid?! It is a perfectly valid result in Python!

Maybe in Java it is not possible to concatenate strings like this, but in Python you can, so **it is not a bug but a feature.**
As you realized you can multiply strings, integers or floats with the same '*' operator. The flexibility to do things like this is what makes Python a great language.

But, why would you like to concatenate strings like this? Isn't it complicated and counterintuitive? Well, maybe at this point in time you think so, but that's because you haven't had a problem in which you could apply these tricks.


In order to solve your problem you would do something like this
```

# this is pseudocode
def function( a, b ):
    if (a is not number) OR (b is not number):
        return "Wrong input"
    
    return a*b

```

For this simple example it may look like the type checking of statically typed languages would be better:
```

# this is pseudocode
def function( int a, int b ):
    return a*b

```

However, remember that the keyword in Python is *'dynamic'*. You can dynamically try different stuff, and change your code as you need. Emphasis is not on writing each line of code perfectly, but on testing the code thoroughly until it works as you expect. And remember: you have all the power to make it work incorrectly!

Once you get a prototype running, maybe working only for integers, you can add type checking and handle exceptions. You can even port your prototype to C or Java or any other statically typed language once you know your algorithms work.

---

### Post by pp. on 2008-10-23
> **Vox754 said:**
> YOU ARE WRONG!!!

Why do you think the result is invalid?! It is a perfectly valid result in Python.

Obviously, OP intended to say that the valid result of the overloaded operation tends to be useless in some situations. 

Once you have inserted a data item of an unexpected type into a program, finding the cause of unexpected results can become quite a nightmare because so many intermediate expressions can apply overloaded operators.

For someone accustomed to strict type checking at every step in a program, this can be something of an unexpected side effect of the more liberal handling such as encountered in Python.

Careful placement of statement for vetting your input all of a sudden becomes overridingly important.

---

### Post by LaRoza on 2008-10-23
> **Vox754 said:**
> 
Maybe in Java it is not possible to concatenate strings like this, but in Python you can, so **it is not a bug but a feature.**


I would also like to point out that Python is strongly typed. So in a weakly typed language, like Perl or PHP:
```

"2" + 2

```
Is valid, and I am not sure if you will get "22" or 4.

In Python, that is invalid. You can + strings or numbers, not both.

The better way to handle it, instead of having multiple return values, is to use exceptions.

---

### Post by y-lee on 2008-10-23
> **mosty friedman said:**
> what i'm talking about guys is, lets say i want to write a method that would take two arguments
```

def function( a, b ):
    return a*b

```
if i pass a string and an integer to the method, it will give me an output which is just the String repeated 'b' times..and if i pass in two integers, it will return the multiplication of both integers..which means that the function will produce an output either ways but it will not always return a valid output, depending on the inputs.. and as far as i know the user can pass any inputs..when i used to code in java, the arguments to a method had to match the elements in the parameter list so the output was always valid...how do i ensure a valid output in python??

We have already gave you enough information to answer this yourself. But if you insist here goes, suppose you wish function to only handle *ints*, then :

```
def function( a, b ):
    if isinstance(a,int) and isinstance(b,int):
        return a*b
    else:
        raise TypeError

# in code that uses function
a = 2
b = 3
try:    
    c = function(a, b)
    print a, b, c
except TypeError:
    print a, b, "opps: Type Error"
    
```

I happen to like exceptions, but if that bothers you then here is another approach based on *if thens*:

```
def function( a, b ):
    if isinstance(a,int) and isinstance(b,int):
        return a*b
    else:
        return None

# in code that uses function
a = 2
b = 'what'
ans = function(a,b)
if ans:
    print a, b, ans
else:
    print a,b, "opps: Type Error"
```

However, the problem with both these approaches is it clutters up your *function(a,b)* definition with type checking code, imho, it would be better to separate that from the function as it is irrelevant to it. So here is a decorator string approach to clarify this:

```

def typeisint(func):
    def wrapper(*arg):
        if isinstance(arg[0],int) and isinstance(arg[1],int):
            res = func(*arg)
        else:
            res = None
        return res
    return wrapper

@typeisint
def function( a, b ):
    return a*b
    
# in code that uses function
a = 2
b = 'what'
ans = function(a,b)
if ans:
    print a, b, ans
else:
    print a, b, "opps: Type Error"
```

Clearly I could make the decorator string approach work with the *try except* code above but I will forgo that to discuss one minor problem with this so far, what if you change *function(a,b)* to *function(a,b,c)*?

It would better if *typeisint(func)* were more general, so here ya go:

```
from operator import and_

def typeisint(func):
    def wrapper(*arg):
        if reduce(and_, [isinstance(a,int) for a in arg]):
            res = func(*arg)
        else:
            res = None
        return res
    return wrapper

@typeisint
def function( a, b, c ):
    return a*b*c
    
# in code that uses function
a = 2
b = 3
c = 'a'
ans = function(a,b,c)
if ans:
    print a,b,c,ans
else:
    print a,b,c,  "opps: Type Error"
```

I hope you get the idea and this helps :)

---

### Post by nvteighen on 2008-10-23
> **Vox754 said:**
> YOU ARE WRONG!!!


I kindly advice you to not write that way... even when you are right! ;)

---

### Post by LaRoza on 2008-10-23
> **nvteighen said:**
> I kindly advice you to not write that way... even when you are right! ;)

YOU ARE RIGHT!

[color="white"]small letters[/color]

---

### Post by nvteighen on 2008-10-23
> **LaRoza said:**
> YOU ARE RIGHT!

[color="white"]small letters[/color]
I'll report you for bad joke...

---

### Post by LaRoza on 2008-10-23
> **nvteighen said:**
> I'll report you for bad joke...

I'll ban you, as a good joke (well, for me).

---

### Post by mosty friedman on 2008-10-23
> 
YOU ARE WRONG!!!

Why do you think the result is invalid?! It is a perfectly valid result in Python!

i'm not saying that it is a bug in python, i know that the output is correct, all i'm saying is that its not what the user wants..if the user wants a function that multiplies INTEGERS and not STRINGS then if by mistake someone inputs a string it will return an output that is not desireable but that doesnt mean that it is an invalid output... thanks for all the feedback though :D

---

### Post by CptPicard on 2008-10-23
> **mosty friedman said:**
> i'm not saying that it is a bug in python, i know that the output is correct, all i'm saying is that its not what the user wants..if the user wants a function that multiplies INTEGERS and not STRINGS then if by mistake someone inputs a string it will return an output that is not desireable

Well, it's just something the user has to understand and want.. ;) The genericity of Python is one of its strong points, duck typing and all... as long as whatever objects you have on hand, as long as they can be applied to whatever operations you try on them, everything is fine and dandy...

---

### Post by Vox754 on 2008-10-23
> **pp. said:**
> Obviously, OP intended to say that the valid result of the overloaded operation tends to be useless in some situations. 

Of course he meant that, I was just reinforcing the fact that people should not think that one construct in a given language should behave the same way in another language, after all, they are different languages.
I was also being picky with the chosen words of the result "being invalid".

> 
For someone accustomed to strict type checking at every step in a program, this can be something of an unexpected side effect of the more liberal handling such as encountered in Python.

Yes, and then is when one needs to start thinking differently.
People coming from that world should try to relax a little, realizing that they can use their time to implement new functionality in their code without resorting to checking the type of every variable they use.

---

### Post by Vox754 on 2008-10-23
> **y-lee said:**
> We have already gave you enough information to answer this yourself. But if you insist here goes, suppose you wish function to only handle *ints*, then :
...
So here is a decorator string approach to clarify this:
...
I hope you get the idea and this helps :)

Yeah...
I'm pretty sure that was the short explanation.

Talking seriously, I don't think you should scare new users like that!
Let them discover exception handling at their own pace, otherwise your code, or all written code eventually, would lead to an explosion of "try... except...", not gaining much from the dynamic characteristic of the language.

---

### Post by Vox754 on 2008-10-23
> **mosty friedman said:**
> i'm not saying that it is a bug in python, i know that the output is correct, all i'm saying is that its not what the user wants..

I know, I'm just being picky in the way you used your words, specially "invalid".
If you enter a string and you get a Double Falcon Pawnch Collision and the whole universe is destroyed, that I'd call "invalid".

> 
... if the user wants a function that multiplies INTEGERS and not STRINGS then if by mistake someone inputs a string it will return an output that is not desireable but that doesnt mean that it is an invalid output...

The user wants what he wants. If the user wants potatoes, he wants exactly that.

It is not the user's job, nor the programming language's job to do it, but the programmer who has to implement it correctly in whatever language he chooses to use.
"If by mistake someone inputs a string" then you, the programmer, have to handle that accordingly.

```

def function(args):
    if args is not valid:
        return "YOU ARE WRONG! Read the manual on how to use this function!!!"

    return YOU_ARE_RIGHT!

```

---

### Post by y-lee on 2008-10-23
> **Vox754 said:**
> 
[QUOTE=y-lee;6020240]We have already gave you enough information to answer this yourself. But if you insist here goes, suppose you wish function to only handle *ints*, then :

So here is a decorator string approach to clarify this:

I hope you get the idea and this helps :)
Yeah...
I'm pretty sure that was the short explanation.

Talking seriously, I don't think you should scare new users like that!
Let them discover exception handling at their own pace, otherwise your code, or all written code eventually, would lead to an explosion of "try... except...", not gaining much from the dynamic characteristic of the language.[/QUOTE]

Hmm actually that was the short version, I did not continue in the generalizing the decorator string type check function. I could have tried to make it really general. Nor did I even mention the various problems one might have with decorators or how to deal with them. 

But I have already said in this thread: 

> **y-lee said:**
> you actually can test the type of a variable in python 

But in reality there are *very few occasions* where this is a good idea. It is considered unpythonic and coding like that is coding in a C or C++ style in python. It is far better to avoid it and learn to code in a python like style. I wanted to do that too at first, check types and code in a C style. Now i love the freedom python gives :)

And I stick by that despite posting code showing various approaches to type checking. I *seriously doubt* the code the OP is working on needs type checking, user input should be checked before it is passed to whatever functions need it and if necessary exceptions should be used sparingly to deal with pathological cases or whatnot. I *fully agree* one should take advantage of pythons "dynamic nature" and not code like one would code in C or Java :)

As to scaring new users, I myself am a new user of python, but not new to coding. And honestly I wish not so many python tutorials and books online were so dumbed down. I benefit more learning python by examples of *real* code and *real* problems and not stuff wrote for a third grader. My first day of learning python I was using exceptions, obviously to me handling errors is one of the first things one needs to learn in using a new language. That and all the other *basic* topics, defining functions and variables and classes and how to do loops and recursion and ...

Anyway thanks for your opinion.

---

### Post by newbuntuxx on 2008-10-24
I would do it this way:

```
def multiply (a,b)
   if not a.isdigit or (not b.isdigit):
       return "Bad Entry"
   return in(a) * int(b)
```

---

### Post by ghostdog74 on 2008-10-24
> **newbuntuxx said:**
> I would do it this way:

```
def multiply (a,b)
   if not a.isdigit or (not b.isdigit):
       return "Bad Entry"
   return in(a) * int(b)
```

```

if False not in map(str.isdigit,[a,b]):
   print "ok"

```

---

### Post by LaRoza on 2008-10-24
> **newbuntuxx said:**
> I would do it this way:

```
def multiply (a,b)
   if not a.isdigit or (not b.isdigit):
       return "Bad Entry"
   return in(a) * int(b)
```
That won't work, besides the typo.

isdigit() only works on strings, so if someone is passing numbers to this function, it will throw an exception. A function named "multiply()) should get numbers I think...

Also, that fails if the strings are not ints. So "10.9" would be another number and throw the results off.

---

### Post by nvteighen on 2008-10-24
> **y-lee said:**
> 
As to scaring new users, I myself am a new user of python, but not new to coding. And honestly I wish not so many python tutorials and books online were so dumbed down. I benefit more learning python by examples of *real* code and *real* problems and not stuff wrote for a third grader. My first day of learning python I was using exceptions, obviously to me handling errors is one of the first things one needs to learn in using a new language. That and all the other *basic* topics, defining functions and variables and classes and how to do loops and recursion and 

+1

Inductive learning (i.e. by working on *real examples*) is really a powerful method to learn, specially languages (of any kind). Of course, you just can't tell a raw beginner what an exception is if he/she doesn't know what's a variable, but you should be able to confront the student with real issues and real solutions instead of lab-created examples...

EDIT: By the way, I'd just use type() to check the data type...

---

