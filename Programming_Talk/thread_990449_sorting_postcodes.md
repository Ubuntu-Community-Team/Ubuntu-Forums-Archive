---
title: "sorting postcodes"
date: 2008-11-22
forum: Programming Talk
---

### Post by dunryc on 2008-11-22
Hi 

I have a file with uk postcodes what i would like to do is shorten each line of the file to just 3 characters then sort the file into just unique lines. I have an idea that i can use uniq to sort only unique lines but no idea how to get just the first three characters of each line into one file. the file i have is as below only much larger 

> 
SG11 
SG12 
SG13 
SG14 
SG15 
SG16 
SG17 
SG18 
SG19 
SG2 

any help would be greatly appreciated

---

### Post by WW on 2008-11-22
Try this:
```

cut -b 1-3 file.dat | sort | uniq

```
where file.dat is the file containing the codes.

---

### Post by dunryc on 2008-11-22
> **WW said:**
> Try this:
```

cut -b 1-3 file.dat | sort | uniq

```
where file.dat is the file containing the codes.

THanks WW worked a treat :-)

---

