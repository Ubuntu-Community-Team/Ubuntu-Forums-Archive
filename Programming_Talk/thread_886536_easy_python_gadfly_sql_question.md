---
title: "easy python gadfly sql question"
date: 2008-08-11
forum: Programming Talk
---

### Post by bigdidz on 2008-08-11
hello,

I think that my question is quite simple for somebody that hold the answer :).  I'm writing a python script and I want to save a (relativly) large amount of datas and work with them.  Consequently, I decided to use SQL and gadfly to do it.  I stored all my data in my database without any problems but now I want to compare all the datas with each of theme.

My problem is I do not know how to 'ask' the data base to feed me with the first row, then the second, the 3th...  And, in fact, I don't know eather how it will give it to me.

More generally, do you think that my gadfly chose is a good one.  I choose it because I read about it in a ebook (dive into python I think) but now I have a lot of dificulty to find docs about it.  It's maybe because it's the first time I use database and I don't have the basic knowlage about it but I'm an avreage programmer (In python at least).

thanks for your help, unfortunatly I need to go to work.

Didier

---

### Post by pmasiar on 2008-08-11
I don't care searching for gadfly: SQLite is excellent SQL-compatible database, and is included in core Py2.5. Use it, and any SQL will work for you.

---

