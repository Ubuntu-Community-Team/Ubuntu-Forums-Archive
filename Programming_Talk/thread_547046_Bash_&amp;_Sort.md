---
title: "Bash &amp; Sort"
date: 2007-09-09
forum: Programming Talk
---

### Post by mfreeze on 2007-09-09
Does anyone have any any experience with the following situation?

I am using BASH and I am trying to sort a file using the command-line sort command.  I have done this on Fiesty and on Dapper and get the same results. Consider the following tab-delimited file (test.txt)(Tabs indicated as [tab] for readability):

> PSL [tab] 99887766 [tab] Bill Blue [tab] 33445566
PSL [tab] 99887766 [tab] Bill Blue  [tab] 33445566
PFF [tab] 43305900 [tab] Yasmine Yellow [tab] 12097847
PAB [tab] 34567901 [tab] Gina Gold [tab] 21309854
PXX [tab] 12345765 [tab] Ralph Red [tab] 67480194
PTR [tab] 87458762 [tab] Paul Purple [tab] 78409710
If I perform the sort:

```
sort -t \t -k 1 test.txt
```

I correctly get:

> PAB     34567901        Gina Gold       21309854
PFF     43305900        Yasmine Yellow  12097847
PSL     99887766        Bill Blue       33445566
PSL     99887766        Bill Blue       33445566
PTR     87458762        Paul Purple     78409710
PXX     12345765        Ralph Red       67480194

If I sort:

```
sort -r -t \t -k 1 test.txt 
```

> PXX     12345765        Ralph Red       67480194
PTR     87458762        Paul Purple     78409710
PSL     99887766        Bill Blue       33445566
PSL     99887766        Bill Blue       33445566
PFF     43305900        Yasmine Yellow  12097847
PAB     34567901        Gina Gold       21309854

However, If I try to sort the 4th field with:

```
sort -t \t -k 4 test.txt
or 
sort -n -t \t -k 4 test.txt
or 
sort -n -t \t -k 4,4 test.txt
```

I get

> PAB     34567901        Gina Gold       21309854
PFF     43305900        Yasmine Yellow  12097847
PSL     99887766        Bill Blue       33445566
PSL     99887766        Bill Blue       33445566
PTR     87458762        Paul Purple     78409710
PXX     12345765        Ralph Red       67480194

No matter what I do, it will not sort the file by the 4th column.  

However, with this same file, this operation does work correctly on my OpenBSD box. (Or should I say that I can accurately sort by the 4th field on my OpenBSD box.)

What can the problem be on Linux?

Thanks,
Mark.

---

### Post by Lux Perpetua on 2007-09-09
The problem is that **\t** evaluates to **t** in bash. The trick is getting a literal tab character onto your command line. bash and readline don't make this very easy in my opinion. (Any naive attempt to press the tab character will trigger the command-completion feature.) The way to do it is to press **Control-V** before you press **Tab**. **Control-V** causes the next key you press to be interpreted literally and inserted on the command line. Make sure you enclose your tab character in quotes, or bash will treat it as blank space and skip it!

**edit:** Alternatively, you can use a shell other than bash, one that interprets the Tab key literally.

---

### Post by ghostdog74 on 2007-09-09
```

sort  -k4 file

```

---

### Post by mfreeze on 2007-09-09
It works!  I bow inthe presence of your supreme knowledge.  

Why does this work correctly in the Bash shell on OpenBSD, but not in the Bash shell on Linux?   I have a friend who observed the same behavior on Fedora.

Again, thanks for the help.

Regards,
Mark.

---

### Post by Lux Perpetua on 2007-09-09
Can you post the output of **bash --version** on your OpenBSD box?

**edit:** I just found a cleaner way to solve your problem: > sort -n -t $'\t' -k 4 test.txt

See [http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_03.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_03.html), the section on ANSI-C quoting.

---

