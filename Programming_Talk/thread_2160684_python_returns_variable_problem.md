---
title: "python returns variable problem"
date: 2013-07-07
forum: Programming Talk
---

### Post by wingnut2626 on 2013-07-07
ok so here is my code:

```
global a


def determineTypes(arg1, arg2):
    if type(arg1) is not type(arg2):
        print 'WARNING...OBJECTS NOT SIMILAR...ERROR MAY GENERATE...'
        print 'press enter to continue.'
        raw_input('>')
        adder(arg1,arg2)
    else:
        adder(arg1,arg2)


def adder(arg1, arg2):
    if type(arg1) is list:
        arg1.append(arg2)
	return arg1
    elif type(arg1) is str:
        a = arg1 + arg2
        return a
    elif type(arg1) is dict:
        for key in arg2:
            a = arg1
            a[key] = arg2[key]
            return a


    elif type(arg1) is int or float:
        a = arg1 + arg2
        return a


    else:
        #should not happen, just a placeholder
        pass
    


def begin():
    print 'what is item one?'
    item1 = raw_input('>')
    print 'what is item two?'
    item2 = raw_input('>')
    determineTypes(item1,item2)



```

How come none of the values for a get returned as 'a'.  After running the program, say:

```
adder.determineTypes(3,4)
print adder.a
```

I get an error, or if i switch the values of arg1 and arg2 i get 'None'.  Why is that?

---

### Post by Bachstelze on 2013-07-07
It looks like you expect your module to behave like a class. You can't access [font=monospace]a[/font] like that, you need something like

```
class Adder(object):

    def determineTypes(self, arg1, arg2):
        if type(arg1) is not type(arg2):
            print 'WARNING...OBJECTS NOT SIMILAR...ERROR MAY GENERATE...'
            print 'press enter to continue.'
            raw_input('>')
            self.adder(arg1,arg2)
        else:
            self.adder(arg1,arg2)

    def adder(self, arg1, arg2):
        if type(arg1) is list:
            arg1.append(arg2)
            self.a = arg1
        elif type(arg1) is str:
            self.a = arg1 + arg2
        elif type(arg1) is dict:
            for key in arg2:
                self.a = arg1
                self.a[key] = arg2[key]
        elif type(arg1) in [int, float]:
            self.a = arg1 + arg2
        else:
            #should not happen, just a placeholder
            pass
    
```

Then

```
>>> import adder
>>> add = adder.Adder()
>>> add.determineTypes(.5, .3)
>>> add.a
0.8
>>> add.determineTypes(1,2)
>>> add.a
3

```

P.S.: You should also consider switching to Python 3, there doesn't seem to be anything stopping you.

---

### Post by nvteighen on 2013-07-08
However, if you don't want to write a class, then just importing (**import adder**) will make your code work without any trouble.

---

### Post by Bachstelze on 2013-07-08
> **nvteighen said:**
> However, if you don't want to write a class, then just importing (**import adder**) will make your code work without any trouble.

I must be doing something wrong then...

```
>>> import adder
>>> adder.determineTypes(3,4)
>>> adder.a
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'module' object has no attribute 'a'

```

---

### Post by nvteighen on 2013-07-08
> **Bachstelze said:**
> I must be doing something wrong then...

```
>>> import adder
>>> adder.determineTypes(3,4)
>>> adder.a
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'module' object has no attribute 'a'

```

Just when I thought I knew Python really well, it hits me with this one... *facepalm*... globals are module-scoped.

---

### Post by wingnut2626 on 2013-07-08
Thanks guys lol.  Im just doing it class based  now.

---

### Post by wingnut2626 on 2013-07-08
how do I mark this thread as complete?

---

### Post by trent.josephsen on 2013-07-08
Edit the original post and add [Solved] to the title.

For posterity, and in case you see something like this again: An assignment within an inner scope masks or "shadows" variables in outer scopes. To prevent this, you need to put a "global" statement (or "nonlocal", in Python 3) in the **inner** scope, which tells Python "I want to use the `a' in the outer scope, even though I'm assigning to it." This is kind of a gotcha and easy to overlook.

```
a = "hello"
def greet(target):
    print a, target
greet("world")
```
will print "hello world", but
```
a = "hello"
def greet(target):
    print a, target
    a = "hi"
greet("world")
```
raises an error.

You can fix your original program (well, that particular bug) by moving the "global a" declaration inside the definition of adder().

---

### Post by alan9800 on 2013-07-08
according to the [programming recommendations]("http://www.python.org/dev/peps/pep-0008/#programming-recommendations") contained in the PEP8, you should use:
[LIST=1]
[*]```
if isinstance(obj, type)
```instead of```
if type(obj) is type(value of the type to be checked)
``` 
[*]```
''.join([string1, string2, ...])
```instead of```
string1 = string1 + string2 + ...
``` 
[/LIST]

---

