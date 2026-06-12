---
title: "python - locate list items in string"
date: 2009-09-23
forum: Programming Talk
---

### Post by smerny on 2009-09-23
I have a list of a few strings and a big txt file. What would be the best way find the location (or possibly multiple locations) of where the strings in the list exist in the txt file? (Line and position within the line)

---

### Post by ghostdog74 on 2009-09-23
show your input files, and describe your output.

---

### Post by ve4cib on 2009-09-23
[img]http://imgs.xkcd.com/comics/regular_expressions.png[/img]

If you know what a list looks like (probably enclosed in [] characters, with 1 or more alpha-numeric strings, separated by commas) you can create a regex and apply that to your input file.  Should do the trick.

Unless of course I've completely misunderstood your goal.

---

### Post by smerny on 2009-09-23
input should be flexible... output can be something like...


if search[1] = "blue" and the word "blue" and lets say that line 5 of the txt file says "There was a blue crayon." and line 11 says "He drew a blue ball."

the output should be:

> The word "blue" shows up on:
- line 5 on the 13th character
- line 11 on the 10th character

The word "whatever" shows up on:
- ...etc

---

### Post by ghostdog74 on 2009-09-23
so what have you tried on your own? have you read up on Python's basics?

---

### Post by ve4cib on 2009-09-23
There's a convenient function called "find" that's a member of the string class.  Chances are you'll be wanting to use that *hint-hint*.

```

>>> print "".find.__doc__
S.find(sub [,start [,end]]) -> int

Return the lowest index in S where substring sub is found,
such that sub is contained within s[start:end].  Optional
arguments start and end are interpreted as in slice notation.

Return -1 on failure.

>>> s="The blue ball rolled under the red car"
>>> s.find('blue')
4
>>> s.find('red')
31
>>> s.find('green')
-1

```

---

### Post by A_Fiachra on 2009-09-24
> **ve4cib said:**
> There's a convenient function called "find" that's a member of the string class.  Chances are you'll be wanting to use that *hint-hint*.

..


Oh, sure -- if you want to do it the easy way!!!!


First ... get the source code for egreg, install the boost C++ python libraries, fire up bison and flex and start a pot of coffee.

Now the nontrivial part ....


:P

---

### Post by A_Fiachra on 2009-09-24
s/egreg/egrep/

---

### Post by ve4cib on 2009-09-24
> **A_Fiachra said:**
> Oh, sure -- if you want to do it the easy way!!!!


First ... get the source code for egreg, install the boost C++ python libraries, fire up bison and flex and start a pot of coffee.

Now the nontrivial part ....


:P

"There should be one (and preferably only one) obvious way of doing something."

Wise words from our Benevolent Dictator for Life...

---

