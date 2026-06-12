---
title: "this doesnt make sense, Def, and return, etc"
date: 2010-05-04
forum: Programming Talk
---

### Post by makuab on 2010-05-04
im following this guide [http://hetland.org/writing/instant-hacking.html](http://hetland.org/writing/instant-hacking.html)

```

def floor(number):
    result = 0
    while result <= number:
        result = result+1
    result = result-1
    return result
```above doesnt make any sense to me, i dont understand functions at all...does it
multiply floor*number? or make it equal or what?

---

### Post by schauerlich on 2010-05-04
It's defining a "floor" function, which takes a decimal number and returns the greatest integer less than that number. In effect, you're "chopping off the decimal" part of a number - floor(3.1) is 3; floor(5.9) is 5; and so on.

A function is essentially a reusable piece of code, which you can give different inputs so it'll act differently depending on what you tell it to do. In this case, it takes a number, and spits another number back out (the "floor" of that number).

What this does is starts from 0 and increases the number (result) until it is no longer less than or equal to the original number. It then subtracts 1, and returns that value. For instance, say the number you put in is 3.1. The function would start at 0, and ask if that's less than your starting number (3.1); since it it, it increases it. Then it asks if 1 is less than 3.1. It is, so increase it... and so on until you get to 4. 4 is no longer less than 3.1, so it breaks out of the loop and then subtracts 1 to get 3, which it returns.

---

### Post by |Porsche on 2010-05-04
number in this case is an argument to the function. 

[http://www.ibiblio.org/swaroopch/byteofpython/read/function-parameters.html](http://www.ibiblio.org/swaroopch/byteofpython/read/function-parameters.html)

For more info. 

Basically, the function is using the value of number which it got from some other place to do what it has to do which is return result.number is a variable name which can have any value depending on what is going on with the program/script.

---

### Post by makuab on 2010-05-04
> **schauerlich said:**
> It's defining a "floor" function, which takes a decimal number and returns the greatest integer less than that number. In effect, you're "chopping off the decimal" part of a number - floor(3.1) is 3; floor(5.9) is 5; and so on.

A function is essentially a reusable piece of code, which you can give different inputs so it'll act differently depending on what you tell it to do. In this case, it takes a number, and spits another number back out (the "floor" of that number).

What this does is starts from 0 and increases the number (result) until it is no longer less than or equal to the original number. It then subtracts 1, and returns that value. For instance, say the number you put in is 3.1. The function would start at 0, and ask if that's less than your starting number (3.1); since it it, it increases it. Then it asks if 1 is less than 3.1. It is, so increase it... and so on until you get to 4. 4 is no longer less than 3.1, so it breaks out of the loop and then subtracts 1 to get 3, which it returns.

i dont understand 
def floor(number):

what are the parenthesis for? do they mean its multiplying?

---

### Post by |Porsche on 2010-05-04
It has nothing to do with math. I just the syntax of the language.

---

### Post by schauerlich on 2010-05-04
> **makuab said:**
> i dont understand 
def floor(number):

what are the parenthesis for? do they mean its multiplying?

The parentheses surround the arguments to the function. The arguments are the "input". The reason it says "number" is because you're telling python that you want to call the first argument to that function "number" when you use it in your code.

```
def floor(number):
---> Define a function called floor, with one argument, named "number"
```

You can also have more than one argument, in which case you put a comma in between them.

```
def fry(eggs, spam):
---> Define a function called fry, with two arguments: one named "eggs" and the
     other named "spam"
```
Call the function like this:
```
fry(4, 2)
```
That will run the function "fry," using 4 and 2 where you put "eggs" and "spam", respectively.

---

### Post by makuab on 2010-05-04
> **|Porsche said:**
> It has nothing to do with math. I just the syntax of the language.
I just dont understand why its there!

---

### Post by makuab on 2010-05-04
```
def hello(who):
    print "Hello,", who

hello("world")
# Prints out "Hello, world"
```i also dont understand this... its so confusing :(

because if its hello(who), wouldnt it print hello, hello?

---

### Post by schauerlich on 2010-05-04
> **makuab said:**
> ```
def hello(who):
    print "Hello,", who

hello("world")
# Prints out "Hello, world"
```i also dont understand this... its so confusing :(

because if its hello(who), wouldnt it print hello, hello?

First, you define a function called "hello" which takes one argument. You'll call this argument "who".

When you call the function, you hand in the string "world" to the function. The function then runs, with the value of the variable named "who" used wherever its name appears. In this case, you said you wanted "who" to contain the string "world", so it printed out "Hello, world".

What do you think would happen if you said
```
hello("makuab")
```

?

---

### Post by makuab on 2010-05-04
> **schauerlich said:**
> First, you define a function called "hello" which takes one argument. You'll call this argument "who".

When you call the function, you hand in the string "world" to the function. The function then runs, with the value of the variable named "who" used wherever its name appears. In this case, you said you wanted "who" to contain the string "world", so it printed out "Hello, world".

What do you think would happen if you said
```
hello("makuab")
```?


hello makuab?

where does it say that it put the string world in who?

---

### Post by makuab on 2010-05-04
i think i might understand it now

```
def hello(c):
    print "Hello,", c

hello("a")
# Prints out "Hello, a"

```

pretty much the (c) corresponds with the ("a")?

---

### Post by makuab on 2010-05-05
bump, eager to resume

---

### Post by lavinog on 2010-05-05
If it doesn't make sense, it might help to try some different reading material:
[http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python](http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python)

Something else that you might be missunderstanding is variable scope.
For example the c variable in your hello(c) function does not exist outside of the function...so if you do a print c outside of the function...you will get an error.

---

### Post by Reiger on 2010-05-05
Perhaps you will understand this somewhat better in a more mathematical notation:

```

def func(x) :

```
Means:
```

let `func' be a function which takes a variable `x' and is defined as:

```

And hence:
```

result = func(x)

```
Means:
```

let `result' be the value of the function `func' applied to the value of `x'

```

And consequentially:
```

result = func(42)

```
Means:
```

let `result' be the value of function `func' applied to 42

```

---

### Post by soltanis on 2010-05-05
A function is a little machine that takes something you put in it and transforms it and spits it out. The things you give it are called "inputs" or "parameters"; the function output is called the "result" or "value of the function at the input".

Functions operate on their inputs according to rules. As a programmer, you tell the computer what these rules are, and it manipulates the inputs accordingly.

```

def identity(x):
  return x

```

This is the definition of the identity function; for every x you give as its input, the value of the function at x is x itself.

In particular,

```

x = identity(x)

```

Is always true. If you want to check this, type that function into python, then try typing this:

```

>>> 1 == identity(1)

```

You will find that Python informs you this is "True". Check for yourself that this is always the case, no matter what you put in the parenthesis.

By the way, "x" in the function stands for the function's "variable". Functions of a single variable (like the identity function) have only one input. If you haven't taken algebra yet, and don't understand the concept of a variable, you should either teach yourself that now, or wait until you learn it.

---

### Post by schauerlich on 2010-05-05
> **makuab said:**
> where does it say that it put the string world in who?

You never really come out and say it - but think about "world" taking the place of who. When you are defining it - that is, telling python "this is what the function 'hello' is supposed to do" - you put who there as a placeholder name. When you want to actually USE the function, you put something in that place. That something is the string "world".

---

### Post by makuab on 2010-05-05
this is so frustrating..
I still dont understand it.
I feel really stupid :(

let me try and explain what this is saying to me
```

def absolute_value(n):
    if n < 0:
        n = -n
    return n

```absolute_value contains these instructions
if n is greater than 0 then n equals -n
change the value of n back to its original value

what is the value of n?!

the hardest part for me to understand is 
```
def absolute_value(n):
```

---

### Post by CptPicard on 2010-05-05
There is a slight weirdness in that function in the sense that it reassigns the function parameter binding... but, I have a feeling that you simply don't understand the concept of function. From math class, do you remember what it means to do

```

f(x) = x+5

```

And then, what would

```

f(5)

```

then be?

Equivalently in Python we have

```

def f(x):
  return x + 5

```

---

### Post by schauerlich on 2010-05-05
> **makuab said:**
> let me try and explain what this is saying to me
```

def absolute_value(n):
    if n < 0:
        n = -n
    return n

```absolute_value contains these instructions
if n is greater than 0 then n equals -n
change the value of n back to its original value

Think of a variable as a box with a name on it. You can put different things in this box (but only one thing at a time), and you can always refer to the box by the same name.

Allow me to translate.

"Define a function named absolute_value. When someone wants to use this function, they should give it one value. Whatever value they give us, we'll store in a box called 'n'. If the value that's in the box is less than zero, then we should take the number out, make it the opposite sign, and stick it back in the box. At the very end, we should take out whatever value is in the box and hand it back to the person who used the function."

What that "return" means is that you want to return the value of n (after you've possibly changed it) to whoever used the function. This function is saying "give me one value. I'll do something with it, and in the end, I'll return a value to you."

> the hardest part for me to understand is 
```
def absolute_value(n):
```

The def part means "define". It's telling python that you want to define a function. absolute_value is the name of the function, and n is the name of a variable that you need to supply a value for when you use the function.

---

### Post by makuab on 2010-05-05
> **CptPicard said:**
> There is a slight weirdness in that function in the sense that it reassigns the function parameter binding... but, I have a feeling that you simply don't understand the concept of function. From math class, do you remember what it means to do

```

f(x) = x+5

```And then, what would

```

f(5)

```then be?

Equivalently in Python we have

[code]
def f(x):
  return x + 5
[code]

i think thats my problem, i've only taken algebra 1

f(x) = x+5 i dont know how to solve that.. what would you call it?

---

### Post by CptPicard on 2010-05-05
> **makuab said:**
> 
f(x) = x+5 i dont know how to solve that.. what would you call it?

A function *definition*. "f" is a value dependent on the value x, which is the function's "parameter". Since f(x) = x+5, then, for example for the value x = 5, f(5) = 5 + 5 = 10.

A much nicer definition for the abs function is, by the way:

```

def abs(x):
  if x < 0:
    return -x
  else:
    return x

```

This avoids the reassignment of the parameter which you may be finding confusing.

---

### Post by trent.josephsen on 2010-05-05
First, I'll assume you are already familiar with variables and values and control flow -- if these things are alien to you then you should learn a little more about programming in general, and Python in particular, before starting to write your own functions.

If you've taken any algebra courses, you'll be familiar with the mathematical meaning of "function".  For example, the identity function, f(x) = x, "takes" as its argument some value x and "returns" the same value.  More interestingly, the doubling function g(x) = 2x takes a value x and returns the number that is twice x:

g(1) = 2
g(2) = 4
g(0.5) = 1

The parentheses are just a way of saying "Evaluate the function g, replacing x with this particular value."  It's a convention that goes back to the 17th century at least.  It's not related to multiplication.

We can use functions in programming, and specifically in Python, in the same way.  This is the definition of the doubling function in Python:

```
def g(x):
    return 2*x
```

This is equivalent to the mathematical definition g(x) = 2x.  The parentheses after "g" hold a list of "arguments" or "parameters" to the function -- they tell Python that the function named g takes one argument, which is referred to within the function as x.

The return statement causes the function to return the value 2*x.

Let's look at what happens when we use this function:

```
print g(3)
```

Python recognizes g(3) as the syntax of a function call.  (There's no implicit multiplication in Python, so that can't be it.)  Python then looks for the function that goes by the name g.  It finds our definition (above).  Now Python copies the 3, which is the "actual" parameter of the function (the value it was called with) into the variable x, which is the "formal" parameter (the variable used to hold the actual parameter within the definition of the function).

Now the flow of the program jumps from the line where you wrote g(3) to the first line of the function g.  So now you're executing everything in the function just as if it were in line with the rest of your code, but the variable x has been magically set to the value 3 -- even though you never explicitly wrote x = 3 in your program.  That's what Python does behind the scenes.

Now Python evaluates the expression 2*x, and since x holds the value 3, it gets 6.  The return statement causes the control flow to jump back to the place where you called the function.  But because you put an expression after 'return', the function call is replaced by the value of the expression -- that is, 6.  So "print g(3)" is the same in this context as writing "print 6".  The function call "evaluates" to 6.

In your hello function, the function doesn't explicitly use the return keyword, and so if you were to use it in an expression, it would be the built-in value None.  This is a Python-specific feature.  However, the hello function is a little more interesting because it has a side effect -- printing a message to the console.  And because the formal parameter (below, called name) is replaced by the actual parameter, you can call the hello function with any name you want.

```
def hello(name):
    print 'Hello,', name

hello('Joe')  # same as print 'Hello,', 'Joe'
hello('world') # same as print 'Hello,', 'world'
myName = raw_input('What is your name? ')
hello(myName) # same as print 'Hello,', myName

```

---

### Post by makuab on 2010-05-05
> **makuab said:**
> i think thats my problem, i've only taken algebra 1

f(x) = x+5 i dont know how to solve that.. what would you call it?

> **CptPicard said:**
> A function *definition*. "f" is a value dependent on the value x, which is the function's "parameter". Since f(x) = x+5, then, for example for the value x = 5, f(5) = 5 + 5 = 10.

A much nicer definition for the abs function is, by the way:

```

def abs(x):
  if x < 0:
    return -x
  else:
    return x

```This avoids the reassignment of the parameter which you may be finding confusing.


what exactly does 

```

def abs(x):
  if x < 0:
    return -x
  else:
    return x
```

do?

what is an argument?
what does return do?

Please explain things in words i can understand..


i have not learned about functions yet, thats probably why im so lost.

---

### Post by makuab on 2010-05-05
I know you guys are trying hard, and I thank you for that. I just cant seem to understand this.

---

### Post by lisati on 2010-05-05
You might want to think of a function as a kind of shorthand.

Often in a programming project you will want to do the same kind of calculation or other stuff on different pieces of information in different parts of your project. 

What a function does is give you a way of coding "this is how you do this" once and use a reference to the function instead of rewriting the same code over and over again. 

When your program encounters a "function call", it takes a breather from what it's doing, makes a note of where it's up to, and goes off and does whatever the function tells it it. The idea of the "return" is to tell the function, "we're finished here, let the main part of the program continue". 

When we talk of "arguments" and "parameters" for the function we are talking about how we tell the function which information we want the function to do its work with.

Hope this helps.

---

### Post by makuab on 2010-05-05
so should i give up on programming?
try to use functions?
skip functions?

---

### Post by schauerlich on 2010-05-05
> **makuab said:**
> so should i give up on programming?
try to use functions?
skip functions?

Functions are a very important part of nearly every programming language. You definitely shouldn't skip them for good. If you're frustrated, it's okay to take a break and work on other things - but once you feel like giving it another try, you should definitely come back. Sometimes it takes a while to sink it, and it's harder to focus and think when you're overwhelmed.

---

### Post by makuab on 2010-05-05
> **schauerlich said:**
> Functions are a very important part of nearly every programming language. You definitely shouldn't skip them for good. If you're frustrated, it's okay to take a break and work on other things - but once you feel like giving it another try, you should definitely come back. Sometimes it takes a while to sink it, and it's harder to focus and think when you're overwhelmed.
okay.. thanks

---

### Post by CptPicard on 2010-05-05
> **makuab said:**
> so should i give up on programming?

The function concept is central in mathematics too, so I would suggest not give up on this because of it. You'll regret it later on.

> 
try to use functions?
skip functions?

There is no way to skip them.

I do wonder what is so hard about it though. Let's sit in the Python shell for a while... say, I want to have a function that adds 1 to whatever I give it.

```

>>> def add(x):
...     return x + 1
...
>>> add
<function add at 0x7fb38c8c47d0>
>>> add(1)
2
>>> add(2)
3
>>> add(3)
4

```

Works great! Going through the function definition:

```

def add(x):

```

"Add is a function that takes a value, x"

```

return x + 1

```

... and whatever x is, it returns x + 1.

---

### Post by makuab on 2010-05-05
> **CptPicard said:**
> The function concept is central in mathematics too, so I would suggest not give up on this because of it. You'll regret it later on.



There is no way to skip them.

I do wonder what is so hard about it though. Let's sit in the Python shell for a while... say, I want to have a function that adds 1 to whatever I give it.

```

>>> def add(x):
...     return x + 1
...
>>> add
<function add at 0x7fb38c8c47d0>
>>> add(1)
2
>>> add(2)
3
>>> add(3)
4

```Works great! Going through the function definition:

```

def add(x):

```"Add is a function that takes a value, x"

```

return x + 1

```... and whatever x is, it returns x + 1.

now that i can understand, but how can i apply this to the other ones?

---

### Post by CptPicard on 2010-05-05
> **makuab said:**
> now that i can understand, but how can i apply this to the other ones?

I'm not really sure I understand... the core idea is the same, it's just that the function is defined differently?

---

### Post by nvteighen on 2010-05-05
Functions are "machines" that take some stuff, do something inside and spit out something from it. For example,

```

f(x) = x + 5

```

That's read like this: "f" takes "x" and returns "x" splus five. So, if you take, e.g. 50 as your value, then f(50) = 50 + 5 = 55. As you see, the "=" sign in the formula I wrote above is not really the same as the "=" you see in an equation like "x = 3x + 4"... when dealing with "declaring" functions (telling people what's the formula for something), that "=" should be read like "let": "let f to be a function that takes x and results in x + 5".

There are other functions... for example, you could use a function that given a circle's radius, it returns the circle's area... let's call it "circ_area" (r^2 is "r squared"):

```

circ_area(r) = pi * r^2

```

And the area of a rectangle? Well, you need two arguments (two pieces of information): width and length, so:
```

rect_area(w,l) = w * l

```

In programming, functions are essentially the same as the mathematical ones I've shown you. The difference is that you start using some devices for logical control (conditionals, for example) and some other stuff that allow you to do much more complex functions than what I've shown to you.

You're using a certain programming language that's called Python; it's one of a really huge lot of programming languages. So, in Python functions are declared this way:
```

def function_name(argument1, argument2, argument3, ...):
    code

```

For example, the rectangle's area function I wrote above can be translated to Python like this:
```

def rect_area(width, length):
    return width * length

```

What return does is like the equal sign in the previous formulas, it tells you "ok, rect_area is going to spit out whatever width * length is going to be". 

Applying a function is just to see what it returns when giving some values to it. So, "applying" rect_area to a rectangle 5 mts. wide and 2 mts. long will be rect_area(5, 2) and that will return 10 back to you.

---

### Post by schauerlich on 2010-05-05
> **makuab said:**
> now that i can understand, but how can i apply this to the other ones?

Try writing a function that will multiply a number by 4 if the number is greater than 10, and add 3 if it's less than or equal to 10.

---

### Post by makuab on 2010-05-05
before i forget

```

circ_area(r) = pi * r^2
```so circ_area takes the r and puts out pi * r^2?


could i write
```

def circ_area(r):
    return 3.14 * r^2

```

---

### Post by nvteighen on 2010-05-05
> **makuab said:**
> before i forget

```

circ_area(r) = pi * r^2
```

so circ_area takes the r and puts out pi * r^2?

Yes! :)

---

### Post by CptPicard on 2010-05-05
(EDIT n/m didn't read the posts above right)

But anyway, you should try the little "homework assignment" suggested by schauerlich...

---

### Post by makuab on 2010-05-05
> **schauerlich said:**
> Try writing a function that will multiply a number by 4 if the number is greater than 10, and add 3 if it's less than or equal to 10.
```

def multiply(n):
       if n > 10
       return 4 * n
       elif n <= 10
       return n + 3

```

---

### Post by makuab on 2010-05-05
> **nvteighen said:**
> Yes! :)
  wouldn'ti need to tell it what r is?

r = input("enter text here")

or r = ?

---

### Post by CptPicard on 2010-05-05
> **makuab said:**
> wouldn'ti need to tell it what r is?

You'll need to know when you call the function, so eventually, yes. But the idea in the definition is that the parameter r is a "placeholder".

---

### Post by schauerlich on 2010-05-05
> **makuab said:**
> ```

def multiply(n):
       if n > 10
       return 4 * n
       elif n <= 10
       return n + 3

```

You've definitely got the right idea, which is good. There are just a few little things that python will complain about, which is that how much you indent code DOES matter. Also, after if statements, you need a colon.

```

def multiply(n):
       if n > 10:
           return 4 * n
       elif n <= 10:
           return n + 3

```

But you've got the idea of a function down, which is very good. Keep going! Try slightly more complicated things until you're comfortable with what functions are good at doing.

---

### Post by makuab on 2010-05-05
> **schauerlich said:**
> You've definitely got the right idea, which is good. There are just a few little things that python will complain about, which is that how much you indent code DOES matter. Also, after if statements, you need a colon.

```

def multiply(n):
       if n > 10:
           return 4 * n
       elif n <= 10:
           return n + 3

```But you've got the idea of a function down, which is very good. Keep going! Try slightly more complicated things until you're comfortable with what functions are good at doing.

can you give me another problem?

---

### Post by CptPicard on 2010-05-05
Let's try factorial... which is, for n, the number 1 * 2 * 3 * ... * n. It can be done with all the tools you've got right now, if you realise that the situation is as follows... if n = 1, the result is 1. For n > 1, it is... ?

---

### Post by makuab on 2010-05-05
> **CptPicard said:**
> Let's try factorial... which is, for n, the number 1 * 2 * 3 * ... * n. It can be done with all the tools you've got right now, if you realise that the situation is as follows... if n = 1, the result is 1. For n > 1, it is... ?
im a bit confused

---

### Post by schauerlich on 2010-05-05
CptPicard gave you a good one, but it might be a little hard for you right now. How about this one? write a function that will return 3 times a number plus 1 (3n + 1) if the number is odd, and half of the number (n / 2) if the number is even. Hint: if a number is even, n % 2 == 0

---

### Post by makuab on 2010-05-05
> **schauerlich said:**
> CptPicard gave you a good one, but it might be a little hard for you right now. How about this one? write a function that will return 3 times a number plus 1 (3n + 1) if the number is odd, and half of the number (n / 2) if the number is even. Hint: if a number is even, n % 2 == 0
```

def multipy(n):
    if n % 2 == 0:
        return n / 2
    else:
        return 3 * n + 1

```

---

### Post by schauerlich on 2010-05-05
> **makuab said:**
> ```

def multipy(n):
    if n % 2 == 0:
        return n / 2
    else:
        return 3 * n + 1

```

Good! you seem to have an idea of what functions can do now.

---

### Post by makuab on 2010-05-05
I have another question

```

def hello():
    print "Hello"
 
def area(width, height):
    return width * height
 
def print_welcome(name):
    print "Welcome", name
 
hello()
hello()
 
print_welcome("Fred")
w = 4
h = 5
print "width =", w, "height =", h, "area =", area(w, h)


```here it says

```

def print_welcome(name):
    print "Welcome", name
```where does it define (name)
here?
```

print_welcome("Fred")

```


taken from 
[http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python_2.6/Defining_Functions](http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python_2.6/Defining_Functions)

---

### Post by CptPicard on 2010-05-05
> **makuab said:**
> 
```

def print_welcome(name):
    print "Welcome", name
```where does it define (name)
here?
```

print_welcome("Fred")

```


When you call the print_welcome function with the "Fred", the function argument "name" gets assigned to it. That's the whole point of the function arguments :)

---

### Post by schauerlich on 2010-05-05
> **makuab said:**
> ```

def print_welcome(name):
    print "Welcome", name
```where does it define (name)
here?
```

print_welcome("Fred")

```

A variable is like a box that you can put a value in. In this case, the value is what's called a string, a bunch of letters between quotes. When you define the function [noparse](def print_welcome(name): )[/noparse] you're saying "this function has one variable, called name. I don't give it a value here, but when someone wants to use it, they will give me one." When you use the function [noparse](print_welcome("Fred") )[/noparse] you're saying "run the 'print_welcome' function, and when you do, put 'Fred' into the box called 'name'". Does that make sense?

---

### Post by makuab on 2010-05-05
> **CptPicard said:**
> When you call the print_welcome function with the "Fred", the function argument "name" gets assigned to it. That's the whole point of the function arguments :)
i see i see, thank you so much :)

anyone else got a problem for me :D?

---

### Post by CptPicard on 2010-05-05
Try the factorial function I suggested. ;) It's slightly challenging but eye-opening regarding recursion, probably the most important idea in programming. All you need to realize that the function's value is 1 for input 1, and... for the rest, n * factorial for the smaller values... :)

In case you didn't get what it actually is, examples...

```

fact(5) = 5 * 4 * 3 * 2 * 1
fact(3) = 3 * 2 * 1

```

---

### Post by schauerlich on 2010-05-05
> **makuab said:**
> i see i see, thank you so much :)

anyone else got a problem for me :D?

I suggest you keep following the tutorial you linked to previously, or use another one, like [this one](http://diveintopython.org/toc/index.html).

---

### Post by makuab on 2010-05-05
"So — I have outlined two ways of making functions: One type is more like  a procedure, and doesn’t return a result; the other is more like a  mathematical function and doesn’t do anything *but* returning a  result (almost)."

can someone give an example of each? 
taken from [http://hetland.org/writing/instant-hacking.html](http://hetland.org/writing/instant-hacking.html)

---

### Post by CptPicard on 2010-05-05
```

x = 5

def addToX(n):
  global x   # sorry, forgot this; it just says that the x is outside
  x = x + n


def add(x,n):
  return x + n

```

---

### Post by makuab on 2010-05-05
> **CptPicard said:**
> ```

x = 5

def addToX(n):
  x = x + n


def add(x,n):
  return x + n

```


and those both mean the same thing?

what is this 'add'? what does it do?

---

### Post by CptPicard on 2010-05-05
Those are both example functions that illustrate the point that you quoted in your post above. The first is a "procedure" that manipulates some state outside the function itself (the first "X") and does not return a result... latter is a function that does nothing but return a result. Outside program is unaffected.

---

