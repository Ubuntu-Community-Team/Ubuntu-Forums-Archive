---
title: "[SOLVED] Python Import"
date: 2008-11-12
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-11-12
in python, if you have these two files

test1
[PHP]def p():
     print 1[/PHP]

test2
[PHP]def p():
     print 2[/PHP]

you could now do this
[PHP]>>> from test1 import *
>>> p()
1
>>> from test2 import *
>>> p()
2
[/PHP]

Is this looked down upon (not this simple, but for more complex things)

---

### Post by jimi_hendrix on 2008-11-12
if you mean purposely naming two functions the same when there is a possibility you might need both in the same program than yes

---

### Post by Mr.Macdonald on 2008-11-12
> if you mean purposely naming two functions the same when there is a possibility you might need both in the same program than yes 

no naming them the same so they overwrite each other when you import either file, so if you need to run a different function based upon input. you can parse the input and import different files so that later when you run that function, it is specialized for the input

---

### Post by snova on 2008-11-12
It is looked down upon to use 'from XXXXX import *'. Heed this advice, and the problem will never arise.

But I have no qualms about naming two functions the same way, and I cannot think of a reason not to if the name is adequate.

---

### Post by unutbu on 2008-11-12
Using imports to overwrite function definitions makes your program harder to maintain and debug. When you read your code a year from now, and see a call to p(), how will you know in which file p() is defined? You'll have to hunt for the import statement. Not only is it bad because you'll have to trace through your program's logic to find out which file it came from, but also -- if you are not intimately familiar with your code -- you'll have to puzzle over the lack of explicitness caused by using the * form of the import statement. The statement
```

from test1 import *
```

does not make it explicit that p came from test1. This makes it extra burdensome to track down where functions are defined.

This might serve you better:
```

import test1
import test2

if ...:
    p=test1.p
else:
    p=test2.p

```
Then you can call p simply with

```
p()
```

---

### Post by Mr.Macdonald on 2008-11-12
look at this example

test1
[PHP]def F(num1, numarray):
	for i in range(len(numarray)):
		numarray[i] = numarray[i] + num1
	return numarray[/PHP]

test2
[PHP]def F(char, chararray):
	for i in chararray:
		print i+char
	return char[/PHP]

execute this
[PHP]def func(array, type):
	if type=="char":
		from test2 import F
	else:
		from test1 import F
	while True:
		print F(input("Value"), array)[/PHP]

This works, but will I run into problems later, with more complex thing. Or is this new to you, as it is to me

---

### Post by Greyed on 2008-11-13
> **Mr.Macdonald said:**
> Is this looked down upon (not this simple, but for more complex things)

No.  What you're doing is an extremely crude and basic form of OOP.  That's the entire notion behind OOP and classes.

EG:

[php]
>>> class _BaseClass():
...     def __init__(self):
...         pass
...     def p(self):
...         print("Placeholder")
...
>>> class SubClassA(_BaseClass):
...     def p(self):
...         print("A")
...
>>> class SubClassB(_BaseClass):
...     def p(self):
...         print("B")
...
>>> spam = SubClassA()
>>> spam.p()
A
>>> spam = SubClassB()
>>> spam.p()
B
[/php]Notice that p() depends on which class you assign to spam.  This would much the same effect as importing a similarly named function from one library as opposed to the other.

As was pointed out, avoid "from spam import *".  If you simply must use that form (which I do, often) remember one of the core Python principles.  **Be Explicit!**.

[php]
from spam import eggs
eggs.benedict(over_easy)
[/php]There is no mistaking where eggs came from.  If the import line used * instead of eggs later maintainers would wonder where it came from and would have to dig through the imported libraries to find it.  If you really mean to import the whole library then just import it normally, not with the from form.

[php]
import spam
spam.eggs.benedict(over_easy)
[/php]Again, no question on where it came from.

---

### Post by Greyed on 2008-11-13
> **Mr.Macdonald said:**
> This works, but will I run into problems later, with more complex thing. Or is this new to you, as it is to me

You will run into problems.  Avoid multiple imports of the same library over and over.  As it is imported only once (subsequent imports do not actually run) you will run into serious problems later on based on false presumptions.

For what you're doing, import both once and assign them to variables then swap another between those two.

[php]
import test1
import test2

def func(array, type): 
    if type=="char": 
        F = test2.F
    else: 
        F = test1.F
    while True: 
        print F(input("Value"), array)  
[/php]

But, now that I am looking at the code, what are you trying to do?

---

### Post by Mr.Macdonald on 2008-11-13
My reasoning for doing that, although it seems strange, was that F would be a large and complex function. F would be defined for many different problems.

If I were to import all of them, as different classes, then the system would slow because python would be importing many different page to two page long methods.

I was designing it like the kernel and how you load modules for different hardware, but if you load all the modules then your system goes slower

Should I not use it for that? Would overwriting just write the function to more memory or does it actually overwrite.

---

### Post by Greyed on 2008-11-13
You're preoptimizing.  Write the code, then identify the bottlenecks, then address the slow portions.  Other than wanting to keep the different portions separate for ease-of-maintenance for you, as the programmer, don't worry about import tricks like this unless you really, absolutely know you need them.

---

### Post by Mr.Macdonald on 2008-11-13
I guess I will just write good code so that it works and then optimize it. To many times I have started projects trying to get the speed up, and then dumped it because the code was too abstract

---

