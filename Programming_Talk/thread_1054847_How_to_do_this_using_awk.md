---
title: "How to do this using awk"
date: 2009-01-30
forum: Programming Talk
---

### Post by minwei86 on 2009-01-30
1 IT 50
2 IT 40
3 Finance 200
4 MP 30
5 MP 10
6 HQ 30

how to use awk to do it that i can get the total of specified department  and display it like this

IT 90
MP 40
HQ 30
Finance 200

---

### Post by geirha on 2009-01-30
Use [Arrays](http://www.gnu.org/software/gawk/manual/gawk.html#Arrays)
```
awk '{ A[$2] += $3 } END {for (i in A) print i" "A[i]}' < input.txt
```

---

### Post by minwei86 on 2009-01-30
got any other way other that array cause i haven reali touch on array yet

---

### Post by myrtle1908 on 2009-01-30
Using associative array such as *geirha* has demonstrated is really the best way.  It really isn't that complex.  What bit is confusing you?

---

### Post by myrtle1908 on 2009-01-30
This *may* help to explain ...

By design, awk splits line input on space and the "pieces" are available as $1..$NF (where $NF is the number of columns or "pieces").

What is happening in the solution provided is:-

1. { A[$2] += $3 }

For each line in the input file, store the second column ($2) which is a string (in your case IT, MP etc) in the array named A and += its value with that of the third column ($3 ie. 50, 40, 200 etc).

2. {for (i in A) print i" "A[i]}

Now loop through the array named A and print the key (ie. IT, MP etc) followed by a space and then the value of the key eg. for IT the value is 90.

Hope that helps a little.

---

