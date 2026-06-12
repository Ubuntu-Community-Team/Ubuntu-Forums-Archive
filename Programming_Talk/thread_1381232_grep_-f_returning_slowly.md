---
title: "grep -f returning slowly"
date: 2010-01-14
forum: Programming Talk
---

### Post by mbeach on 2010-01-14
I have two files

partnums.txt
catalog.txt

partnums.txt has a list of unique part numbers, one per line. 
catalog.txt is a list of properties from a vendor catalog and will include items not in in partnums.txt. 

partnums.txt will contain parts not in catalog.txt. 
catalog.txt is fixed width with the partnum in cols 66 to 73. 
catalog.txt has one item per line as well.

I'm trying to extract all the lines in catalog.txt for which a part number exists in partnums.txt.

partnums.txt contains somewhere around 9000 lines or so, catalog.txt contains around 12000 lines

I'm using 
```

grep -f partnums.txt catalog.txt

```
which is working, however, at a deadly slow pace. I'm used to grep returning so quickly (much simpler usage) that I have to check that it worked as desired - this is the first time I've used it with a file (-f) instead of the pattern. Is there a better bash tool for this other than grep? Open to perl, just not all that familiar with it.

---

### Post by Trumpen on 2010-01-14
Perhaps it's faster with awk:

[PHP]awk 'FNR==NR{a[$1];next} {num=substr($0,66,73-66+1); if (num in a) print;} ' partnums.txt catalog.txt[/PHP]

---

### Post by Hellkeepa on 2010-01-14
HELLo!

Actually, I think I'd recommend you to use a database for this. This is what they're made for, and nothing beats them on searching through lots of records quickly doing comparisons. Just make sure you set up an index on the partsnum columns, and you're set.
```
SELECT p.* FROM partsnum n INNER JOIN parts p ON p.partsnum = n.partsnum
```

Happy syncin'!

---

### Post by mbeach on 2010-01-14
hey hellkeepa, I agree, a db could handle this type of task nicely, but its going to be part of a script with some files being pulled in from legacy systems as part of a nightly cron job, the resulting list is then pushed off to another server for insert into a db.

giving the awk route a try now.

---

### Post by diesch on 2010-01-14
Maybe it's faster if you create one regex from all the part numbers, i.e. instead of
```
1
2
3
4
5

```
you use
```
1|2|3|4|5
```

If not sure if this works well with that much numbers.

---

### Post by mbeach on 2010-01-15
> **diesch said:**
> Maybe it's faster if you create one regex from all the part numbers, i.e. instead of
```
1
2
3
4
5

```
you use
```
1|2|3|4|5
```

If not sure if this works well with that much numbers.

Yes, I see where you are going, but same as you, my gut feeling is with that many patterns, do things work correctly.

Anyway, have been trying with awk, however the array doesn't seem to be getting populated correctly. If I try to print a[knownitem], nothing prints (even if the array is a[$1] = "foo").

Might just throw it all in a python script - was trying to avoid but it is what I know.

---

### Post by Hellkeepa on 2010-01-15
HELLo!

For speed, I think I'd go for Perl. Perhaps also set up groupd of 10-20 patterns, to speed things up a bit. Play around, and see if you can't find that sweet spot. ;-)

Happy codin'!

---

### Post by Trumpen on 2010-01-15
@mbeach

Could you post here a couple of lines of your input files (especially of partnums.txt)?

---

### Post by merilius on 2010-01-21
Sure, databases, what else???
mbeach: try changing grep
```
grep -f partnums.txt catalog.txt
```to fgrep
```
fgrep -f partnums.txt catalog.txt
```Should be orders of magnitude faster. I guess fgrep is building one finite-state automaton and scanning text once and grep uses each fixed string at a time.

---

### Post by greg3124 on 2011-11-10
I just had the same issue, and solved it via a quick python script. The script reads 15.000 patterns in a hashtree and filters a 2.000.000  lines file in a fraction of a second, because I know where the pattern is in the line.
Usage: cat file_to_filter | python my_script.py patterns.txt

```
import sys

patterns=set()
f_patterns=open(sys.argv[1])
for line in f_patterns:
        patterns.add(line[:-1])

for line in sys.stdin:
        key=line[1:10]   # This you certainly need to change!
        if key in patterns:
                print line,
```

---

