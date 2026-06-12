---
title: "Grepping multiple lines at once?"
date: 2010-11-24
forum: Programming Talk
---

### Post by durand on 2010-11-24
Hi!

I've got an interesting problem and I'm not sure about how to go about it with grep. Basically, I have a file with 10 million lines which are all numbers:

1
2
3
6
23
42
64
2
1
2
3

I want to count the number of times the pattern "1
2
3" repeats in the file. I figured that grep would be the most efficient way to do this but it seems that if I just grep for "1
2
3", it matches lines containing just 1s or 2s or 3s rather than a complete pattern which I don't understand why. Does anyone know of a solution? Alternatively, I can create the file with spaces instead of newlines but grep basically just gives me a count of 1 because it counts the number of lines containing the pattern rather than the number of patterns in the single line that the file is made of, which is totally useless to me.

So any help would be massively appreciated! Thanks!

---

### Post by amauk on 2010-11-24
```
cat your_file | tr '\n' ' ' | grep -o '[^0-9]\?1 2 3[^0-9]\?' | wc -l
```

basically, translate all newlines to space, then match "1 2 3" and count the matches

The test for an optional non-numeric before & after means this will not match "21 2 3" or "1 2 36" or similar

*edit*
oops, fixed a bug in the regex pattern

---

### Post by Arndt on 2010-11-24
> **amauk said:**
> ```
cat your_file | tr '\n' ' ' | grep -o '[^0-9]\?1 2 3[^0-9]\?' | wc -l
```

basically, translate all newlines to space, then match "1 2 3" and count the matches

The test for an optional non-numeric before & after means this will not match "21 2 3" or "1 2 36" or similar

*edit*
oops, fixed a bug in the regex pattern

I'm not sure that grep can handle a line millions of characters long. Maybe it can, though.

Personally, I would write a small program for this purpose.

---

### Post by durand on 2010-11-24
Yeah, my friend's doing that, I thought grep would work as well though. And yeah, grep might not support such a big file.

EDIT: I forgot to say thanks to both of you :)

---

### Post by mo.reina on 2010-11-24
in python
```
import re

def run():
    with open('file.txt') as f:
        a = f.read()
    print len(re.findall(r'.*(1\n2\n3\n).*', a))
```

---

### Post by Arndt on 2010-11-24
> **mo.reina said:**
> in python
```
import re

def run():
    with open('file.txt') as f:
        a = f.read()
    print len(re.findall(r'.*(1\n2\n3\n).*', a))
```

This matches

11
2
3

too, but I don't know how to fix that elegantly. I've never used multi-line regexps much. Inserting ^ before the 1 doesn't work, in any case.

---

### Post by mo.reina on 2010-11-24
i'm no regex expert, but try changing the last line to this:

```
  print len(re.findall(r'(?<!1)(1\n2\n3\n)', a))
```

that's a negative look behind assertion, so it should match as long as the letter preceding the pattern isn't 1

---

### Post by Arndt on 2010-11-24
> **mo.reina said:**
> i'm no regex expert, but try changing the last line to this:

```
  print len(re.findall(r'(?<!1)(1\n2\n3\n)', a))
```

that's a negative look behind assertion, so it should match as long as the letter preceding the pattern isn't 1

Now it matches

21
2
3

---

### Post by MadCow108 on 2010-11-24
edit doesn't work :( matches 1 2 2 3

ugly but it uses only grep ;)
grep -A 3 -E "^1$" test.txt | grep -E "^2$" -B 1 -A 1 | grep -E "^3$" -B 2
count by grepping again:  grep "\-\-" | wc -l (+ 1)

non-regex python:
```

import io

file = io.open("test.txt")
c = 0 
for l in file:
  if l == "1\n" and file.next() == "2\n" and file.next() == "3\n":
    c += 1

print(c)

```

---

### Post by mo.reina on 2010-11-24
ok this is a bit of a hack, it's not pretty and i'm not proud of it... 

```
 print len(re.findall(r'(\n1\n2\n3\n|^1\n2\n3\n)', a))
```

so there are two patterns being matched, either there's a new line that preceds 1, but this won't count 1 2 3 if it's found at the beginning of the file, so i added a separate pattern ^1\n2\3\n.

i'm sure there are better ways to do this but it should work.

---

### Post by Arndt on 2010-11-25
> **MadCow108 said:**
> edit doesn't work :( matches 1 2 2 3

ugly but it uses only grep ;)
grep -A 3 -E "^1$" test.txt | grep -E "^2$" -B 1 -A 1 | grep -E "^3$" -B 2
count by grepping again:  grep "\-\-" | wc -l (+ 1)

non-regex python:
```

import io

file = io.open("test.txt")
c = 0 
for l in file:
  if l == "1\n" and file.next() == "2\n" and file.next() == "3\n":
    c += 1

print(c)

```

This doesn't match

1
1
2
3

---

### Post by amauk on 2010-11-25
> **Arndt said:**
> I'm not sure that grep can handle a line millions of characters long. Maybe it can, though.

Personally, I would write a small program for this purpose.
Grep (or any of the standard text stream utilities) can handle any sized input

---

### Post by durand on 2010-11-25
Cheers for the python stuff. It would have worked for my problem when it matched 21 2 3 because what I didn't really tell you was that every number was a decimal between 0 and 1. But in any case, the reason I was doing that was because I was trying to find the periodicity of the rand() c function which further research tells me is 2^32 ~= 4 billion and I couldn't create a file with 9 billion values (to get the period twice) without my hard drive or grep complaining so either way, it was impractical.

Python would have been even worse really but I guess if I left it long enough, it would have worked. Anyway, those snippets are quite useful for other things so I'll keep this thread in mind.

Thanks everyone!

---

