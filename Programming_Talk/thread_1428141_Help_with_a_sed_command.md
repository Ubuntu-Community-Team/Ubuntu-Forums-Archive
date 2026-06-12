---
title: "Help with a sed command"
date: 2010-03-12
forum: Programming Talk
---

### Post by jamefarm on 2010-03-12
Hello, I have a text file that is tab delimited with 6 fields, what I need to do is replace the final field.  Here's a sample of the text file:

```

NAVI	Navisite	-0.08	-0.08	-0.09	11-Mar
NEN	New England Realty	null	null	null	11-Mar AMC
NPSP	NPS Pharmaceuticals	-0.13	-0.14	-0.18	11-Mar 4:30 PM

```

I need to replace the date field with a variable, but lets just use 2010-03-11 for now.  The beginning of the field will begin with either 1 or 2 numbers followed by a dash etc... e.g. 9-Mar, or 11-Mar AMC

Here's what I tried, though it didn't work.
```

sed 's/[0-9]+(?=-.)/2010-03-11/g'

```

---

### Post by PmDematagoda on 2010-03-12
This seems to work:-
```
sed 's/[0-9]*-[A-Z][a-z][a-z]/11-03-2010/'
```

---

### Post by jamefarm on 2010-03-12
Just about, but I need it to remove anything after that as well, such as the AMC or the time so that the last field is only '2010-03-11'

---

### Post by PmDematagoda on 2010-03-12
Then this may do the trick:-
```
sed 's/[0-9][0-9]*-[A-Z a-z 0-9 :]*/11-03-2010/'
```

Edit:- Whoops, didn't see that the time was also there at times.

---

### Post by jamefarm on 2010-03-12
Works like a charm!  Thanks a bunch PmDematagoda!

---

### Post by DaithiF on 2010-03-12
another couple of variations:
```
~/tmp$ sed 's/[^\t]*$/11-03-2010/' testfile
NAVI    Navisite        -0.08   -0.08   -0.09   11-03-2010
NEN     New England Realty      null    null    null    11-03-2010
NPSP    NPS Pharmaceuticals     -0.13   -0.14   -0.18   11-03-2010
~/tmp$ cut -f1-5 testfile | sed 's/$/\t11-03-010/'
NAVI    Navisite        -0.08   -0.08   -0.09   11-03-010
NEN     New England Realty      null    null    null    11-03-010
NPSP    NPS Pharmaceuticals     -0.13   -0.14   -0.18   11-03-010

```

---

