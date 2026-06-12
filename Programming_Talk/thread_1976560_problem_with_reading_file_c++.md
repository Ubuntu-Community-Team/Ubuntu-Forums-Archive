---
title: "problem with reading file c++"
date: 2012-05-08
forum: Programming Talk
---

### Post by forsubhi on 2012-05-08
Any one know why this error appear 

[IMG]http://i50.tinypic.com/k0j3q1.png[/IMG]

the same code work well on ubuntu , but when I try it on windows this error appear in fopen.c .

I have another question 
is it possible to see visual studio running on ubuntu ?

---

### Post by muteXe on 2012-05-09
would you like to show some of your code please? :)

---

### Post by karlson on 2012-05-09
> **forsubhi said:**
> 
is it possible to see visual studio running on ubuntu ?

You can install VirtualBox and Windows in it and run VS.

---

### Post by gusnan on 2012-05-09
Its kind of hard to tell from the information you give us, but my guess is that the file you are trying to load isn't in the folder you expect. 
Visual studio builds executables in (for example) ./Debug/myexecutable.exe, instead of ./myexecutable.exe, so if you try to open a file in the same folder as the executable, it will not be found.
(It depends on the build type - it can be Debug/ or Release/ or something similar).

---

### Post by forsubhi on 2012-05-09
thank you the problem solved by installing latest version  of sphinxTrain code

---

