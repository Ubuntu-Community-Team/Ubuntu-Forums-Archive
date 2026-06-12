---
title: "'comm' command not finding match"
date: 2009-05-06
forum: Programming Talk
---

### Post by prem1er on 2009-05-06
I'm running a bash script and using the 'comm' command to compare two sorted files.  I have the matching results being written to another file.  After realizing that I had no matching data in the files I went back to the DB and added a number that now appears in both queries.  I turned off the '-12' option for comm so it no longer suppresses any output.  The file now shows the matching number (0680430620103)in column 1 and 2 (which means that it is not a match).  Why is this?

Usage:
```
comm ${_sortDataArray[$_index]} $_db2_sorted >> ${_matchArray[$_index]}
```

Output:
```
        
        063053107965
        066128501
0680430620100
0680430620101
0680430620102
0680430620103
        0680430620103
        069211426
        069292507
        069292515
        077360931

```

---

### Post by prem1er on 2009-05-06
Sort of solved....seems something else in my code is adding white space after the number.  It is either caused by my DB2 query or from sorting.  I will report back.

---

### Post by prem1er on 2009-05-06
My db2 query is returning the results that are equal in length longest result.  This means that white space is added to each result that is less than the size of the longest result.  I have no idea why this is happening.  For now I am just going to use 'sed' to remove the white space.  Any other suggestions are welcomed.

---

