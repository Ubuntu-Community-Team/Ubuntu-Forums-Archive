---
title: "grep without spaces"
date: 2007-09-28
forum: Programming Talk
---

### Post by wrathkeg on 2007-09-28
Hi,

I am trying to search through text files using grep (though if there is a better tool for the job, I could use something else).  I want to identify all of the instances of the characters "a", "n", "d", in that order, but without spaces between them.    I can do this:
```
grep "a.*n.*d" foo.txt
```
which seems to work, with the exception that it returns all lines with those characters, even when there is an intervening space.

Does anyone have any ideas?

TIA

WK

---

### Post by wrathkeg on 2007-09-28
just after I posted, I found what seems to be the answer: using [^ ] in the pattern.  If there are better ideas, I'd still love to hear them.
WK

---

### Post by ghostdog74 on 2007-09-28
can you post your sample file, and describe what you want to grep

---

### Post by amo-ej1 on 2007-09-28
```

 grep -e "a[^\ ]*n[^\ ]*d"

```
Would've been my suggestion to. 

If you're only working with ascii test (searching within a string) you could use

```

 grep -e "a[a-z]*n[a-z]*d"

```

---

### Post by eph1973 on 2007-09-28
Not sure I understand what you are asking, but it looks like you are looking for something like
```
grep ".*and.*"
```which should return the whole line if the letters "and" are together with no spaces in between them.  Place the option -n if you want which line number each occurs.

If you are looking for the letters "and" in a word, but not necessarily next to each other, you could use:
```
grep ".*\w*a\w*n\w*d.*"
```

---

