---
title: "python var  directly to evaluation"
date: 2009-10-07
forum: Programming Talk
---

### Post by flyingsliverfin on 2009-10-07
is it possible to have python just take a math symbol i entered into a variable and put it directly into the operation, for ex

x = input('enter a operator')
y = input('enter 1st #: ')
z = input('enter second #: ')

then i want it to print out the result. i can easily do
y ___ z

i can manually make a bunch of 'if' statements and from that fill in the appropriate operation in the underlined blank.. however, sometimes there lots of operations to check for. is there an equivalent to just doing

print y x z 

from there python just plugs it in and sees the expression, and evaluates it?

---

### Post by Can+~ on 2009-10-07
The easiest way, is with eval, in fact, you're already allowing to use expressions in the input because of the function "input"

Python 2.6
"raw_input" : Reads input as string
"input" : Reads input as python expression

(Will be deprecated in favor of)
Python 3.x
"input" : Reads input as string.

See for yourself:
[PHP]evalme = input("What you want to do?")

print evalme[/PHP]
```
What you want to do? 2+3 
5
```

This method is unsafe, because having directly interpreted input (either eval or 2.6 "input") may lead to a malicious input like "import os; <delete some file>"

> i can manually make a bunch of 'if' statements and from that fill in the appropriate operation in the underlined blank.. however, sometimes there lots of operations to check for. is there an equivalent to just doing

That's because you're thinking on procedural, switch gears to functional, and you can easily do:

Python 2.6
[PHP]#!/usr/bin/env python

# Dictionary of tasks
tasks = {
	"+" : lambda x, y: x + y,
	"-" : lambda x, y: x - y,
	"*" : lambda x, y: x * y,
	"/" : lambda x, y: x / y
}

operator = raw_input("Enter an operator >").strip()
leftmost = int(raw_input("Enter the left-most oparand >"))
rightmost = int(raw_input("Enter the right-most oparand >"))

# Call the function on the dictionary
# with both arguments
result = tasks[operator](leftmost, rightmost)

# Print result
print "%d %s %d = %d" % (leftmost, operator, rightmost, result)[/PHP]

The reason why this works, is because the dictionary, works by getting a key (the operator in this case) and returning it's value (a function in this case). Therefor, calling:

[PHP]f = tasks["+"][/PHP]

Will yield the function for addition, and then executing it just like in any other function:

[PHP]print f(2, 3) # prints 5[/PHP]

All this done in a single line, with anonymous functions.

---

