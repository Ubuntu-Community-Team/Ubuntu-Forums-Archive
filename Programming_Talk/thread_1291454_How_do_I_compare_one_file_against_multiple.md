---
title: "How do I compare one file against multiple?"
date: 2009-10-14
forum: Programming Talk
---

### Post by SNYP40A1 on 2009-10-14
I have one text file that I want to compare against 60-100 others.  I want to know which file out of those 60 others is most similar (fewest line-by-line differences).  Anyone know an efficient way to do this?  In fact, I think it can be done in one command line using diff, but not sure how to feed the output of ls *.pat into diff as one of the arguments.

---

### Post by stylishpants on 2009-10-14
Rough, and untested, but maybe something like this:
```

l=/tmp/lines.txt
for f in *.pat; do diff file.pat $f > $l; n=`wc -l $l`; echo "$n $f"; done | sort -n
```

---

