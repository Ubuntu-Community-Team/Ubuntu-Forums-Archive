---
title: "[SOLVED] [python] Help with global variable"
date: 2008-08-06
forum: Programming Talk
---

### Post by Titan8990 on 2008-08-06
I realized as I started this weeks programming challenge that I am lost when it comes to manipulating global variables. I have book but it is not in front of me to reference as I am at work. What I am trying to do in the programming challenge is alter a global variable inside of a function and return it back to the global variable.

I did some testing with the python IDLE but this confused me even more:

[php]>>> x = 10
>>> print x
10
>>> def test():
...     print x
... 
>>> test()
10
>>> def test2():
...     print x
...     x = x + 1
...     print x
... 
>>> test2()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 2, in test2
UnboundLocalError: local variable 'x' referenced before assignment[/php]

Why did x remain a global variable in the function test but not in test2?

For now, that is all I would like to know. I think that it beneficial to my learning experience that I figure out as much as I can for myself but I am getting a bit frustrated (should have brought my book to work knowing I would have nothing to do other than this programming challenge). 

Also, would it have been more appropriate for me to have made this post in the programming challenge thread?

---

### Post by days_of_ruin on 2008-08-06
Because you assigned x after you printed it.If python doesn't find
a variable with a name in a function it looks in the global scope.
But if you assign it inside the function it will mess it up.

If you want to use the global x use ```
global x
``` before you print it or do anything else with it.If you want it to be local, assign it before
doing anything with it.

---

### Post by y-lee on 2008-08-06
> Why did x remain a global variable in the function test but not in test2?

Because test2 tries to change the value of x. Use something like the below if you wish to alter global variables.

And btw the use of global variables is generally discouraged in programming these days. It can lead to alot of problems, some hard to debug.

```
def test3():
...     global x
...     print x
...     x = x + 1
...     print x
```

> Also, would it have been more appropriate for me to have made this post in the programming challenge thread?

Probably better to ask here instead of clutter the prog challenge post with off topic questions.

---

### Post by Titan8990 on 2008-08-06
Thank you for the replies guys, I understand that now.

> And btw the use of global variables is generally discouraged in programming these days. It can lead to alot of problems, some hard to debug.

What is the alternative to get one variable to pass from one function to another? Or is there a way of avoiding passing variables around functions altogether?

---

### Post by Bachstelze on 2008-08-06
> **Titan8990 said:**
> Or is there a way of avoiding passing variables around functions altogether?

Yes, OOP ;)

```
>>> class Main :
...     def __init__(self) :
...         self.x = 0      
...     def inc(self) :     
...         self.x += 1
...         print self.x
...     def dec(self) : 
...         self.x -= 1
...         print self.x
...                     
>>> foo = Main()
>>> print foo.x
0
>>> foo.inc()
1
>>> foo.inc()
2
>>> foo.inc()
3
>>> foo.dec()
2
>>> foo.dec()
1
>>> foo.dec()
0
>>> foo.dec()
-1
>>> foo.dec()
-2
>>> foo.dec()
-3
>>> foo.inc()
-2
>>> foo.inc()
-1
>>> foo.inc()
0

```

---

### Post by Titan8990 on 2008-08-06
Well, OOP is the chapter of my book that I am on. I am still going to do this challenge using global variable for the learning experience. Hopefully by the next challenge I will be ready to implement objects in my code.


Thanks again for the help guys.

---

