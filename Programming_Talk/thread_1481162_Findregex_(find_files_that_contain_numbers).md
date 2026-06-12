---
title: "Find/regex (find files that contain numbers)"
date: 2010-05-12
forum: Programming Talk
---

### Post by altonbr on 2010-05-12
I'm pretty new to regexs, let along find's implementation of how to use regexs.

I'm looking to find all files that contain numbers, not just end in them.

Currently, my regex just returns files that end in a number...
```
find . -regex ".*[0-9]+"
```Any advise?

I guess this could work:
```
find . | egrep '0|1|2|3|4|5|6|7|8|9'
```

---

### Post by ja660k on 2010-05-12
find . 
will return all files and files in subfolders of your current working directory...
if thats what you want fine...

so your regex, 

\d matches any digit, 
\d is the same as [0-9]

but short  :-)
That being said, egrep regex engine doesnt support \d (i think)

so youll have 
```

ls | egrep '[0-9]'
```

and that returns files & dirs with a digit in them.

```
ls | egrep '^[0-9]'
```

will return files/folders where a number is at the start

```
ls | egrep '[0-9]$'
```

will return files/folders with a number at the end.

happy regex'ing

---

### Post by schauerlich on 2010-05-12
```
schauerlich@inara:~/clean$ ls -R
3three bar foo foobar one two2

./foo:
4four4 five5five
schauerlich@inara:~/clean$ find . | egrep "[0-9]"
./3three
./foo/4four4
./foo/five5five
./two2
schauerlich@inara:~/clean$

```

---

### Post by hannaman on 2010-05-12
find . -name "*[0-9]*" doesn't work?

---

### Post by schauerlich on 2010-05-12
> **hannaman said:**
> find . -name "*[0-9]*" doesn't work?

That's much too simple an efficient. :) (d'oh)

---

