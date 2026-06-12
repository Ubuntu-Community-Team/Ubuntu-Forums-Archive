---
title: "help with output"
date: 2011-12-20
forum: Programming Talk
---

### Post by arunshankar.c on 2011-12-20
Hi gurus,

```

[carun@fattony] /u/carun/MTNN>
=> cat file2.txt
7000,2,1,6
7001,2,1,7
7002,2,1,6
7003,1,2,1

[carun@fattony] /u/carun/MTNN>
=> cat file1.txt
7000,2,1,6
7001,2,1,7
7002,2,1,6
7003,1,2,5

=> awk -F',' -v file1="$1" -v file2="$2" 'NR == FNR {a[$1,$2,$3,$4]++;count++;next} !(a[$1,$2,$3,$4]){print FNR FS $0}' OFS="," file2.txt file1.txt
4,7003,1,2,5

```

Now currently the output shows the lines in file2.txt which does not match with file1.txt

Can someone please guide me to process proper output, the expected output is as below :


```

Comparing 5 in file1.txt in column 4 in line 4 does not match with 1 in file2.txt with column 4 in line 4

```

Can anyone please guide me to get the above output ?

---

### Post by Petrolea on 2011-12-20
Awk supports formatting, so you can use printf to get the desired output. It's same as in C, D and many other languages.

[http://osr507doc.sco.com/en/OSUserG/_Formatting_awk_output.html](http://osr507doc.sco.com/en/OSUserG/_Formatting_awk_output.html)

---

### Post by sudodus on 2011-12-20
Have you tried the diff command?
```
diff file1.txt file2.txt
``` or
```
diff -y file1.txt file2.txt 
```or
```
diff -y --suppress-common-lines file1.txt file2.txt
```For more details, read ```
man diff
```

---

