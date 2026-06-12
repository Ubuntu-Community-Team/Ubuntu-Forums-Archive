---
title: "getting data from a file where you only know a partial match and dont want the full l"
date: 2013-07-31
forum: Programming Talk
---

### Post by cbillson on 2013-07-31
lets say i have a file that has:
[INDENT]
name=123 data=blah
name=124 data=blah
name=125 data=blah
name=126 data=blah
name=127 data=blah[/INDENT]

i need to get "123" into a variable, so i could use a for loop and grep (cat myfile | grep "name=", but is there any way i can grep or only select the data up to the next space?

Also, when using arrays, if you split a line of data up into data[1] data[2] etc, and you have lets say up to data[30] is there any way to easily echo data[20] to data[30] without the obvious specifying every element - kind of like data[20]+

Cheers
Chris

---

### Post by zazzle on 2013-07-31
it's can be solved by writing a simple C program, use fgets() read lines from the data file and sscanf() get a variable equal to 123 and print this line with the first 8 bytes.

---

### Post by codemaniac on 2013-07-31
there is a split function in awk which splits an string into an array using a delimiter. 

```
awk  '{split($1,a,"="); var[$1] = a[2]} END{for (i in var) {print var[i]} }' sample.dat
```

---

