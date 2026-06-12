---
title: "[script/CLI]Arbitrary reordering of lines"
date: 2008-06-14
forum: Programming Talk
---

### Post by tehet on 2008-06-14
Is there a way to reorder lines in a non-logical way? For example, change
```
line1
line2
line3
```
to
```
line2
line1
line3
```
AFAICT sort only supports logical reordering (alphabetical, numerical etc.).


I've got many files looking like this:
```
entry1
in 20 out 1111

entry2
in 7098 out 2222

entry3
in 98765 out 3333
```
that I need to process like this (or in any other way that results in a comma seperated list of $2 and $4)
```
awk '/in/{print $2,",", $4}' foo
```
The output
```
20 , 1111
7098 , 2222
98765 , 3333
```
needs to be
```
7098 , 2222
20 , 1111
98765 , 3333
```

Any help or hints would be much appreciated.

---

### Post by ghostdog74 on 2008-06-14
```

awk '!/^$/ && /in/{
 array[$2]=$4
}END{
 for (i in array) print i, array[i]
}
' file

```

---

### Post by tehet on 2008-06-14
ghostdog, thanks for your reply. Is that a random ordering? I can't figure out how it is reorder.

I have found a working solution though it's not very pretty:
```
#!/bin/bash
awk '/in/{print $2,",", $4}' input > temp
sed -n '2p' temp > output
sed -n '1p' temp >> output
sed -n '3p' temp >> output
```

---

### Post by ghostdog74 on 2008-06-14
> **tehet said:**
> ghostdog, thanks for your reply. Is that a random ordering? I can't figure out how it is reorder.

first, you should try it out and see what happens. Second, yes, the for loop used this way is not in order. 

> 
I have found a working solution though it's not very pretty:
```
#!/bin/bash
awk '/in/{print $2,",", $4}' input > temp
sed -n '2p' temp > output
sed -n '1p' temp >> output
sed -n '3p' temp >> output
```
yes indeed. awk itself can do the jobs of most common unix tools like cut/sed/grep/wc etc combined. therefore, you don't need to use sed.

---

### Post by tehet on 2008-06-14
> **ghostdog74 said:**
> first, you should try it out and see what happens.
I did try it offcourse. So I'll need to change the bit after END to my sorting (I think).

Thanks for your help.

---

### Post by Trumpen on 2008-06-14
You have just to modify the code ghostdog74 posted before:
```
awk '/^in/{ array[++count]=$2", "$4} END {print array[2];print array[1];print array[3]}'
```

---

