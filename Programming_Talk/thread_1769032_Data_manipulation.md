---
title: "Data manipulation"
date: 2011-05-27
forum: Programming Talk
---

### Post by abraxas334 on 2011-05-27
I have a file that looks like this:


0.05 11 R cvpvvvvi 0.142857 0.26452 7 1266
0.05 12 A vlpvvvvi 0.60375 0.0345858 800 (7.42875 nan 807) 1925 0.000359901 57
0.05 13 R vlivvvvi 0.5375 0.0557443 320 1925
0.05 14 R vppvvvvi 0.4 0.195959 25 1925

All I want to do is print the 4th column to a file but only if the third one has an A in it and not an R.
What is the best way of doing this?

Thanks for any help!

---

### Post by Arndt on 2011-05-27
> **abraxas334 said:**
> I have a file that looks like this:


0.05 11 R cvpvvvvi 0.142857 0.26452 7 1266
0.05 12 A vlpvvvvi 0.60375 0.0345858 800 (7.42875 nan 807) 1925 0.000359901 57
0.05 13 R vlivvvvi 0.5375 0.0557443 320 1925
0.05 14 R vppvvvvi 0.4 0.195959 25 1925

All I want to do is print the 4th column to a file but only if the third one has an A in it and not an R.
What is the best way of doing this?

Thanks for any help!

```
awk '{if ($3 == "A") print $4;}'
```

---

### Post by Barrucadu on 2011-05-27
Assuming the third column is only one character:

```
awk '{ if ($3 == "A") print $4 }' datafile
```

---

