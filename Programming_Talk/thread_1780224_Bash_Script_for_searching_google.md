---
title: "Bash Script for searching google"
date: 2011-06-11
forum: Programming Talk
---

### Post by conradin on 2011-06-11
Hi all,
i have a bash script which works almost as i would hope.
the function is to read a file (Chemical names) line by line,
and open a firefox tab & do a google search using the Im feeling lucky parameter. This Script is to get the MSDS for each chemical.
Ah, so it went ok until I had a space in the line. Ethanol, Hexane, water..
all single line stuff works fine. But Oxalic acid would search generate 2 incorrect searches. So I know my while loop is screwy. But, I'm not sure how to fix it. Its a pretty simple script, can some one please help?

```

#!/bin/bash 
x="http://www.google.com/search?q="  
L="&btnI=Im+Feeling+Lucky"
y="&as_filetype=pdf"
z=0
while read line
do z=$(($z+1));
firefox $x$line$y$L;
#sleep so google doesn't baulk about suspicious traffic
sleep 3
done < "NeededMSDS.txt"

```


The fix I came up with was to insert "%20" into every place there was a space in the Chemical Names list. Preferably however, I would like to not alter my data set.

---

### Post by Toz on 2011-06-11
In place of:> firefox $x$line$y$L;
Try:```
firefox $x`echo "$line" | sed -e 's/ /\%20/g'`$y$L
```

---

### Post by BkkBonanza on 2011-06-11
Use parameter substitution in bash.

Replace 

firefox $x$line$y$L;

with

firefox $x${line// /%20}$y$L;

This takes $line but replaces " " with "%20". The extra "/" in the pattern makes it do all occurences not just the first.

---

### Post by conradin on 2011-06-11
XD BkkBonanza !!! Aw sweet! its working perfect now! Thank You SOO much!! :D

> **BkkBonanza said:**
> Use parameter substitution in bash.

Replace 

firefox $x$line$y$L;

with

firefox $x${line// /%20}$y$L;

This takes $line but replaces " " with "%20". The extra "/" in the pattern makes it do all occurences not just the first.

---

