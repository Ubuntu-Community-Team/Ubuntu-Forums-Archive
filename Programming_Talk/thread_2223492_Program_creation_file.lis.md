---
title: "Program creation file.lis"
date: 2014-05-11
forum: Programming Talk
---

### Post by sandroterzi on 2014-05-11
Good morning friends, 

I have a little problem, i have a file in gedit with a list of these sequences are all different .

40067-01-07-00
40067-01-08-01
96050-02-03-05
56008-06-08-06

each sequence is a specific folder with several files including total.pds . What should the program is:

1 ) read the sequence file from gedit
2 ) Open the folder corresponding to the list
3 ) extract the files total.pds
4) write through

  ```
  ls total.pds > @ intervall.lis 
```

in a file called @intervall.lis

For example :

I have six folders in parent folder:

10252-02-08-02
40067-01-07-00
40067-01-08-01
50056-02-09-00
96050-02-03-05
56008-06-08-06

in the list

40067-01-07-00
40067-01-08-01
96050-02-03-05
56008-06-08-06

program :

10252-02-08-02 is in the list ? not, exclude folder
40067-01-07-00 is in the list ? yes, open the folder you take total.pds file and write it in @intervall.lis
40067-01-08-01 is in the list ? yes, open the folder you take total.pds file and write it in @intervall.lis
50056-02-09- 00E in the list? not, exclude folder
......
.....
.....

I should get to the end @intervall.lis :

total.pds from folder 40067-01-07-00
total.pds from folder 40067-01-08-01
......
......
.....

etc.

Thank you in advance!

):P):P:lolflag::lolflag:

---

### Post by dwhitney67 on 2014-05-11
Ubuntu Forums is not a homework service.  If you have attempted writing a shell script or other program (using the programming language of your choice), please show us what you have done.

If you have an specific questions regarding what you have attempted, I'm sure someone can help you.

---

### Post by sandroterzi on 2014-05-12
I know, but I don't have any idea how to fix this problem neither of which language is better to use, c++, shell scripting.

---

### Post by dwhitney67 on 2014-05-12
If you know bash shell scripting, then I would suggest you use that.

---

### Post by sandroterzi on 2014-05-12
Thank you very much dwhitney67 ;);)

---

### Post by sandroterzi on 2014-05-17
I did it, the program was easier than I thought. Thank you very much for the suggestion dwhitney67.

Good week-end

Bye Bye :lolflag::lolflag:

---

