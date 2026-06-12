---
title: "[SOLVED] Simple regex question with python"
date: 2008-08-31
forum: Programming Talk
---

### Post by realitybites on 2008-08-31
i am very new to python, so sometimes i have small problems
my question is, how do i extract the matched pattern from the string. for example, i have a path like /home/user/movie_name how do i extract the movie_name from this string?

---

### Post by ghostdog74 on 2008-08-31
> **realitybites said:**
> i am very new to python, so sometimes i have small problems
my question is, how do i extract the matched pattern from the string. for example, i have a path like /home/user/movie_name how do i extract the movie_name from this string?

```

>>> a="/home/user/movie_name"
>>> import os
>>> os.path.split(a)
('/home/user', 'movie_name')
>>> os.path.split(a)[-1]
'movie_name'

```
or just simply string split
```

>>> a.split("/")
['', 'home', 'user', 'movie_name']
>>> a.split("/")[-1]
'movie_name'

```
or simply using some of the string functions
```

>>> a[a.rindex("/")+1:]
'movie_name'

```
please read up the documentations, as well as the Python tutorial to get familiar.
   |
   |
   |
   v

---

### Post by realitybites on 2008-08-31
that will work for path names but what i really want is to extract matched pattern from a random string.
for example let the regex be [0-9]{4} and the string is "qweasd0000asd". how do i print "0000"

---

### Post by ghostdog74 on 2008-08-31
In Python, to use regex, you use the re module
```

import re
pat=re.compile("\d{4}")

```
or just using the basics (not tested)
```

for n,i in enumerate(s):
  if s[n:n+4].isdigit():  print s[n:n+4]


```

---

### Post by realitybites on 2008-08-31
i realized now that i wasn't very specific about my question
i know about the re module and regex syntax. and my regexes are not specific, so specific things like digit check or split() won't work, i need pattern match.
what i don't know is extracting the "0000" from previous example, not as digits, but as a pattern.

to sum up, when a pattern in a string is matched via regex, i need that pattern

---

### Post by pmasiar on 2008-08-31
Generic patter matching is not easy - regex is it's own specialized programming language. It's not easy to learn but powerful (and standard - embedded in many languages).

Power of Python is that 60-80% of cases for beginners can be solved in much simper way, using plain string methods one after another: split, startwith, endswith, in, etc.

So either bite the bullet and learn re language, or just avoid it for couple months - with Python, avoiding is rather painless.

---

### Post by WW on 2008-08-31
ghostdog74 showed you how to create a pattern for four digits.  One of the functions that you can use with this pattern is **findall**.  For example,
```

>>> import re
>>> pat = re.compile("\d{4}")
>>> str = "qweasd0000asd" 
>>> matches = re.findall(pat,str)
>>> matches
['0000']
>>> str2 = "abc 1234 56 78910"
>>> matches2 = re.findall(pat,str2)
>>> matches2   
['1234', '7891']
>>> # Actually, it is not necessary to compile the pattern first:
... 
>>> re.findall(r'\d{4}',str2)
['1234', '7891']
>>> 

```
More details can be found in [Section 4.2](http://docs.python.org/lib/module-re.html) of the [Python Library Reference](http://docs.python.org/lib/lib.html), although the example in [Section 10.5](http://docs.python.org/tut/node12.html#SECTION0012500000000000000000) of the [Python Tutorial](http://docs.python.org/tut/tut.html) might be enough to do what you want.

---

### Post by realitybites on 2008-08-31
thanks WW, that's what i want. i looked through docs before but couldn't realized it, i guess.

---

### Post by mssever on 2008-08-31
You might also be interested in reading up on backreferences (finding what was matched inside the parentheses in your regex).

<rant>Python does many things right, but regular expressions are not one of them. Python makes them more complicated than they need to be.</rant>

---

### Post by pmasiar on 2008-08-31
> **mssever said:**
> <rant>Python does many things right, but regular expressions are not one of them. Python makes them more complicated than they need to be.</rant>

What way of doing regex is simpler? Perl way?

It was deliberate (and IMHO smart) decision to put 75% of basic functionality into string methods, and rest to re library. So language is not polluted by regex functionality like Perl is (so beginner can access 75% of functionality with 10% of effort), and experts are not limited by whatever regex syntax was frozen at some time: if better regex library appears, it will be much easier to switch to it, as if regex was part of syntax.

So you may disagree but IMHO Guido did the right decision regarding regex.

---

### Post by mssever on 2008-09-01
> **pmasiar said:**
> What way of doing regex is simpler? Perl way?I don't know Perl, so I can't comment on Perl's regexps. Ruby supports regexps at the syntax level, and many regexp operations don't involve manipulating a regexp object. For example, to print the matched portion of a string, only if the string matches, ```
if string =~ /^some regex ([0-9]+)/
  puts $1 # $[0..n] is a regexp backreference. They're badly-named, though, because
          # in Ruby, variables beginning with $ are global, yet $1 is a local variable.
end
```Of course, this kind of thing violates Python's philosophy, and I don't expect Guido to change that. Python is a very well-designed language, but every design has its suboptimal corner cases--and sometimes a perfect solution isn't possible.

> experts are not limited by whatever regex syntax was frozen at some time: if better regex library appears, it will be much easier to switch to it, as if regex was part of syntax.That's a valid point. And I think I've read that Python has changed regex libraries at least once. Of course, Python's syntax does evolve over time, as well.

I guess my opinion on this comes down to the fact that I find built-in regexps to be much more convenient from my perspective as a language user, not a developer, but I recognize that there are valid reasons for Python's approach. This also reminds me of your bias thread, as my reasoning clearly exposes a bias of mine, since I didn't even consider the implications of how regexps are implemented from a language designer's perspective.

---

### Post by pmasiar on 2008-09-01
> **mssever said:**
> I don't know Perl, so I can't comment on Perl's regexps. Ruby supports regexps at the syntax level, and many regexp operations don't involve manipulating a regexp object.

Yup, regex is one of places where Ruby shows Perl heritage. :-)

> They're badly-named, though, because in Ruby, variables beginning with $ are global, yet $1 is a local variable.

So, for sake of convenience for experts, confusion was added for beginners.

Zen of Python says: "Special cases are not special enough to break the rules" :-) 

> but every design has its suboptimal corner cases--and sometimes a perfect solution isn't possible.

When designing language, like anything else, you need to make compromises. Guido decided that simple methods in strings are enough for total beginners, and more advanced hackers can deal with re.

> Python's syntax does evolve over time, as well.

Yes, but all changes up to Python 3.0 were backward-compatible. Py3K is first real break, and it is huge deal to make it almost painless.

> This also reminds me of your bias thread, as my reasoning clearly exposes a bias of mine, since I didn't even consider the implications of how regexps are implemented from a language designer's perspective.

Yup, exactly. Every feature has a price (you need to learn it's syntax even if you don't use it, and maintain it's implementation as you add newer features), so for a designer is very important to say 'No' even if someone provided working patch for some feature.

---

