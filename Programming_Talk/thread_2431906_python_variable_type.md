---
title: "python variable type"
date: 2019-11-23
forum: Programming Talk
---

### Post by marchello_lippi2 on 2019-11-23
Hi all, 
I just started to learn python programming and have a question. 
It does not require to set variable data type, hmm. 
So I can just declare 
```
my_variable = 5
```
and it will be integer. 
What if I need to assign something like 4.3 (not integer) to that variable later?
I believe I should instead declare it from the beginning as
```
my_variable = 5.0
```
so that it will accept my 4.3 value later and store it properly (not as 4 integer).
But... how do I declare variable with datatype (definitely)?

I believe I will find out this a bit later, but typing my question here helps me to understand what I am looking for.
So... thank you for your attention.

---

### Post by gnusci on 2019-11-23
There are three distinct numeric types: integers, floating point numbers, and complex numbers.

[https://docs.python.org/3/library/stdtypes.html](https://docs.python.org/3/library/stdtypes.html)

---

### Post by The Cog on 2019-11-24
> But... how do I declare variable with datatype (definitely)?
You did, in our first post. Twice. You knew what type you were assigning.
You cannot have a variable that only stores one datatype - variables will store whatever is assigned to them. Come to think if it, I don't think you can "declare" variables. They are created when you assign a value to them.
Also look at this:
```
a=5
a *= 1.0
```
This stores an integer in a, and then replaces it with a float, something that's not immediately obvious.

P.S.
All variables in python are just references to objects. It's the objects that have types. Even integers are objects in python. Try:
```
help(3)
dir(3)
```

---

### Post by marchello_lippi2 on 2019-11-25
> **gnusci said:**
> There are three distinct numeric types: integers, floating point numbers, and complex numbers.

[https://docs.python.org/3/library/stdtypes.html](https://docs.python.org/3/library/stdtypes.html)
So it's only for Python 3, right? 
I started from Python 2 as it's still in use as well and can't see anything like this. Did I miss anything?

---

### Post by marchello_lippi2 on 2019-11-25
> **The Cog said:**
> 
You cannot have a variable that only stores one datatype - variables will store whatever is assigned to them. [/code]
Hm... so one variable can store integer first, then same variable can store string? Is it correct or am I missing something?

---

### Post by The Cog on 2019-11-25
> I started from Python 2 as it's still in use as well and can't see anything like this. Did I miss anything?
Python3 added a new type for byte arrays that is distinct from strings which are now always unicode. Apart from that, nothing big. [https://docs.python.org/2/library/datatypes.html](https://docs.python.org/2/library/datatypes.html)
> Hm... so one variable can store integer first, then same variable can store string? Is it correct or am I missing something?
I would prefer to say that a variable can **refer** to an int object first, then refer to a float object or any other type of object later. It refers to whatever is assigned to it. The only thing you can do to a variable is to assign to it (or delete it). If you try to use it you just end up using whatever it refers to.

---

### Post by spjackson on 2019-11-25
> **marchello_lippi2 said:**
> Hm... so one variable can store integer first, then same variable can store string? Is it correct or am I missing something?
Yes. This is an aspect of dynamic typing. If you want to declare a variable of a particular type and to ensure that only values of that type can be assigned to it, then you need a statically typed language.

---

### Post by marchello_lippi2 on 2019-11-26
Well, I believe I sorted this out a bit with your help, thanks.

Now wanted to use same thread to speak regarding Python 2. Honestly, I started learning exactly this version because codecademy has its online interactive course for free. Python 3 is PRO plan and it's paid. Not that I'm short of funds right now, but wanted to try it for free because I don't know how it will go.
Done 10% and then found information that Python 2 is used in legacy projects while Python 3 is more for new and future usage. I believe I would need both because I'm lucky to work on legacy projects recently, though I should be ready to create something from scratch as well.
Now my question is, how different those two versions are? Like, how a newcomer can understand the logic, why both versions co-exist? Can you imagine that one is able to work on Python 3 project with some googling if he/she learned only Python 2 before?
Thanks!

---

### Post by The Cog on 2019-11-28
They really are not that different. You can find lots of info on the difference by web searches. 
The two biggest differences are:
1: 
print is not a function, not a language built-in. So instead of "print a, b, c", you say "print(a, b, c)". Not so hard, really.
2: 
Strings are all unicode and there is a new **bytes** type for a sequence of bytes. I think this is the big difference, that will catch people out when reading/writing files/sockets.
```
>>> a="hi there"
>>> type(a)
<class 'str'>
>>> b = a.encode("utf8")
>>> type(b)
<class 'bytes'>
```

---

### Post by marchello_lippi2 on 2019-11-28
> **The Cog said:**
> They really are not that different. You can find lots of info on the difference by web searches. 
The two biggest differences are:
[...]
Good news, so I believe it's good that I started from Python 2.

Another question comes to my mind... If it's not so big difference, then why they even splitted?
I mean, I would just introduce print2 stuff and so on. 
Is there any real serious reason to have different versions?...

---

### Post by The Cog on 2019-11-28
[https://snarky.ca/why-python-3-exists/](https://snarky.ca/why-python-3-exists/)
[https://whypy3.com/](https://whypy3.com/) - interesting collection of differences

---

### Post by marchello_lippi2 on 2019-11-28
> **The Cog said:**
> [https://snarky.ca/why-python-3-exists/](https://snarky.ca/why-python-3-exists/)
[https://whypy3.com/](https://whypy3.com/) - interesting collection of differences
Thanks!

---

