---
title: "Beginner: Python Syntax"
date: 2011-07-23
forum: Programming Talk
---

### Post by infectedorganism on 2011-07-23
I have taken a semester in Java, but the second half isn't offered until the Spring. I will dabble in it over the next few months, but for now I want to focus on Python.

Here are my questions regarding syntax: 

Can I use a semicolon (;) to end a line (what I prefer to do)? Could that get me into trouble down the line (once I learn more syntax)? Would using it make my code "harder" to read for those familiar with Python?

Can I enclose most statements in parenthesis (print statements, etc.)?

Can I use + to concatenate strings with variables?

Hmm, I think that is all for now.

Thanks in advance.

---

### Post by Vaphell on 2011-07-23
fire up python environment and play with it to see what works and what not

```
>>> a=3*2; b='wtf';
>>> print 'abc'+b+`a`
abcwtf6
>>> print ( 'abc'+b+`a` )
abcwtf6
>>> print '%s %s %s' % ( 'abc', a, b )
abc 6 wtf
>>> print ( '%s %s %s' % ( 'abc', a, b ) )
abc 6 wtf
>>> print a, b
6 wtf
>>> print ( a, b )
(6, 'wtf')

```

last one doesn't work, it creates a tuple and prints it

---

### Post by cgroza on 2011-07-23
> **infectedorganism said:**
> I have taken a semester in Java, but the second half isn't offered until the Spring. I will dabble in it over the next few months, but for now I want to focus on Python.

Here are my questions regarding syntax: 

Can I use a semicolon (;) to end a line (what I prefer to do)? Could that get me into trouble down the line (once I learn more syntax)? Would using it make my code "harder" to read for those familiar with Python?

Can I enclose most statements in parenthesis (print statements, etc.)?

Can I use + to concatenate strings with variables?

Hmm, I think that is all for now.

Thanks in advance.
You can use a semicolon, but that will look weird and clutter the code for other python users.
Statements like if, while, for ... do not accept parenthesis. Print is an exception, but in python3000 it becomes a function. 

That depends, if the variable is a string too, no problem. If not, you may need to get a string from that variable using str().

---

### Post by TwoEars on 2011-07-23
> **infectedorganism said:**
> I have taken a semester in Java, but the second half isn't offered until the Spring. I will dabble in it over the next few months, but for now I want to focus on Python.

Here are my questions regarding syntax: 

Can I use a semicolon (;) to end a line (what I prefer to do)? Could that get me into trouble down the line (once I learn more syntax)? Would using it make my code "harder" to read for those familiar with Python?

 
Yes, you can do it, but don't.  Hardly anybody in the Python world uses them, and those who do don't follow convention, and as a result should be shunned ;). Shun the non-believer, shun!

> 
Can I enclose most statements in parenthesis (print statements, etc.)?

