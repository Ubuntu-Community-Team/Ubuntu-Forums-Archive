---
title: "&quot; makefile &quot; where ?"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2008-07-09
I have just downloaded and extracted a program and the readme file says all I have to do is type " make " to build , but it doesn't say where , and when I try it in terminal all I get are error messages. Previous threads on this subject are not clear enough for me. Thanks.

---

### Post by sujoy on 2008-07-09
you have to cd to the directory where you extracted the program. if there is a "configure" file in there, then do

./configure
make
make install

---

### Post by ex-wirecutter on 2008-07-09
I assume you do this in the terminal widow , yes ?

---

### Post by Elfy on 2008-07-09
Yes you do - while you are in there make sure you have build essential installed

sudo apt-get install build-essential

---

### Post by ex-wirecutter on 2008-07-09
Thanks for your help , I'll give it a try.
Much obliged,

---

### Post by nowshining on 2008-07-10
any libs needed are -dev versions, when u install those from synaptic or apt-get - ./configure again until u don't get any errors.

---

