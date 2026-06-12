---
title: "shell scripting month extraction"
date: 2013-10-05
forum: Programming Talk
---

### Post by aadil7 on 2013-10-05
hi everyone

I want to manipulate a file (copy it to another location) and change the name to have the month created on the end.

the month can be seen from ls -l and i want the file to be like:
file
copy and change name to
file_oct

is this a possibility?
I tried scouring the net for a good hour with no luck of any command which will allow me to seperate and select the month save it as a variable and then attach it to the end of the filename.

all help is highly appreciated
thank you

---

### Post by Vaphell on 2013-10-05
```
$ f=file1.txt
$ dest=test 
$ mkdir -p "$dest"
$ m=$( date -d @$( stat -c %Y "$f" ) +%b )
$ cp -v -- "$f" "$dest/${f}_$m"
„file1.txt” -> „test/file1.txt_Oct”
$ cp -v -- "$f" "$dest/${f%.*}_$m.${f##*.}"
„file1.txt” -> „test/file1_Oct.txt”
```
*stat --help* and *date --help* for more info.

---

### Post by aadil7 on 2013-10-05
why thank you for that..
i think having the month is not very accurate and this the i-node number would be more relative.. i had a look in stat --help and i-node was represented with a -i
i tried incorporating it but had no luck!
i already have the destination set up as to where i want it text to be written to just dont know how to extract the i-node.. a push in the right direction would be real nice :-)

---

### Post by Vaphell on 2013-10-05
> i had a look in stat --help and i-node was represented with a -i****

more like %i
```
$ stat -c %i file1.txt
302110
```

---

### Post by aadil7 on 2013-10-06
Ow right i see how this works.. Thanks for your help!

---

