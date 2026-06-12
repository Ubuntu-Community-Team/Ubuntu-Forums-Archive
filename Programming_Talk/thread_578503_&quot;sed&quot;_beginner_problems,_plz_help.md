---
title: "&quot;sed&quot; beginner problems, plz help"
date: 2007-10-17
forum: Programming Talk
---

### Post by philip.yhelzon on 2007-10-17
I've studying a bit of shell scripting of a book, and I came a long a problem, the book it talking about the "sed" command, it says I should type some thing like:
sed -e 's/\(<[^ ]*>\)\([ ]*\)\(<[^ ]*>\)/\3\2\1/g'
and then when I start typing to stdin it should revers the 2 first words.
it looks alright, but it doesn't work :confused: ?

I'm using the default shell in Ubuntu 7.04 (I think it's dash).

What am I doing wrong??   thanx guys :)

---

### Post by ghostdog74 on 2007-10-17
i removed the < and >. 
the input file should have spaces in between the first 2 words in order for the sed to work

```

# cat file
05/03/2001 73,110,abc
05/04/2001 73,120,def
05/05/2001 99,120,ghi
# sed -e 's/\([^ ]*\)\([ ]*\)\([^ ]*\)/\3\2\1/g' file
73,110,abc 05/03/2001
73,120,def 05/04/2001
99,120,ghi 05/05/2001



```

---

### Post by philip.yhelzon on 2007-10-18
Thanx, works great :)
One question...how come the syntax is different?   shouldn't it be the same on all distros?

---

### Post by ghostdog74 on 2007-10-18
> **philip.yhelzon said:**
> Thanx, works great :)
One question...how come the syntax is different?   shouldn't it be the same on all distros?

it depends on how your input file data looks like. i have provided example of the input file the doesn't have < and >

---

