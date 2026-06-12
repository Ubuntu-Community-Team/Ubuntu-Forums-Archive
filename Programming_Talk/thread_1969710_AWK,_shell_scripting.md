---
title: "AWK, shell scripting"
date: 2012-04-30
forum: Programming Talk
---

### Post by screechy on 2012-04-30
Hello AWK gurus,
I want to know if we can copy first line of each file from a folder and copy them into another file in a order. 

Eg. let's say the files are named as file1, file2, file3 etc. The output lines should be stored in output.txt. 
If first line in file1 = 123
   first line in file2 = 412
   first line in file3 = xyz

then, content of output.txt =    123 
                                                412
                                                xyz

Any idea folks? :confused:

---

### Post by sisco311 on 2012-04-30
```
head -qn1 * > newfile
```?

---

### Post by codemaniac on 2012-05-01
Since you have asked an awk one liner .

Here it goes ;) .
```
awk 'FNR==1' file* > output.txt
```

---

### Post by screechy on 2012-05-01
Thank you Sisco 311 and codemaniac :)

---

