---
title: "What is the easiest way to reformat a text file?"
date: 2012-06-13
forum: Programming Talk
---

### Post by xytron on 2012-06-13
I have a plain text file of sun spot data.
It is formatted as follows;


```

year   month   sun spot number    deviation

1749    1         58.0             24.1


```
All I need from this file is the sun spot number as a complex number with the imaginary part set to 0,  so that the example above should be;
```

58.0, 0

```

The file has 3160 lines so reformatting it by hand will take a long time.

I know I could write a program to do this, but is there some simple utility to do this (preferably one that also works on Windows).

Thanks for any suggestions.

---

### Post by Bachstelze on 2012-06-13
```
awk '{print $3 ", 0"}' input.txt
```

There probably are Windows builds of awk around...

---

### Post by trent.josephsen on 2012-06-13
Simple utilities on Windows? You've GOT to be joking! :lolflag:

This is the kind of thing awk, sed and perl are made for. I came up with the following awk one-liner in about 1 minute -- would've been quicker with perl because I know Perl better, but the complexity of the problem doesn't really merit throwing the entire Swiss Army chainsaw at it.

```
awk '{print $3 ", 0"}' old_file.txt >new_file.txt
```

---

### Post by xytron on 2012-06-13
> **Bachstelze said:**
> ```
awk '{print $3 ", 0"}' input.txt
```

There probably are Windows builds of awk around...

Thanks, I'll look for it.

---

### Post by xytron on 2012-06-14
There's a "gawk" for Windows but I get an error on the above commands when I use that;

```

gawk: cmd. line:1: '{print
gawk: cmd. line:1: ^ invalid char ''' in expression

```

There's also a "sed.exe" Do you know the formatting command for that one?

Thanks.

---

### Post by Bachstelze on 2012-06-14
Hmm, quoting works differently in Windows... Do

```
awk "{print $3 \", 0\"}" input.txt
```

---

### Post by xytron on 2012-06-14
> **Bachstelze said:**
> Hmm, quoting works differently in Windows... Do

```
awk "{print $3 \", 0\"}" input.txt
```

Terrific, that worked!

Thank you for your help Bachstelze and trent.josephsen.

---

