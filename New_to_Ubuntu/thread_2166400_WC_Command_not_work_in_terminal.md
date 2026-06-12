---
title: "WC Command not work in terminal"
date: 2013-08-09
forum: New to Ubuntu
---

### Post by radha2 on 2013-08-09
Hello Friends

I used ubuntu 10.04 and i am trying to perform WC command to count word & line but it gives 

**" wc -c radha.txt****wc: radha.txt: No such file or directory "**


so how to solve this problem ?

---

### Post by d2btoo on 2013-08-09
[QUOTE=radha2]" wc -c radha.txtwc: radha.txt: No such file or directory "[/QUOTE]
It means the file path is wrong, check the file path!
BTW [COLOR=seagreen]wc -w[/COLOR] counts words not [COLOR=firebrick]wc -c[/COLOR]

---

### Post by gordintoronto on 2013-08-09
Use this command: locate radha.txt
then cd to the directory where it lives.

---

### Post by The Cog on 2013-08-10
Just in case you didn't realise - filenames on Linux are case sensitive.

It might help to type "wc " into a command prompt and then drag the file icon from the file manager and drop it on the command prompt window.

---

