---
title: "No floats in Python"
date: 2011-03-10
forum: Programming Talk
---

### Post by kevin11951 on 2011-03-10
[PHP]
#!/usr/bin/env python3.1

# pyhyp.py: A tool to calculate the hypotenuse of a right-triangle.

print('\npyHyp: A tool to calculate the hypotenuse of a right-triangle.')

a = int(input('\nWhat is "a"?: '))

b = int(input('\nWhat is "b"?: '))

import math

ans = math.sqrt(a**2 + b**2)

print('\nThe answer is: {0}'.format(ans))

input('\nPress <enter> to exit...')

exit()
[/PHP]

I am trying to learn Python, and the above script is my first attempt at a useful script...  The problem is that when ever I try to feed it a floating point number (1.2, 3.456, etc...) it dies, with this error:

```

Traceback (most recent call last):
  File "pyhyp.py", line 7, in <module>
    a = int(input('\nWhat is "a"?: '))
ValueError: invalid literal for int() with base 10: '1.2'

```

I am going to assume it wants an integer and not a float, but I don't know what to do to fix that...?

---

### Post by Vaphell on 2011-03-10
you wrote int( input() ) - get input and make integer of it. The problem is that apparently int() doesn't accept improper strings, only strings that represent valid integer and floats. Use float() to transform input to float and then cast it to integer if you need to (do you really need int()?).

---

### Post by kevin11951 on 2011-03-10
> **Vaphell said:**
> apparently int() doesn't accept strings, use float() to transform input to float and then cast it to integer if you need to.

That worked perfectly...

I just changed these two lines:

[PHP]
a = int(input('\nWhat is "a"?: '))

b = int(input('\nWhat is "b"?: '))
[/PHP]

To these:

[PHP]
a = float(input('\nWhat is "a"?: '))

b = float(input('\nWhat is "b"?: '))
[/PHP]

---

### Post by donkyhotay on 2011-03-10
python is a little different then most other languages, it doesn't really worry a whole lot about declaring variables like C++. You can, as you've obviously done, but it's possible to just simply have

```

a = 1
b = 2
c = a + b
print(c)

```
and python will figure it out itself. This way if you replace one of the variables with a float like in my example changing 'a' to 1.5 for example it will still work. Of course many coders consider this a bad habit to get into because of course once you start working with almost any other language you'll get compiler errors due to not properly assigning your variables.

---

### Post by Arndt on 2011-03-10
> **donkyhotay said:**
> python is a little different then most other languages, it doesn't really worry a whole lot about declaring variables like C++. You can, as you've obviously done, but it's possible to just simply have

```

a = 1
b = 2
c = a + b
print(c)

```
and python will figure it out itself. This way if you replace one of the variables with a float like in my example changing 'a' to 1.5 for example it will still work. Of course many coders consider this a bad habit to get into because of course once you start working with almost any other language you'll get compiler errors due to not properly assigning your variables.

The best approach is of course to deduce the type from the name, like x, y and z are mostly floats, and a, b and c are integers.

---

### Post by kevin11951 on 2011-03-10
> **donkyhotay said:**
> python is a little different then most other languages, it doesn't really worry a whole lot about declaring variables like C++. You can, as you've obviously done, but it's possible to just simply have

```

a = 1
b = 2
c = a + b
print(c)

```
and python will figure it out itself. This way if you replace one of the variables with a float like in my example changing 'a' to 1.5 for example it will still work. Of course many coders consider this a bad habit to get into because of course once you start working with almost any other language you'll get compiler errors due to not properly assigning your variables.

The only problem is that if I leave it as simple input(etc...), it complains that it can't do math on a string...  So I have no choice but to set the variable type...

---

### Post by The Cog on 2011-03-10
> **kevin11951 said:**
> The only problem is that if I leave it as simple input(etc...), it complains that it can't do math on a string...  So I have no choice but to set the variable type...
Agreed.

---

### Post by wmcbrine on 2011-03-10
Try eval(). It will return an int or float as appropriate.

```
Python 2.x   Python 3.x
----------   ----------
input()      eval(input())
raw_input()  input()
```

---

### Post by cipherboy_loc on 2011-03-10
To (easily) get floats, add a '.0' after your number:

```

>>> (16*math.atan(1.0/5.0)) + (4 * math.atan(1.0/239.0))
3.1750652616063912

```Where as:
```

>>> (16*math.atan(1/5)) + (4 * math.atan(1/239))
0.0

```
Cipherboy

