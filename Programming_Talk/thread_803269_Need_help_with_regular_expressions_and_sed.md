---
title: "Need help with regular expressions and sed"
date: 2008-05-22
forum: Programming Talk
---

### Post by yaztromo on 2008-05-22
I have a simple text file of which I need to erase the first 97 columns of each line.

Presently I have been using the line:

```
sed 's/^................................................................................................//g' prods2.csv > prods3.csv
```

Obviously this isn't very elegant. I'd like something a little smaller, so I tried:

```
sed 's/^.{97}//g' prods2.csv > prods3.csv
```

Which doesn't work at all. What am I doing wrong? Suggestions very much appreciated.

---

### Post by mali2297 on 2008-05-22
I think **cut** is an appropriate tool for this task. Try
```

cut -c98- prods2.csv > prods3.csv

```
or
```

cut --complement -c1-97 prods2.csv > prods3.csv

```
Read *man cut* for more information.

---

### Post by yaztromo on 2008-05-22
Awesome I was unaware of that command. Thanks :)

---

### Post by manicman on 2008-05-22
If you wanted you to use sed you could use the expression
```
sed -ni '98,$ p' file_name.txt
```
this will output from line 98 until the end of the file from "file_name.txt" and then overwrite the file afterwards

---

### Post by K.Mandla on 2008-05-22
Moved to Programming Talk.

---

### Post by WW on 2008-05-22
> **yaztromo said:**
> ... so I tried:

```
sed 's/^.{97}//g' prods2.csv > prods3.csv
```

Which doesn't work at all. What am I doing wrong? Suggestions very much appreciated.
It looks like the **cut** command is a simple way to accomplish what you want, but since you asked...

Use the **-E** option to tell sed that you are using an "extended" (or "modern") regular expression rather than a basic regular expression:
```
sed -E 's/^.{97}//' prods2.csv > prods3.csv
```
(Since you are matching from the beginning of the line, the **g** flag will have no effect and can be dropped.)

---

### Post by yaztromo on 2008-05-22
Thanks for your response WW.

I need to do some research on the difference between extended and non-extended regex now :)

---