As in ```
(print) 'something'
(print 'something')
print ('something')

```
? 
No.
You can do the last, but I don't suggest doing it that way, not at all (it evaluates 'something' as a tuple). Alternatively, you can look at 3.x, in which print is a function. If you're going to learn Python, please use the conventions - [http://www.python.org/dev/peps/pep-0008/](http://www.python.org/dev/peps/pep-0008/) or you might end up with nobody willing to read your code but you ;)

> 
Can I use + to concatenate strings with variables?

Yes, provided they are both strings. However, this it not recommended most of the time - what you'd want instead is string formatting.

---

### Post by infectedorganism on 2011-07-23
Thanks for the responses!

Last question: Should I move to Python 3.x or stick with 2.x?

---

### Post by Bachstelze on 2011-07-23
Depends what you want to do. A lot of third-party libraries haven't been ported to Python 3 yet, so if you want to use one of them, you will have to stick with Python 2. Otherwise, if you have no reason to stick with Python 2, you might as well use Python 3.

---

### Post by TwoEars on 2011-07-23
> **infectedorganism said:**
> Thanks for the responses!

Last question: Should I move to Python 3.x or stick with 2.x?

Well, that depends. If you want to write production code that relies on 3rd party software, stick with Python 2. Otherwise, Python 2 or Python 3 are both great, but there's more 3rd party resources out there for Python 2(so if you need examples, be sure to use 2to3 or learn the differences between the versions)

---

### Post by schauerlich on 2011-07-23
> **TwoEars said:**
> You can do the last, but I don't suggest doing it that way, not at all (it evaluates 'something' as a tuple).

Nope.

```
$ python
Python 2.6.1 (r261:67515, Dec  6 2008, 16:42:21) 
[GCC 4.0.1 (Apple Computer, Inc. build 5370)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> ("foo")
'foo'
>>> ("foo",)
('foo',)
```

You have to include the comma for a one element tuple. Otherwise, any time you wanted to do some calculation involving parentheses, you'd just be creating a ton of tuples and then not evaluating them.

---

### Post by Bachstelze on 2011-07-23
> **schauerlich said:**
> 
```

Python 2.6.1 (r261:67515, Dec  6 2008, 16:42:21) 
[GCC 4.0.1 (Apple Computer, Inc. build 5370)] on darwin

```


Which version of OS X are you using? O.o

---

### Post by schauerlich on 2011-07-23
> **bachstelze said:**
> which version of os x are you using? O.o

10.6.7. Apple tends to be behind on their python releases. You've just reminded me to update.

---

### Post by unknownPoster on 2011-07-23
> **cgroza said:**
> 
Statements like if, while, for ... do not accept parenthesis.

That is mostly false.

If you don't believe me, run the following snippets of code:

```

 #!/usr/bin/python
while (True):
    print "It Works!"

```

```

#!/usr/bin/python
if ((1 == 1) and (2 != 3)):
        print "It Works"

```

You are correct about for loops though.

I typically find that wrapping conditionals in parenthesis can make them easier to read, especially if they are compound as in my second example.

EDIT: This works on Python 2.X, I haven't gotten into Python 3.0 yet, as it needs more widespread adoption.

---

### Post by Bachstelze on 2011-07-23
> **schauerlich said:**
> 10.6.7

You should upgrade to 10.6.8, then you'll have *GCC 4.2*!

```
firas@aoba ~ % python
Python 2.6.1 (r261:67515, Jun 24 2010, 21:47:49) 
[GCC 4.2.1 (Apple Inc. build 5646)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> 

```

---

### Post by unknownPoster on 2011-07-23
> **Bachstelze said:**
> You should upgrade to 10.6.8, then you'll have *GCC 4.2*!

```
firas@aoba ~ % python
Python 2.6.1 (r261:67515, Jun 24 2010, 21:47:49) 
[GCC 4.2.1 (Apple Inc. build 5646)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> 

```


Heh...I'm running 10.7 and I have this:

```


jeremiah:~ jeremiah$ python
Python 2.6.6 (r266:84374, Aug 31 2010, 11:00:51) 
[GCC 4.0.1 (Apple Inc. build 5493)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> 

```

---

### Post by Bachstelze on 2011-07-23
That is weird, why did they downgrade to GCC 4.0? I'm less and less eager to upgrade to Lion each day...

---

### Post by schauerlich on 2011-07-23
> **Bachstelze said:**
> That is weird, why did they downgrade to GCC 4.0? I'm less and less eager to upgrade to Lion each day...

Perhaps they're steering towards clang?

---

### Post by unknownPoster on 2011-07-23
> **Bachstelze said:**
> That is weird, why did they downgrade to GCC 4.0? I'm less and less eager to upgrade to Lion each day...

Actually, I did some research.

I may be mistaken, but I think that gcc version number is the gcc that your python was built with.

Regardless, OSX Lion doesn't include gcc, and it deletes it if you previously had it. That being said, the newest XCode (4.1) is free when you buy Lion, I'm downloading it now. I'll report back later.

---

### Post by Bachstelze on 2011-07-23
> **unknownPoster said:**
> Regardless, OSX Lion doesn't include gcc, and it deletes it if you previously had it. That being said, the newest XCode (4.1) is free when you buy Lion, I'm downloading it now. I'll report back later.

Good point, gcc does not actually come with OS X, but with Xcode. It's been like that at least since Leopard, but I forgot about it since I always install Xcode (Xcode has always been free, by the way).

---

### Post by schauerlich on 2011-07-23
> **Bachstelze said:**
> Good point, gcc does not actually come with OS X, but with Xcode. It's been like that at least since Leopard, but I forgot about it since I always install Xcode (Xcode has always been free, by the way).

XCode 4 actually costs $5 now if you're not in the Mac/iOS Developer Program.

---

