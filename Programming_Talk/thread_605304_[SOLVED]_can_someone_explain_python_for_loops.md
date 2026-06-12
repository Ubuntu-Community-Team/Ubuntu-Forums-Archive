---
title: "[SOLVED] can someone explain python for loops"
date: 2007-11-06
forum: Programming Talk
---

### Post by Nefarious on 2007-11-06
Ok, so being a C only user for i dunno 5yrs maybe and deciding to try a new language I am immensely frustrated with for loops in python I JUST CANT UNDERSTAND how to read it. 

not only that but python just gets me frustrated in general. ( but i do want to learn it)

also if you could recommend some python resources, so far I'm using Dive into python and I have a sh#t load of Ebooks that I've found.

(sry if I sound stupid I'm really tired)

---

### Post by LaRoza on 2007-11-06
> **Nefarious said:**
> Ok, so being a C only user for i dunno 5yrs maybe and deciding to try a new language I am immensely frustrated with for loops in python I JUST CANT UNDERSTAND how to read it. 

not only that but python just gets me frustrated in general. ( but i do want to learn it)

also if you could recommend some python resources, so far I'm using Dive into python and I have a sh#t load of Ebooks that I've found.

(sry if I sound stupid I'm really tired)

It is like a "foreach" loop.

In C:

[php]
int x[10];
int i;
for (i = 0; i < 10; i ++)
{
    x[i] = 0;
}
[/php]

in Python:

```

for i in x:
    i = 0

```

This assumes x is a list.

If you want to iterate a given number of times, use the range() function.

```

for i in range(10):
    print i

```

This prints the integers up to 10.

Python loops are built for iterating over arrays.

---

### Post by cwaldbieser on 2007-11-06
For loops in python are similar to:
+ "For each" loops in Visual Basic
+ for loops in bash
+ The std::for_each algorithm in the C++ standard library.

Basically, the idea is that you have a sequence of elements.  The for loop lets you iterate over that sequence of elements in order.  In python, that sequence is often finite, but it doesn't have to be.

For example:
```

l = [4, 1, 2, 3]
for elm in l:
    print elm

```
This code prints out the elements of the list, l, in order.  The sequence is finite, so it terminates after the last element is printed.
```

def repeat(expr):
    while True:
        yield expr

for elm in repeat("Whee!"):
    print elm

```
This is an infinite loop.  The function, repeat(...), is a generator that constantly produces the same expression for every iteration.

```

x = zip(range(10), repeat("Whee!"))

```  
This code zips together two sequences.  Since one of the sequences is finite, the resulting sequence is also finite.  It has the same length as the shortest sequence.

To produce the same counting behavior as a typical "for" loop in C or JavaScript, you would do something like:
```

for i in xrange(100):
    print i

```
The generator function, xrange(...), produces the integers in a sequence starting from 0 up to 99 (the upper bound of 100 was given in this example)..

---

### Post by LaRoza on 2007-11-06
> **cwaldbieser said:**
> 
For example:
```

l = [4, 1, 2, 3]
for elm in l:
    print l

```
This code prints out the elements of the list, l, in order.  The sequence is finite, so it terminates after the last element is printed.

No, that prints l 4 times, it should be:

```

for elm in l:
    print elm

```

---

### Post by Wybiral on 2007-11-06
It's pretty simple... It uses iterators.

[http://docs.python.org/lib/typeiter.html](http://docs.python.org/lib/typeiter.html)

Try writing your own class that supports iterating and use a "for" loop to iterate it. It helps to know whats going on behind the scenes.

---

### Post by Nefarious on 2007-11-07
ok, but how would i read something like this

```
method for method in dir(object)
```

its the first "method" that bugs me

is the first method being assigned dir(object) or something

---

### Post by samjh on 2007-11-07
That code doesn't look like valid Python.

---

### Post by smartbei on 2007-11-07
I get it, you are talking about list comprehensions - not exactly "for" loops.

List comprehensions take a form similar to the one Nefarious posted above, except they are written with [ ] around them. A valid list comprehension would be:
```

l = [a*2 for a in range(10)]

```
This is equivalent to:
```

l=[]
for a in range(10):
    l+=[a*2]

```
Basically, it goes through the list returned by range, assigns the current value to a and appends a*2 to the list l.

In your (Nefarious) example, 
```

method for method in dir(object)

```
remember that dir returns a list. The variable method would take, in order, each method from dir and (in your example) not do much of anything with it. Say dir(object) returns:
```

['join','split','eat','explode']

```
method would in each be equal to one of those, in order (first 'join', then 'split' ...).

Hope that helps.

---

### Post by pmasiar on 2007-11-07
"Dive into Python" might not have more modern constructs like list comprehension. Read "what is new" for couple recent Python versions. Many new cool features were added, not covered by old books and tutorials. Python tutorial, included in each distro, covers all features, including the most recent, so you may want to browse through it.

[http://docs.python.org/tut/node7.html](http://docs.python.org/tut/node7.html)

---

### Post by Nefarious on 2007-11-07
Thanx smartbei, now I can continue my venture into python :).

---