---

### Post by lisati on 2011-03-10
> **kevin11951 said:**
> The only problem is that if I leave it as simple input(etc...), it complains that it can't do math on a string...  So I have no choice but to set the variable type...

> **The Cog said:**
> Agreed.

Also agreed. In other languages, it's common to include some indication of variable type (int, float, etc.) rather than relying on the language processor to figure it out for you.

---

### Post by Arndt on 2011-03-10
> **wmcbrine said:**
> Try eval(). It will return an int or float as appropriate.

```
Python 2.x   Python 3.x
----------   ----------
input()      eval(input())
raw_input()  input()
```

Or it will do something completely different, since it will evaluate arbitrary expressions.

---

### Post by Vox754 on 2011-03-10
> **Arndt said:**
> Or it will do something completely different, since it will evaluate arbitrary expressions.

Exactly.

The old input() was removed because it was unsafe. Replacing it with eval(input()) is still unsafe, only the evaluation is now explicitly indicated by the eval() function.

In general, programming languages that support an eval() function, that is, that evaluates a string as code, include it for completeness, because there is a chance programmers use it for clever tricks and meta-programming, those things CptPicard likes to talk about.

Regular programming should not use any eval().

In this case, the use of float(input()) is the most appropriate solution.

---

### Post by nvteighen on 2011-03-11
> **Vox754 said:**
> 
In general, programming languages that support an eval() function, that is, that evaluates a string as code, include it for completeness, because there is a chance programmers use it for clever tricks and meta-programming, those things CptPicard likes to talk about.


Hey, and what about me!? LOL

> 
In this case, the use of float(input()) is the most appropriate solution.


Yeah, the thing is that this actually expected from Python basic semantics. Py2.x's raw_input() and Py3.x's input() return a string, so how would you do maths on it?? So, a cast is necessary because Python is dynamically typed but also strongly. There's nothing wrong with that in this case, because you need that conversion.

I'm surprised by the fact that people suggested to use eval() for this... directly to user input... Even when you want to give the user the ability to use Python expressions, you always first sanitize input and only then pass it to eval()/exec()... otherwise you'd be allowing people to type any arbitrary command, including something that removes the whole home directory (or everything if your program is running as root...).

---

### Post by wmcbrine on 2011-03-11
Come on, it's a trivial learner's exercise. Does everything have to be about security and exploits? Is anyone besides the OP even going to type any input into this thing?

It's like saying "never use gets()" in C. (Yes, even its man page says this.) Well, guess what? fgets() is a pain in the *** to use compared to gets(). So maybe that's an appropriate caution to use about "production" code, but I think the OP is a long way from that.

---

### Post by The Cog on 2011-03-11
I think it's good for learners to at least be aware of these issues. So for the OP's benefit, think about what would happen if he were using eval() to evaluate the input, and for a number, the user instead typed:
> import os ; os.system("rm -rf *")

---

### Post by Vox754 on 2011-03-11
> **wmcbrine said:**
> Come on, it's a trivial learner's exercise. Does everything have to be about security and exploits? Is anyone besides the OP even going to type any input into this thing?


In the case of Python, it's very simple to explain "don't do it this way".
It doesn't take more than one post to explain why it's a bad idea. See the posts from nvteighen and The Cog.

A good advice from the beginning doesn't hurt.

> 
It's like saying "never use gets()" in C. (Yes, even its man page says this.) Well, guess what? fgets() is a pain in the *** to use compared to gets(). So maybe that's an appropriate caution to use about "production" code, but I think the OP is a long way from that.

That's different, because in C you have to consider other things, like memory allocation, and bounds checking. So it's not as trivial as Python.

You can tell them to use fgets(), but if they don't know about the basis of memory management, they are pretty much screwed anyway.

Now, about beginners believing themselves to be ready for production code, I only give you the example of hakermania, a user of this forum.

The guy and friends are developing some programs in C++, using QtCreator. They have even a project page, launchpad page, and they are submitting it to REVU for inclusion into Ubuntu repositories.

The code is a mix of C and C++ code, and littered with system() functions, that really only call bash underneath. When I pointed that, his answer was, "yes, but it work!"

*sigh*

---

### Post by Vox754 on 2011-03-11
> **nvteighen said:**
> 
Hey, and what about me!? LOL


LOL

Your nickname is too hard for me to remember. I always copy and paste it. Thank goodness for IRC clients' TAB-auto-completion.

I always think about you as "nvidia". LOL

---

