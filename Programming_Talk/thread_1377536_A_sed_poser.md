---
title: "A sed poser"
date: 2010-01-10
forum: Programming Talk
---

### Post by meastwood on 2010-01-10
Hi -

I would like to know if 'what I'd like to do' can be done with sed. I know it can be done with awk, and I've done it with python - I only want to know if it can be done with sed!!

I have a line of text:
```
"static/lpi-cmd-index.html:#:A #:B #:C #:D #:F"
```

Using sed .. (preferably a one-liner) .. I want to change this to
```
static/lpi-cmd-index.html:/static/lpi-cmd-index.html#:A
static/lpi-cmd-index.html:/static/lpi-cmd-index.html#:B
static/lpi-cmd-index.html:/static/lpi-cmd-index.html#:C
static/lpi-cmd-index.html:/static/lpi-cmd-index.html#:D
static/lpi-cmd-index.html:/static/lpi-cmd-index.html#:F
```

I can get so far -
```
$ a="static/lpi-cmd-index.html:#:A #:B #:C #:D #:F"
$ echo $a | sed 's/\([^:]*\):\(#:.*$\).*/\1:\/\1\2/; :a ;s/ /\ncc/;/ /b a'
static/lpi-cmd-index.html:/static/lpi-cmd-index.html#:A
cc#:B
cc#:C
cc#:D
cc#:F
```

However I want 'cc' to be whatever string/filename appears before the first ':'
Hardcoding the 'filename' is not an option.

The problem is being able to access/use the value of the group \1 in the first command from subsequent commands - maybe this is not the way to do it.

cheers

---

### Post by Brandon Williams on 2010-01-10
You don't need to "remember" the \1 from the first substitution, since you're putting that string at the beginning of every line and can pull it out again at the start of every loop.

```
echo "$a" | \
sed 's/^\([^:]*\):\(.*\)$/\1:\/\1\2/;
     :a ;s/^\([^#]*\)\(.*\) \(.*\)$/\1\2\n\1\3/;/ /b a;'
```

Line one replaces the relative filename component of the line with the relative:absolute construction you want. Line two loops over the line and replaces every space with '\n:relative:absolute'.

---

### Post by meastwood on 2010-01-10
Nice one - thanks :D

Took me blooming ages to get as far as I did ... 

Just using it as a comparison between 'sed' and python's re module.

---

