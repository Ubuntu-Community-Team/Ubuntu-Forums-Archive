---
title: "Tranpose data file?"
date: 2007-02-06
forum: Programming Talk
---

### Post by rich.bradshaw on 2007-02-06
Hi,

I have a program that unavoidably outputs data in rows as so:

time 1 2 3 4 5 .... 5999 6000
data1 1 5 10 20 30 ... 99 100
data2 1 7 11 25 35 ... 99 100
data3 ....
.
.
.

I want to be able to analyse this in excel, so need someway of tranposing the file, preferably that is usable in a shell script.

Does anyone know of anyway to achieve this? I have looked at awk, sed etc, but have no idea how to understand how to do it!

Thanks,

Rich

---

### Post by kidders on 2007-02-06
Hi there,

Forgive the stupid question, but what do you mean when you say you want to transpose it?

Technically, it seems like you should be able to import your file into Excel pretty easily ... it looks as though your values are all space delimited, and your rows are separated by line feeds. For a bit more reliability, you might like to transform it into a CSV-style file though (ie comma or maybe tab delimited fields), and convert all the line feeds into those silly Microsoft CRLFs.

---

### Post by Ramses de Norre on 2007-02-06
Hmm it shouldn't be too hard in java or c, just read the file in an array and output the array with the indices switched, but I'm not sure how to go about this in a shell script (which hasn't got arrays as far as I know).

---

### Post by lnostdal on 2007-02-06
Excel should be able to read CSV-format. If this program outputs a format like this, it should be no problem to import directly. If it outputs a format similar it should be no problem running the data through some script that does some changes to the format so it is suitable for Excel/Calc.

[http://en.wikipedia.org/wiki/Comma-separated_values](http://en.wikipedia.org/wiki/Comma-separated_values)

If you could provide a more accurate sample/description (edit: preferably the output from your program piped to a file or something) I can create a script for you that transform the data to a format both Excel and Calc will be able to import.

---

### Post by duff on 2007-02-06
```
# cat transpose.sh 
#!/bin/bash

for i in $(seq $2);
do
   cat $1 | awk "{print \$${i}}" | tr '\n' '\t'
   echo
done

# cat input 
time 1 2 3 4 5  5999 6000
data1 1 5 10 20 30  99 100
data2 1 7 11 25 35  99 100

# ./transpose.sh input 8
time    data1   data2
1       1       1
2       5       7
3       10      11
4       20      25
5       30      35
5999    99      99
6000    100     100

```

---

### Post by rich.bradshaw on 2007-02-06
Thanks very much... I know excel can transpose, but not if the file has too many columns.

Thanks for that script, it's awesome!

---

