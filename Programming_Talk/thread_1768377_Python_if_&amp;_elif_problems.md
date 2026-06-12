---
title: "Python if &amp; elif problems"
date: 2011-05-26
forum: Programming Talk
---

### Post by DarkSnake-Kobra on 2011-05-26
Hi everyone. :) I'm a beginner to Python and having some problems with the if and elif statements. I did some research and looks like I'm not alone when it comes to getting an invalid syntax error. I need some help getting it in the right format. Thanks! :)

```
>>> OJ_price = 2.50
>>> if OJ_price < 1.25:
	print("Get one, I'm thirsty.")

	
>>> elif OJ_price <= 2.00:
	
SyntaxError: invalid syntax
>>> 
```

---

### Post by TwoEars on 2011-05-26
> **DarkSnake-Kobra said:**
> Hi everyone. :) I'm a beginner to Python and having some problems with the if and elif statements. I did some research and looks like I'm not alone when it comes to getting an invalid syntax error. I need some help getting it in the right format. Thanks! :)

```
>>> OJ_price = 2.50
>>> if OJ_price < 1.25:
	print("Get one, I'm thirsty.")

	
>>> elif OJ_price <= 2.00:
	
SyntaxError: invalid syntax
>>> 
```

```

>>> if 2<1:
...     print "2 is less than 1. Wow."
... elif 3<2:
...     print "3 is less than 2. Woooow."
... else:
...     print "2 is not less than 1, 3 is not less than 2. Phew."
...
2 is not less than 1, 3 is not less than 2. Phew.

```
See the difference? ;) In the interpretor, you need to include it as part of the '...' lines, because it's all part of the same statement.

---

### Post by DarkSnake-Kobra on 2011-05-26
Still very confused. This is what I got when trying your example.

```
>>> if 2<1:
...     print "2 is less then 1. Wow."
  File "<pyshell#9>", line 2
    ...     print "2 is less then 1. Wow."
    ^
IndentationError: expected an indented block
>>> 
```

---

### Post by TwoEars on 2011-05-26
> **DarkSnake-Kobra said:**
> Still very confused. This is what I got when trying your example.

```
>>> if 2<1:
...     print "2 is less then 1. Wow."
  File "<pyshell#9>", line 2
    ...     print "2 is less then 1. Wow."
    ^
IndentationError: expected an indented block
>>> 
```

Urm, the "..." are put there by default on CPython. You don't need to type them, just do the indent in the right places :)

---

### Post by DarkSnake-Kobra on 2011-05-26
Gotcha. I tried without them, but still got an error

```

>>> if 2<1:
	print "2 is less then 1. Wow."
    elif 3<2:
	    
  File "<pyshell#2>", line 3
    elif 3<2:
            ^
IndentationError: unindent does not match any outer indentation level
>>> 
```

---

### Post by DarkSnake-Kobra on 2011-05-26
Never mind I got it. :) Had to backspace and put it directly under the >>> Thanks! :D

```
>>> if 2<1:
	print "2 is less then 1. Wow."
elif 3<2:
	print "3 is less then 2. Wooow."
else:
	print" 2 is not less then 1, 3 is not less then 2. Phew"

	
 2 is not less then 1, 3 is not less then 2. Phew
>>> 
```

---

