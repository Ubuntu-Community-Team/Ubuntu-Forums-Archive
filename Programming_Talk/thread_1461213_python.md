---
title: "python"
date: 2010-04-23
forum: Programming Talk
---

### Post by flyingsliverfin on 2010-04-23
my brother just told me that if statements are really inefficient, so i was just wondering if it would be better to have a dictionary with a bunch of different commands and directly execute those?

for example:
x = {'what' : "print('thats a phone')" ,
  'whatfor': "print('for calling people')" }

then somehow executing the commands directly

instead of:
if x == 'what':
 --  then print('thats a phone')
if x == 'whatfor':
 -- then print('for caling people')

is that a good idea? is it even possible?

---

### Post by soltanis on 2010-04-23
There's nothing particularly inefficient about conditional branches. Don't prematurely optimize your code; use what is best.

Dictionaries are probably slower anyways.

---

### Post by casevh on 2010-04-24
Using a dictionary to store function definitions and accessing them by name is a common practice in Python. It is the recommended alternative to the case..select construct provided in other languages.

I ran some tests using the code below. You should experiment on your computer.

If you can assume that one of the if statements will match, you can use functions[which]() to call the function identified by which.

If you are using if/elif/else so there is a final function call that's done if none of the earlier tests match, then you should use functions.get(which,default_function)().

On my system, if I use functions[which](), it was about as fast as one if statement. If I use functions.get(which, default_function)(), the breakeven point is around 3 or 4 if statements. 

I probably wouldn't be too concerned about the performance differences unless you are trying to choose between a large (5+) number of functions. I think it is a little harder to understand at first. 

```

import time

def f1(): pass
def f2(): pass
def f3(): pass
def f4(): pass
def f5(): pass
def f6(): pass
def f7(): pass

functions = { 'f1' : f1,
              'f2' : f2,
              'f3' : f3,
              'f4' : f4,
              'f5' : f5,
              'f6' : f6
              }

def test_if(which, count):
    start = time.time()
    for i in range(count):
        if which == 'f1':
            f1()
        elif which == 'f2':
            f2()
        elif which == 'f3':
            f3()
        elif which == 'f4':
            f4()
        elif which == 'f5':
            f5()
        elif which == 'f6':
            f6()
        else:
            f7()
    return time.time() - start

def test_dict(which, count):
    start = time.time()
    for i in range(count):
        #Use "functions[which]()" if which is guaranteed to exist.
        #functions[which]()
        #Use "functions.get() to mimic a final else function.
        functions.get(which, f7)()
    return time.time() - start

if __name__ == '__main__':
    print('Function by if:   ' + str(test_if('f4', 10000)))
    print('Function by dict: ' + str(test_dict('f4', 10000)))


```

Python uses dictionaries behind the scenes for almost all name or object lookups. Dictionary lookups are very fast in Python.

casevh

---

### Post by nvteighen on 2010-04-24
Ok, maybe there is a performance boost but conditionals are such a basic logical (and programming) structure that I don't think it's wise to try to replace it at the code's "surface structure". What I mean is, well, maybe you can use some dictionary trick or even the "x and y or z" one, but I'd always try to hide that using some kind of macro or grammar/syntax transformation device such that my code actually reads "if ..." or something similar.

---

### Post by simeon87 on 2010-04-24
Only optimize if it's needed. If you're just doing some if-statements, there's no need to modify it but if the code runs frequently, then yes, you should experiment with a dictionary to make it faster. But it's not recommended to change the code to remove all if-statements.

---

### Post by flyingsliverfin on 2010-04-24
thanks everyone
i also have another question(unrelated to the first one):

if i have something like this

```
grid = [
[0,0,0,0,0],
[0,0,0,0,0],
[0,0,0,0,0],
[0,0,0,0,0],
[0,0,0,0,0]
]
```

and want to transfer that to 

```
print("				
  A B C D E 
1|0|0|0|0|0|
2|0|0|0|0|0|
3|0|0|0|0|0|
4|0|0|0|0|0|
5|0|0|0|0|0|
")
```

i will be making changes to the nested lists, but want to print out the 0's as 0's and 1's as x's in the nice format i have made.

---

### Post by nvteighen on 2010-04-25
> **flyingsliverfin said:**
> thanks everyone
i also have another question(unrelated to the first one):

if i have something like this

```
grid = [
[0,0,0,0,0],
[0,0,0,0,0],
[0,0,0,0,0],
[0,0,0,0,0],
[0,0,0,0,0]
]
```

and want to transfer that to 

```
print("				
  A B C D E 
1|0|0|0|0|0|
2|0|0|0|0|0|
3|0|0|0|0|0|
4|0|0|0|0|0|
5|0|0|0|0|0|
")
```

i will be making changes to the nested lists, but want to print out the 0's as 0's and 1's as x's in the nice format i have made.

Well, there's no trivial way to do that. You better keep your grid untouched and create a procedure that returns the grid-string from the matrix; then pass the returned string to print.

That way, you'll separate implementation from user interface, an habit that will help you a lot in the future if you happen to do... almost everything involving a user :p

---

### Post by StephenF on 2010-04-25
> **flyingsliverfin said:**
> thanks everyone
i also have another question(unrelated to the first one):

if i have something like this

```
grid = [
[0,0,0,0,0],
[0,0,0,0,0],
[0,0,0,0,0],
[0,0,0,0,0],
[0,0,0,0,0]
]
```

and want to transfer that to 

```
print("				
  A B C D E 
1|0|0|0|0|0|
2|0|0|0|0|0|
3|0|0|0|0|0|
4|0|0|0|0|0|
5|0|0|0|0|0|
")
```

i will be making changes to the nested lists, but want to print out the 0's as 0's and 1's as x's in the nice format i have made.
Major spoilers. =;
[http://pastebin.com/Zxu0xjYi](http://pastebin.com/Zxu0xjYi)

---

### Post by flyingsliverfin on 2010-04-25
wow complicated

---

