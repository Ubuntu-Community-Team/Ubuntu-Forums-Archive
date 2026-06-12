---
title: "Python, why use &lt;= instead of == ?"
date: 2009-07-23
forum: Programming Talk
---

### Post by l951b951 on 2009-07-23
This question is a very basic python question.  I'm trying to teach myself Python using the "Think Python" book and I've made it to conditional statements.  All the examples in the book use <= in places I wanted to use ==.  What is the reason for that?  Below is a copy/paste of one of the sample conditional statements.  I wanted to use if n == 0, and I don't quite understand the need to include the negative numbers below 0.

```
def print_n(s, n):
    if n <= 0:
        return
    print s
    print_n(s, n-1)

```

---

### Post by unutbu on 2009-07-23
If you use "n==0" and someone were to be so unwise as to run
```

print_n('Hi',-1)
```

then they fall into an infinite loop.

---

### Post by lisati on 2009-07-23
I'm not a Python guru, so I'll approach an answer more from a "general know-how" sense. 

In short, you need to make sure that your function will stop when it should. 

If you're throwing together code for a function for someone else to use, you can't guarantee that they'll provide valid input: if they give a function for, say, factorials a value where n<0, then not only will it not make sense, you could end up with a horibble mess. If you're lucky, it will result in an exception that your error handling code will catch.

---

### Post by Can+~ on 2009-07-24
> **unutbu said:**
> If you use "n==0" and someone were to be so unwise as to run
```

print_n('Hi',-1)
```

then they fall into an infinite loop.

And not only someone will consciously do that, it might happen at random, say:

[PHP]x = 10
y = 5

# ... code here ...

y += 6
print_n('Hello', x - y)[/PHP]

Thus, the problem becomes transparent to the person (including yourself) using the function. The thing is, functions are enclosed objects that should behave as expected, therefore, I don't expect that when calling a function made by other person (say you created a library and I'm using it) it will go on a infinite loop and crash my program.

The "pythonic" (well, object-oriented) way to handle it is by throwing the proper error:

[PHP]def recursion(s, n):
	
	if n == 0:
		return None
	elif n < 0:
		raise ValueError("Argument 'n' must be positive.")
	
	print s
	recursion(s, n-1)[/PHP]

But exception Handling is not something I would mess with at this point, so leave that for later.

---

### Post by days_of_ruin on 2009-07-24
> **Can+~ said:**
> 
The "pythonic" (well, object-oriented) way to handle it is by throwing the proper error:

[PHP]def recursion(s, n):
	
	if n == 0:
		return None
	elif n < 0:
		raise ValueError("Argument 'n' must be positive.")
	
	print s
	recursion(s, n-1)[/PHP]

But exception Handling is not something I would mess with at this point, so leave that for later.

EDIT: nvr mind. doh!

---

