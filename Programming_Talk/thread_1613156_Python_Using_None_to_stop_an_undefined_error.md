---
title: "Python: Using None to stop an undefined error?"
date: 2010-11-04
forum: Programming Talk
---

### Post by BlackRat90 on 2010-11-04
Hi there! 
So im looking for a way to stop an undifined error when using input. 

example of sort of what I want being:
```
pie = 'yes!'
search = input() #user inputs what they are searching for
if search != None:
    print "Happy!"
else :
    print "sad...."
    search = 0

```
So basically if the user tries to search for anything that is undefined it will become 0 instead of erroring?

I feel like Im close to the answer I need, but it im just not getting it....Could anyone give me advice?

---

### Post by Cheesehead on 2010-11-04
if search !="":     instead of if search !=None

During the user prompt, simply hitting return without other text will result in an empty string, not a None or False.

---

### Post by nvteighen on 2010-11-04
> **BlackRat90 said:**
> 
```
pie = 'yes!'
search = input() #user inputs what they are searching for
if search != None:
    print "Happy!"
else :
    print "sad...."
    search = 0

```


Just a question: what version of Python are you using? (check typing python --version in a terminal). If it's Python 2.x, replace input() by raw_input().

In Python 2.x, input() doesn't just get user input, but it actually works like a Python prompt. If you pass a string containing Python code to input(), that string will be evaluated. raw_input() instead will grab a string but won't do any further action.

Look at this:
```

ugi@UGI:~$ python
Python 2.6.6 (r266:84292, Oct  9 2010, 11:40:09) 
[GCC 4.4.5] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> a = input()
4 + 7
>>> a
11
>>> b = raw_input()
4 + 7
>>> b
'4 + 7'
>>> 

```

In Python 3.x, instead, input() is the old raw_input() and the old input() is deprecated (the same effect of the old input() can be created by using exec() or eval() on any string).

So, if you're using Python 2.x, you better use yourself to raw_input() instead. In your code snippet, it isn't quite relevant but I hope you understand the security risk it is to have any possible string being evaluated without any sanity check.

---

### Post by BlackRat90 on 2010-11-04
raw_input does not work. I noticed I had made a small mistake in the example i made...

```
pie = 'Yes!'
eating = "Nothing..."
search = input()
if search != "":
    print "Happy!"
    search = eating
else :
    print "sad...."
    search = 0
```

So at the end, if the user inputs pie, then eating will be equal to "Yes!"
Ive gotten this to work before, its not working here though.

---

### Post by BlackRat90 on 2010-11-04
I dont think this was clear enough

I want the code to ask a user what string they want to reference.
If the string exists then I want it to be assigned (or copied) to eating so that eating is equal to the string pie (or any string that exists).
If the string asked for does not exist then I want it to reject it, and not give me an error, or at least not make my program end...

I am using version 2.6 I think...

---

