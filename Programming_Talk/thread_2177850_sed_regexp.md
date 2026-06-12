---
title: "sed regexp"
date: 2013-09-30
forum: Programming Talk
---

### Post by IlPazzo on 2013-09-30
Hi folks,

Can anyone suggest a SED command line to replace the occurrences of something like:

    ALIGNED ( type data[size], 16 );
    ALIGNED ( type data, 16 );

into something like

   type data[size] ALIGNED(16);
   type data ALIGNED(16);

Thanks

---

### Post by ofnuts on 2013-09-30
```

sed -r -e 's/ALIGNED \( ([A-Za-z_0-9]+) ([A-Za-z_0-9]+)\[([0-9]+)\], 16 \);/\1 \2[\3] ALIGNED(16);/' -e 's/ALIGNED \( ([A-Za-z_0-9]+) ([A-Za-z_0-9]+), 16 \);/\1 \2 ALIGNED(16);/'

```

---

### Post by Vaphell on 2013-10-01
given that one possibility is pretty much a subset of the other it's easy to achieve proper effect with a single expression utilizing **?** quantifier for the optional part

```
$ test=$'ALIGNED ( type data[size], 16 );\nALIGNED ( type data, 16 );'
$ echo "$test" | sed -r 's/(ALIGNED)\s*[(]\s*(\w+)\s+(\w+**(\[\w+\])?**)\s*,\s*([0-9]+)\s*[)]\s*;/\2 \3 \1(\5);/'
type data[size] ALIGNED(16);
type data ALIGNED(16);
```

---

