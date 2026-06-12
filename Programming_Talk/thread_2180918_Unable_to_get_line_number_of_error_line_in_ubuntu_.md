---
title: "Unable to get line number of error line in ubuntu terminal"
date: 2013-10-15
forum: Programming Talk
---

### Post by Javed_iqbal on 2013-10-15
Hy all;

I am using ubuntu 10.04 where when i compile my programme i get only column no.where error lies and hence unable to locate the column no.as line number is absent.PLz guide me its stopping me from debugging my code.
NB:Usually errror is specified by both line number and column number.

---

### Post by drmrgd on 2013-10-15
You would probably need to give more information.  What language and what compiler are you using?

---

### Post by Javed_iqbal on 2013-10-15
I am doing Socket programming using c.
Compiler information:
ii  gcc                                  4:4.4.3-1ubuntu1                                The GNU C compiler
ii  gcc-4.4                              4.4.3-4ubuntu5                                  The GNU C compiler
ii  libprotoc5                           2.2.0a-0.1ubuntu1                               protocol buffers compiler library
ii  protobuf-compiler                    2.2.0a-0.1ubuntu1                               compiler for protocol buffer definition file

---

### Post by whitesmith on 2013-10-15
Post a sample of the error info you get.

---

### Post by Javed_iqbal on 2013-10-18
> **whitesmith said:**
> Post a sample of the error info you get.

like this 
serverprct.c: In function ‘main’:
serverprct.c:76: error: expected declaration or statement at end of input
here column no.76 given as error.but which line ? i need this infotmation.how to get it.PLease

---

### Post by QIII on 2013-10-18
*Moved to **Programming Talk***

---

### Post by ofnuts on 2013-10-18
What makes you think the '76' is a column number? It's a line number... But since the message is telling you the compiler expected more stuff, it may be the number of the line it was trying to read and didn't find, ie, one line after your final line. Typically you are missing a closing brace higher in the file.

---

