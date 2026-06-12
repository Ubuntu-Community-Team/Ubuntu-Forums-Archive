---
title: "I know there is an easy answer to my question in regards to date manipulation"
date: 2008-09-12
forum: Programming Talk
---

### Post by nuclearj on 2008-09-12
Okay so what I want to do is extract integers from some date data types in Python

so i figure I would use the localtime() function? class? i'm not sure what that is called.  I think is a class right?  Anyway, is there a way to extract the data (Year, Month, Day, etc...) and turn them into integers?

After they are turned into integers I am using them for calculations.

```

>>>import from time localtime
>>> localtime()
(2008, 9, 11, 22, 1, 43, 3, 255, 1)

```

thanks for the help!

---

### Post by Def13b on 2008-09-12
I may have misinterpreted but you mean like,

year = localtime()[0]

(note that this is already an int so no need to change it)

some more reading,

[http://docs.python.org/tut/node7.html#SECTION007300000000000000000](http://docs.python.org/tut/node7.html#SECTION007300000000000000000)

---

### Post by nuclearj on 2008-09-12
exactly!  I knew it was an easy solution.  Thanks!

---

