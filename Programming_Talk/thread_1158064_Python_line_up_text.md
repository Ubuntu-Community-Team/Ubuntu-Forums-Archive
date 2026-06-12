---
title: "Python line up text"
date: 2009-05-13
forum: Programming Talk
---

### Post by matmatmat on 2009-05-13
I have output like this:
```

Name|	|Nickname|	|Number|	|Email|
james|	||	||	||
a|	|a|	|a|	|a|

```
& I want it like this:
```

Name|	|Nickname|	|Number|	|Email|
james|	||	        ||	        ||
a|	|a|	        |a|	        |a|

```
can you do this is python?
(the table will end up with a lot of data in)

---

### Post by ghostdog74 on 2009-05-13
look at the print statement and its format specifiers. also you can try str.rjust() or str.ljust()

---

### Post by matmatmat on 2009-05-13
Thanks for the reply! What do you mean by format specifiers & will str.[r/l]just work as i have something like this:
```

data = "james|\t||\t||\t||\na|\t|a|\t|a|\t|a|"

```
data is the whole table apart from the "Name Nickname" bit, with lots of \t's and \n's
Wouldn't I have to write is as each colum a variable, eg:
```

name = "james"

```

---

