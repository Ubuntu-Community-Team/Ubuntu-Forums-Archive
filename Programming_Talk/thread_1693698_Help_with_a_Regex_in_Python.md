---
title: "Help with a Regex in Python"
date: 2011-02-23
forum: Programming Talk
---

### Post by blazemore on 2011-02-23
Hello everyone. I'm a bit (read very) stuck on working "with" regular expressions on Python.

I pretty much get the regular expression syntax, but I think python handles backslashes in a very specific way.

Anyway I'm trying to do something awk-like:

Given a string like "/lhome/rxh09u/gp10-srb/src/stories/business-11821028.xml"

how can I extract just the word "business" from this, and get it into another string?
Obviously the word won't always be "business", and the absolute path name up to "/stories" could be different.
Furthermore the word to extract often includes a hyphen, in the case of "uk-wales" for example.

So basically if I gave it this string:
"stories/world-us-canada-11836156.xml" it would need to get "world-us-canada" into a string.

it always ends in 8 numbers followed by .xml if that helps.

---

### Post by blazemore on 2011-02-23
OK I used ```
filename = self._filename[0:-13]
```to make it so the bit I want to match is at the end of the string ("/lhome/rxh09u/gp10-srb/src/stories/business"), but I'm still having problems
1. How to cope with the fact that there could be hyphens in there?
2. All I can do is get Python to say "yep, that matched", where I want it to extract the relevant bit?

---

### Post by MadCow108 on 2011-02-23
will that do?
```
re.search(".*/(stories/.+)-[0-9]{8}\.xml$", s).group(1)
```

---

### Post by kurum! on 2011-02-23
Just do a couple of splits and join. in Ruby

```

>> s="/lhome/rxh09u/gp10-srb/src/stories/world-us-canada-11836156.xml"
=> "/lhome/rxh09u/gp10-srb/src/stories/world-us-canada-11836156.xml"
>> s.split("/")[-1].split("-")[0..-2].join("-")
=> "world-us-canada"

```

you can do the same in Python, since they are quite similar.

---

### Post by nvteighen on 2011-02-23
My version:

```

re.search(".*?(stories/.+?)-[0-9]*?\.xml$", string)

```

Why? Because this would allow searching in a relative path too. Also, it allows the number to be arbitrarily long.

---

### Post by LemursDontExist on 2011-02-23
I would be inclined to use os.path and string operations instead of a regex here.
```
import os

s="/lhome/rxh09u/gp10-srb/src/stories/world-us-canada-11836156.xml"
os.path.basename(s)[:-13]
```
is pretty straight forwards, and should correctly with any filename weirdness you can imagine.

If the length of the ending were variable, something like kurum's ruby solution could be done in python:

```
import os

s="/lhome/rxh09u/gp10-srb/src/stories/world-us-canada-11836156.xml"
'-'.join(os.path.basename(s).split('-')[:-1])
```

If you want to avoid importing os:

```
s="/lhome/rxh09u/gp10-srb/src/stories/world-us-canada-11836156.xml"
'-'.join(s.split("/")[-1].split('-')[:-1])
```

All in all, regexes are serious overkill for this problem.

---

### Post by Vaphell on 2011-02-23
maybe, but for some it's easier to pay the performance price with regexes they are intimately familiar with than to bother with string slicing-n-dicing and list magic.

---

### Post by blazemore on 2011-02-25
> **Vaphell said:**
> maybe, but for some it's easier to pay the performance price with regexes they are intimately familiar with than to bother with string slicing-n-dicing and list magic.

Performance is important here.

---

