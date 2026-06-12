---
title: "python strings"
date: 2006-12-08
forum: Programming Talk
---

### Post by Ubuntuud on 2006-12-08
Hi,
I'm creating a program that can help me learn my Greek words.
But I need to divide a string in two parts.

To make it more clear, I have this string:
```
"koeien = cows"
```
And I want to divide it in:
```
"koeien"
and
"cows"
```

What is the easiest way to do this?
The only way I can think of is making a list from the string. Indexing the location of the "=". And then doing something like:

```
part1 = list[:indexed_location-1]
part2 = list[indexed_location+2:]
```

There must be an easier way...
Thanks in advance!

---

### Post by &lt;mawe&gt; on 2006-12-08
Hi!

Well, I think the easiest way would be to use *split()*:
```
In [1]: s = "koeien = cows"

In [2]: s.split("=")
Out[2]: ['koeien ', ' cows']
```
Regards, mawe

---

### Post by christhemonkey on 2006-12-08
An then if you need to remove any white space before or after you could do something like:
```
s = "koeien = cows"
news = s.split("=")
news1 = news[0]
news2 = news[1]
news1 = news1.rstrip()
news2 = news2.strip()
```

Not the most elegant code i've ever written...

---

### Post by &lt;mawe&gt; on 2006-12-08
Ah, the whitespace, sorry, I forgot about that ;)
```
s.split(" = ")
```
or (that's how I would do it)
```
[elem.strip() for elem in s.split("=")]
```

Regards, mawe

---

### Post by Ubuntuud on 2006-12-08
OK. Thanks a lot!

---

