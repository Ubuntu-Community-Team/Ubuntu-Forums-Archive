---
title: "different columns, same row, from different files, into a single file with AWK"
date: 2011-03-18
forum: Programming Talk
---

### Post by hailholyghost on 2011-03-18
:guitar:Hey all,

I've got a file like so:

$head -3 distances
C2H1p-C1H2p
C2H1p-C2H2p
C2H1p-C2H3p

and another file:

$head -3 ptraj.notyet
distance 2 :2@H1' :1@H2'1 out time 0.1
distance 3 :2@H1' :2@H2'1 out time 0.1
distance 4 :2@H1' :2@H3' out time 0.1

I wish to use awk to combine the 2 files so it will read:

distance 2 :2@H1' :1@H2'1 out C2H1p-C1H2p time 0.1
distance 3 :2@H1' :2@H2'1 out C2H1p-C2H2p time 0.1
distance 4 :2@H1' :2@H3' out C2H1p-C2H3p time 0.1

and so on.

I've tried this, and this should work:

head -1 ptraj.notyet | tail -1 | awk '{print $1, $2, $3, $4, $5, system("head -1 distances | tail -1"), $6, $7}'

but unfortunately this puts them out in 2 different lines:

C2H1p-C1H2p
distance 2 :2@H1' :1@H2'1 out 0 time 0.1

I will have to make a BASH loop to do this for all 35 lines.

What am I doing incorrectly?  Is there a better way to do this without a loop?:confused:

thanks for your time,):P
-Dave

---

### Post by sisco311 on 2011-03-18
You can use paste to merge the files and awk to switch the columns:
```
paste ptraj.notyet distance | awk '{print $1, $2, $3, $4, $5, $8, $6, $7}'
```

---

### Post by hailholyghost on 2011-03-18
Thanks so much sisco311!  It worked beautifully!

---

### Post by sisco311 on 2011-03-18
You're welcome!

---

