---
title: "[python] Rerun function"
date: 2009-07-27
forum: Programming Talk
---

### Post by Bohemenian on 2009-07-27
```
def function():
    output = raw_input("Enter 5: ")
    if output != "5":
        function()
    else:
        return output
toprint = function()
print toprint

>>> Enter 5: 2
>>> Enter 5: 5
>>> None
```
How do I get around this? Is there any way of running the function again on the same line, like rerun() or something?

---

### Post by Can+~ on 2009-07-27
> **Bohemenian said:**
> ```
def function():
    output = raw_input("Enter 5: ")
    if output != "5":
        function()
    else:
        return output
toprint = function()
print toprint

>>> Enter 5: 2
>>> Enter 5: 5
>>> None
```
How do I get around this? Is there any way of running the function again on the same line, like rerun() or something?

This does not "rerun" the function, it's causing what's called a recursion, that means that you're getting the following:

```
def function():
    output = raw_input("Enter 5: ")
    if output != "5":
[COLOR="Red"]        def function():
            output = raw_input("Enter 5: ")
            ...[/COLOR]
    else:
        return output
```

And also, when you call the recursion, do it, and go back, you're not returning anything, therefore, to fix it, you should do:

```
def function():
    output = raw_input("Enter 5: ")
    if output != "5":
        return function()
    else:
        return output
toprint = function()
print toprint
```

Although, recursion makes no sense in this scenario (asking user input), that's why you should probably use a loop.

[PHP]def function():
	output = ""
	
	while output != "5":
		output = raw_input("Enter 5: ")
	
	return output

toprint = function()
print toprint
[/PHP]

---

### Post by Bohemenian on 2009-07-30
Thanks, i solved it with a while loop. 
But I'll probably come back to the return function() soon. Anyways, I'm still wrapping my head around Python and programming in general, I just have to get my programming-thinking on, I guess.

---

### Post by lisati on 2009-07-30
> **Bohemenian said:**
> Thanks, i solved it with a while loop. 
But I'll probably come back to the return function() soon. Anyways, I'm still wrapping my head around Python and programming in general, I just have to get my programming-thinking on, I guess.

The "return function()" approach is an example of [recursion]("http://en.wikipedia.org/wiki/Recursion"). It's a neat trick that can make programming solutions to some problems easier but there are traps for the unwary - for example, you need to make sure that your function has a way of knowing when to stop calling itself (before it goes wild and uses up all your system's RAM or stack space).

---

