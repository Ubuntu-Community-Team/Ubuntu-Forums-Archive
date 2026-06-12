---
title: "Having trouble with sort/unique in the shell"
date: 2011-05-01
forum: Programming Talk
---

### Post by MountainX on 2011-05-01
I have a large comma separated values (spreadsheet/text) file I need to sort. I want to keep only the unique lines.

Here's an example of two lines. I want to sort first in ascending date/time order (col 2 and/or 3), then by the column of Left/Right values (the 8th col).

Here's an example of the data
```

deleted

```The sorted file is larger than the original, which shouldn't be the case, right? The sorted file shows many unique lines. I'm not sure if they are in the original, but I don't think so. 

When I try to sort and keep only unique lines I end up with just a single line. (In reality there are thousands of unique lines. I can tell that by simple inspection.)

I'm just using sort and uniq in the shell attempting to follow the options listed in the man page. I appreciate any tips.

EDIT: maybe my lines are too long? When I try sort -u with test data, it seems to work...

EDIT 2: yes, apparently lines were too long (or maybe there was some trailing whitespace I missed). Using uniq -w N (with a sufficiently large N) resolved the problem.

---

