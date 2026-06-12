---
title: "python regular expression help"
date: 2011-02-02
forum: Programming Talk
---

### Post by fokuslee on 2011-02-02
Hi i am trying to match certain file names
i want to match things with few digits appeneded to the end preceded by underscore
such as file_1 and file_12
I do not want to match file1 or file2...
my take would be 
import re
m = re.match('$_/d+','blah_12')
but m always return None
what did i do wrong?
thanks
:popcorn:

---

### Post by Arndt on 2011-02-02
> **fokuslee said:**
> Hi i am trying to match certain file names
i want to match things with few digits appeneded to the end preceded by underscore
such as file_1 and file_12
I do not want to match file1 or file2...
my take would be 
import re
m = re.match('$_/d+','blah_12')
but m always return None
what did i do wrong?
thanks
:popcorn:

What are the $ and / doing there?

---

### Post by kostkon on 2011-02-02
Just a tip: install and try [*kodos*]("http://packages.ubuntu.com/maverick/kodos"). It will help you to easily test and debug you python reg exps.

---

### Post by fokuslee on 2011-02-02
sorry for my sloppyness it should be a \
i actually have it like this

>>> import re
>>> m = re.match('$_\d+','blah_12')
>>> print m
None

\d means [0-9]
$ means i only want to see the match at the end
so file_1_stuff will not match 

at least that is my understanding from the python docs online

---

### Post by kurum! on 2011-02-02
With Ruby, but similar regex in Python.
```

>> filename="file_12"
=> "file_12"
>> filename.match(/^.*_\d+$/)
=> #<MatchData "file_12">


```

---

### Post by fokuslee on 2011-02-02
ok i need to use re.search() not re.match
match will only look at begining of string
need to read docs mroe carefully
thanks

---

### Post by Arndt on 2011-02-02
> **fokuslee said:**
> sorry for my sloppyness it should be a \
i actually have it like this

>>> import re
>>> m = re.match('$_\d+','blah_12')
>>> print m
None

\d means [0-9]
$ means i only want to see the match at the end
so file_1_stuff will not match 

at least that is my understanding from the python docs online

The $ needs to be at the end for it to work that way. I don't know whether $ has any useful function in some other position.

It starts matching at the beginning, so you need to match what comes before the interesting part:

```
re.match('.*_\d+$','abc_56')
```

or use re.search.

---

