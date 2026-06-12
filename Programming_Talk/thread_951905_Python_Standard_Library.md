---
title: "Python Standard Library"
date: 2008-10-18
forum: Programming Talk
---

### Post by tiachopvutru on 2008-10-18
I was learning Python around 3 months ago for about a month until I stopped (discouraged because couldn't solve Project Euler 15, laziness, wanted to enjoy the rest of summer, and for the last month, school).

I'm back to Python again and this time I'm thinking of learning Python Standard Library. However, its size is too big for me to handle, so I would like to know what modules are most commonly used for some selective learnings.

Thanks for any helps. :)

---

### Post by Can+~ on 2008-10-18
Python libraries are usually learnt when you need them. "I need to do X, look in google, learn how to use it, implement it". But if you have spare time to learn, it can't hurt, right?

The choice of libraries is dependant on what you want to do. I'll give you my personal favourites:

[Regular Expressions](http://pydoc.org/2.5.1/re.html) (re) Regular expressions are sometimes useful, others you can stick to split().
[Itertools](http://pydoc.org/2.5.1/itertools.html) (itertools) Impressive library, gives you more control over iterations.
[Sql Lite 3](http://pydoc.org/2.5.1/sqlite3.html) (sqlite3) Sqlite is a portable C library for creating tables (.sqlite), allowing the use of SQL over them, great storing solution.

---

### Post by pmasiar on 2008-10-18
Start PythonChallenge, and learn modules you need to solve each level 8-)

---

### Post by y-lee on 2008-10-18
I agree you usually learn the modules as you need them. But if you want a list here is some of the ones I find the most necessary for me, so far.

cmath math random 
string stringIO
ConfigParser
getop
os os.path sys
re
itertools
pickle
parser
stat
datetime
copy
logging
time
timeit
urllib and json
Sql Lite 3

---

### Post by tiachopvutru on 2008-10-18
Well, I thought that there would be some modules in Python Standard Library where you couldn't do without no matter what (because they're extremely commonly used), and the others are for learning as you go.

> **pmasiar said:**
> Start PythonChallenge, and learn modules you need to solve each level 8-)

I could barely do the non-programming riddle thingy that PythonChallenge is based on (didn't get past many levels). I have also done PythonChallenge before, but could only gotten past level 0... =p I couldn't tell what it wanted me to do for later levels.

---

### Post by Can+~ on 2008-10-18
Here's the full library (2.6) sorted by "section" instead of only alphabetically:

[http://docs.python.org/library/index.html](http://docs.python.org/library/index.html)

This will help you get to the subject you're interested in.

---

