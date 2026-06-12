---
title: "Search a file for a common field in another file and merge the lines [grep, awk]"
date: 2013-05-11
forum: Programming Talk
---

### Post by supershin on 2013-05-11
Hi,

I have two files, file1 and file2. File1 has products names and prices. File2 has product name, description and other info.

If file1 has ASUS computer, $400 and file2 has ASUS computer, Ubuntu OS
then I want an output file ASUS computer, Ubuntu OS, $400.

Please help. The command to do or a straight-forward tutorial to do it will be very much appreciated.


Been searching around and trying different grep(advised not to use with loops?) and awk commands. 

grep ASUS computer file1 file2 > file3 works but I want to do this for more than one.

Not on pc with the code I used but it was something like 
for(i in file1)
  $d = awk $1
grep $d file2


while read
  $myvar < awk $1 file1
  grep $myvar file2 > file3
do

Do I use a loop, grep, awk?

---

### Post by prodigy_ on 2013-05-11
```
awk -F, 'FNR==NR{a[$1]=$2;next}(a[$1]){printf "%s,%s\n", $0, a[$1]}' file1 file2
```
But actually for such tasks you should use a database (e.g. SQLite) if you need to perform them routinely. You can import files into different tables and merge with SELECT ... JOIN. Or you could use [LibreOffice Calc](http://stackoverflow.com/questions/6709225/merging-data-in-open-libreoffice-calc).

---

### Post by supershin on 2013-05-11
Many many thanks! 

Though how would you use LibreOffice Calc to solve that? Import the files into different sheets and then...?

---

### Post by schragge on 2013-05-12
You also could try
```
sort -t, -k1,1 file1|join -t, <(sort -t, -k1,1 file2) -
``` or, if both files are already sorted on the common field, just ```
join -t, file2 file1
```

---

### Post by supershin on 2013-05-12
Thanks but the files aren't sorted. 

Should also add that not all products in file1 will be found in file2 and the common field.

Also I checked the LibreOffice Calc link for more info on how to do it in that.

---

### Post by schragge on 2013-05-13
> **supershin said:**
> Should also add that not all products in file1 will be found in file2 and the common field. Then the first command above should be adjusted as
```
sort -t, -k1,1 file1|join -t, -a2 -oauto <(sort -t, -k1,1 file2) -
```

---

