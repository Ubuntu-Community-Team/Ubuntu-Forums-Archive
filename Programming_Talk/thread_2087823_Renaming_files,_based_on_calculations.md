---
title: "Renaming files, based on calculations"
date: 2012-11-24
forum: Programming Talk
---

### Post by Grenage on 2012-11-24
Greetings!

I'm often renaming directories of files using a loop, and sed - as I'm sure many of us do; what I want to do now is rename files while performing basic subtraction on the numerals at a location in the file name.

```
files19.subfile9.2323.txt
files19.subfile9.2324.txt
files19.subfile9.2325.txt
```

I would like to subtract 49 from each file (there are *thousands*), so that the names are:

```
files19.subfile9.2274.txt
files19.subfile9.2275.txt
files19.subfile9.2276.txt
```

I've been trying various things, and it was getting more convoluted by the minute.

Could anyone suggest an elegant way to go about this?

---

### Post by papibe on 2012-11-24
Hi Grenage.

I would use parameter substitution instead of 'sed'.

For instance:
```
$ file="files19.subfile9.2325.txt"
$ bname=${file%.txt}
$ echo $bname
files19.subfile9.2325

$ number=${bname##*.}
$ echo $number
2325

$ newnumber=$(($number-49))
$ echo $newnumber
2276

$ newfile=${bname%.*}."$newnumber".txt
$ echo $newfile
files19.subfile9.2276.txt
```
Hope it helps.
Regards.

---

### Post by Grenage on 2012-11-24
Perfect, that's a good way of getting it done; thanks a lot. :)

---

