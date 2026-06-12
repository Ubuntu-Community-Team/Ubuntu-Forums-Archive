---
title: "What is the correct (or safest) way to group commands in sed?"
date: 2013-11-06
forum: Programming Talk
---

### Post by vasa1 on 2013-11-06
I have a small file, my.txt:
```
01 this is the first line
02 this is the second line
03 this is the third line
04 this is the fourth line

```
All these give the desired result:
```

sed 's/this/that/g;s/line/verse/g' my.txt
sed '{s/this/that/g;s/line/verse/g}' my.txt
sed -e s/this/that/g -e s/line/verse/g my.txt

```
But which one is the recommended way? Or is there something better?

---

### Post by Vaphell on 2013-11-06
i never use -e, it makes the command longer than it needs to be. Other than that in this case all 3 are equivalent and i suspect they all do the more or less the same thing internally.
{} are necessary only if you want to group commands together under specific condition, eg /pattern/{p;s/X/Y/g;p;q;} which looks a lot like how awk works with its condition/command block pairs

---

