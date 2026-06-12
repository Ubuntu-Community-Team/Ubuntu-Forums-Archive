---
title: "efficiency and scripting"
date: 2010-06-03
forum: Programming Talk
---

### Post by ja660k on 2010-06-03
Hey all, 
hmmm just a little question...
i have a script that reads a csv file, extracts a certain part.

then checks if that part is in a directory or subdirectory of that directory... and copies the file into another directory.

one way:
storing output of `find dir/` and checking that output against the list of ids from csv... 
so, this way its looping output^id_list times.
when i run `time test.pl` i get...

0.18u 0.14s 0:01.43 22.3%


other way, 
as i loop to get the id from csv
i store `find dir/ | grep $id` this way it only loops once, but it executes find every time id appears in the file.
but i run `time test1.pl` i get ...

0.06u 0.21s 0:03.04 8.8%

So which one is more efficient, BTW im not just going on exec time.
because i know test1 was 14s and 2 21sec

---

### Post by trent.josephsen on 2010-06-03
> **ja660k said:**
> So which one is more efficient, BTW im not just going on exec time.
because i know test1 was 14s and 2 21sec

Okay, so how would you define "efficiency"?  If the one that finishes sooner is not necessarily more efficient, then how would you determine which is more efficient?

By the way, piping find into grep is never necessary.  Use one of

```

find dir/ -name "$id"   # finds files with the exact name $id
find dir/ -name "*$id*" # finds files with $id in their name

```

You'll also avoid grabbing a whole bunch of files if one of your subdirectories has $id in its name.

---

