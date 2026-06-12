---
title: "find strings that are in two different files"
date: 2011-11-28
forum: Programming Talk
---

### Post by ryanrio95 on 2011-11-28
for example.
i have file.txt that contains

the quick brown fox
jumps over the
lazy
dog

and file2.txt contains

de snell brown fox
jumpt ssss the dog

than i need an script that outputs the words that are in both files so the output would be:

the
brown
fox
dog

can someone help?

greets, ryan

---

### Post by Arndt on 2011-11-28
> **ryanrio95 said:**
> for example.
i have file.txt that contains

the quick brown fox
jumps over the
lazy
dog

and file2.txt contains

de snell brown fox
jumpt ssss the dog

than i need an script that outputs the words that are in both files so the output would be:

the
brown
fox
dog

can someone help?

greets, ryan

Something like this:

```
$ tr ' ' '\n' <file1 | sort -u >tmp1
$ tr ' ' '\n' <file2 | sort -u >tmp2
$ comm -12 tmp1 tmp2
brown
dog
fox
the

```

---

### Post by McNils on 2011-11-28
1. Create 2 files sorted with all words in them. I made them unique as well.
2. take the intersection of the to files,use comm

```
awk '{n=split($0,a);for(j=1;j<=n;j++) {printf("%s\n",a[j])}}' file1.txt |sort -u > a
awk '{n=split($0,a);for(j=1;j<=n;j++) {printf("%s\n",a[j])}}' file2.txt |sort -u > b
comm -12 a b
rm a b

```

edit. i knew there was a more clever way to transform the files...

---

### Post by Bodsda on 2011-11-29
Python solution, a few more lines, but far more readable imho

```

list1 = open("C:\\file.txt", "r").read().replace("\n", " ").split()
list2 = open("C:\\file2.txt", "r").read().replace("\n", " ").split()
unique = []

for word in list1:
    if word in list2 and word not in unique:
        unique.append(word)
        print word

```

---

### Post by San_SS! on 2011-11-29
I would do it in python but using sets:
```

set1 = set(open("file1.txt", "r").read().replace("\n", " ").split())
set2 = set(open("file2.txt", "r").read().replace("\n", " ").split())

for word in (set1 & set2): #This returns the intersection
    print word


```

---

### Post by stylishpants on 2011-11-29
How do it as a one-liner:

```

bob@cob:/tmp$ join <(perl -pe 's/\s+/\n/g' file1 | sort -u) <(perl -pe 's/\s+/\n/g' file2 | sort -u)
brown
dog
fox
the

```

---

### Post by ryanrio95 on 2011-11-29
thanks for all replies.
i will try all solutions tommorow.

greets. ryan

---

### Post by ryanrio95 on 2011-11-30
> **stylishpants said:**
> how do it as a one-liner:

```

bob@cob:/tmp$ join <(perl -pe 's/\s+/\n/g' file1 | sort -u) <(perl -pe 's/\s+/\n/g' file2 | sort -u)
brown
dog
fox
the

```

this one is working well :)

---

