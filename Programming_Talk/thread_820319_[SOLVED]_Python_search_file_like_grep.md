---
title: "[SOLVED] Python: search file like grep"
date: 2008-06-06
forum: Programming Talk
---

### Post by dbbolton on 2008-06-06
I want to do something like grep with python. I have a file, and I want to search it for a string, and print the line containing that string. Is this possible, and if so, how can I do it?

---

### Post by ghostdog74 on 2008-06-06
> **dbbolton said:**
> I want to do something like grep with python. I have a file, and I want to search it for a string, and print the line containing that string. Is this possible, and if so, how can I do it?

```

for line in open("file"):
 if "search_string" in line:
   print line

```
always read up the documentation and tutorials if you don't know anything.

---

### Post by dbbolton on 2008-06-06
> **ghostdog74 said:**
> ```

for line in open("file"):
 if "search_string" in line:
   print line

```
always read up the documentation and tutorials if you don't know anything.
Thanks. I have been reading the docs and a few tutorials, but I got stuck on this one.

Also, do you know whether it's possible to print only the first occurrence of the search string?

---

### Post by WW on 2008-06-06
> **dbbolton said:**
> 
Also, do you know whether it's possible to print only the first occurrence of the search string?
Just put a **break** statement after the print statement.

---

### Post by dbbolton on 2008-06-06
Thanks :)

---

### Post by helpdeskdan on 2008-11-05
Another thanks!

---

### Post by jdb91 on 2010-10-07
So I'm doing 

```
for line in open("text.txt"):
 if "ref" in line:
  print line

```

And getting back

```
ref= 1
```

(For example)

All I want displayed is the "1"

How do I format the output of print line to print just the second part (in bash it would be awk {print $2})

---

### Post by ghostdog74 on 2010-10-08
you just need to split .
```

print line.split("=")[-1]

```

i thought you have been reading the docs? split() is very basic for Python string processing.

---

