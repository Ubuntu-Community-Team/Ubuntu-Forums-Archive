---
title: "CHM to .doc conversion"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by digitalcali on 2008-09-21
Hi, im new to ubuntu and i want to know how to convert an ebook in .chm format to .doc format. i have tried htmldoc but it didnt work. i dont know if im doing something wrong or im using the wrong software. really appreciate it if someone can help me out.

---

### Post by spiderbatdad on 2008-09-21
i believe the program chm2pdf is in synaptic package manager.

---

### Post by cariboo on 2008-09-21
I couldn't find anything to convert a .chm to .doc, but htere is a utility in the repositories to canvert a chm file to a pdf. It is called chm2pdf. To install it:

```
sudo apt-get install chm2pdf
```

It is a command line tool so you have to open a terminal to use it:

```
man chm2pdf
```

Jim

---

### Post by spiderbatdad on 2008-09-21
the man page is a bit overwhelming, while the program is quite simple to use. Lets say you have the file "Prentice.Hall.PTR.The.Official.Ubuntu.Book.Aug.2006.chm"
 
The command would be:```
 sudo chm2pdf --webpage Prentice.Hall.PTR.The.Official.Ubuntu.Book.Aug.2006.chm

```You can also try the --book option.

---

### Post by TBerk on 2009-06-20
PS, and following up:  I found this thread useful.  Thx everybody.


berk

---

