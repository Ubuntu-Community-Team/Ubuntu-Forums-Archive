---
title: "Python problem"
date: 2013-11-08
forum: Programming Talk
---

### Post by ML7rcEx on 2013-11-08
I am just an old geezer trying to learn Python so in case anyone asks it is definitely _not_ homework.

Have come across the problem where the script keeps throwing an error: ValueError: need more than 1 value to unpack
Could someone please tell me where i have gone wrong.

```

#!/usr/bin/python
from sys import argv

script, Peaches, Pears, Plums, Oranges, Limes = argv
print "This script is called:", script
print "Your first variable is:", Peaches
print "Your second variable is:", Pears 
print "Your third variable is:", Plums
print "Your fourth variable is:", Oranges
print "Your fifth variable is:", Limes

```

---

### Post by steeldriver on 2013-11-08
How are you invoking (running) the script? it expects to get 5 command-line arguments e.g.

```

$ ./pyargv.py qwerty uiop asdf ghjkl zxcv
This script is called: ./pyargv.py
Your first variable is: qwerty
Your second variable is: uiop
Your third variable is: asdf
Your fourth variable is: ghjkl
Your fifth variable is: zxcv

```

whereas if you call it without arguments

```

$ ./pyargv.py
Traceback (most recent call last):
  File "./pyargv.py", line 4, in <module>
    script, Peaches, Pears, Plums, Oranges, Limes = argv
ValueError: need more than 1 value to unpack

```

---

### Post by ofnuts on 2013-11-08
Works for me, with the right number of arguments when callng the script...

---

### Post by trent.josephsen on 2013-11-08
You need to run the script with at least 5 arguments in order for the multiple assignment to work:
```
% python2 spam.py spam eggs spam ham spam
This script is called: spam.py
Your first variable is: spam
Your second variable is: eggs
Your third variable is: spam
Your fourth variable is: ham
Your fifth variable is: spam
```
(edit: I gotta learn to type faster)

---

### Post by ML7rcEx on 2013-11-08
Can see where my mistake was now.
Big thanks to everyone for taking the time out to help an old geezer lol. Cheers!

---

