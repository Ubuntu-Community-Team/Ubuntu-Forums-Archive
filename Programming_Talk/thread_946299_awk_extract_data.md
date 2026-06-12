---
title: "awk extract data"
date: 2008-10-13
forum: Programming Talk
---

### Post by abraxas334 on 2008-10-13
Hello,
I would like to get data out of say 100 files names like test1.dat test2.dat etc and put them into a single file.
I know i can do it with one using awk in the following way, when i say want to get the 2nd column of the file

```
awk 'BEGIN{FS="\t"; OFS="\t"} {print $2}'test1.dat >output.dat
```

how can i use a wildcard so all 100 files will be done automatically, so i won't have to change the input file name for every single one of them.
I tried 

```
 awk 'BEGIN{FS="\t"; OFS="\t"} {print $2}'test*.dat >output.dat
```
but that didn't work.
What kind of wildcards has awk got?

---

### Post by WW on 2008-10-13
Your example should work if you put a space after the closing single quote:
```

awk 'BEGIN{FS="\t"; OFS="\t"} {print $2}' test*.dat >output.dat

```

---

### Post by abraxas334 on 2008-10-13
Lol indeed it does! Silly spaces! Thanks alot

---

### Post by abraxas334 on 2008-12-08
if I have this code to extract certain columns out of a file for the command line,

[PHP]awk 'BEGIN{FS="\t"; OFS="\t"} {print $2}' test*.dat >output.dat[/PHP] 

how can i make it run from a file i.e. something along the lines

```
 awk -f file.awk < test*.dat 
```

this is exactly what i have tried but I get an error saying amigious redirect.
I have 100 files of test1.dat ->test100.dat and i want to extract certain columns out of each of it and then add it to a common output file and i really would like to avoid having to type the long command every time or pressing the up arrow for ages till i can find the command again.
Thanks

---

### Post by ghostdog74 on 2008-12-08
> **abraxas334 said:**
>  

how can i make it run from a file i.e. something along the lines

```
 awk -f file.awk < test*.dat 
```


```

awk -f file.awk test*.dat

```

---

