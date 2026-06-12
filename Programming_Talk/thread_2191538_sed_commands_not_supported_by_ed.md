---
title: "sed commands not supported by ed?"
date: 2013-12-03
forum: Programming Talk
---

### Post by sha1sum on 2013-12-03
Hello guys and gals,

Before, when I wrote a script and I had to change a text file, I'd do it like this:

```

cat text.txt | sed 's/colour/color/g' > temp.txt
mv temp.txt text.txt

```

However, I learned that this is frowned upon, and that a better (or at least more accepted) way to do it would be this:

```

ed -s text.txt << EOF
g/colour/s//color/g
w
EOF

```


However, I can't get certain sed commands to work in ed, for example:

in sed you can do something like this:

```
sed '/[0-9]/!d' file.txt    # this deletes all lines that do not contain a number. 
```

I've found that if you place an exclamation mark after a regular expression in ed, you get an error.

So my question is: Is it true that ed doesn't have an equivalent for certain sed commands. And if yes, how do you work around that in a script?

---

### Post by sha1sum on 2013-12-03
Nevermind guys. I found that ed has the same option, but just with different syntax. If you want to match all lines that not match a certain regular expression, you do it like this:

```
ed -s file.txt << eof
v/[0-9]/d
eof

```

ie: you put 'v' before the regular expression, instead of '!' after it. Manuals are useful :-D

---

### Post by r-senior on 2013-12-03
GNU sed also has the -i or --in-place option:

```
 -i[SUFFIX], --in-place[=SUFFIX]

                   edit files in place (makes backup if SUFFIX supplied)

```

---

### Post by sha1sum on 2013-12-03
Okay, one more question

If I want to delete all the lines that don't contain a dollar sign $, I need to double backslash escape it like this:

```

ed -s file.txt << EOF
v/\\$/d
w
EOF

```

If I use a single backslash escape before the dollar sign, it is still interpreted as a meta character. Why is that?

EDIT: I think I see why: when you write \$ in a here document, shell thinks you're escaping a variable So you have to place another backslash. Today I'm answering all my own questions lol.

---

### Post by sha1sum on 2013-12-03
> **r-senior said:**
> GNU sed also has the -i or --in-place option:

```
 -i[SUFFIX], --in-place[=SUFFIX]

                   edit files in place (makes backup if SUFFIX supplied)

```

That's useful! I didn't know that, thanks :-)

---

