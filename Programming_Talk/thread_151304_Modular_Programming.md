---
title: "Modular Programming"
date: 2006-03-27
forum: Programming Talk
---

### Post by zachtib on 2006-03-27
Could anyone link me to a reference to modular programming? Preferably in C

---

### Post by derelict on 2006-03-27
I'm not sure I understand your question, do you mean object oriented? If so: [http://oopweb.com/](http://oopweb.com/)
You can use a modular approach to C dividing your code into .c files according to a context.

---

### Post by zachtib on 2006-03-27
[QUOTE=derelict]I'm not sure I understand your question, do you mean object oriented? If so: [http://oopweb.com/](http://oopweb.com/)
You can use a modular approach to C dividing your code into .c files according to a context.[/QUOTE]

Basically, I want to make it easy to add and remove features to my program later.

What I need to know is basically how to write the make files to build all the different parts

---

### Post by dave_567 on 2006-03-28
You could give this one a try...

Object Orientated Programming in ANSI-C

[http://www.planetpdf.com/developer/article.asp?contentid=6635&ra](http://www.planetpdf.com/developer/article.asp?contentid=6635&ra)

---

### Post by LordHunter317 on 2006-03-28
None of those have anything to do with what the OP is asking, I think.

Do you mean plugins?  More details.

---

### Post by zachtib on 2006-03-29
[QUOTE=LordHunter317]None of those have anything to do with what the OP is asking, I think.

Do you mean plugins?  More details.[/QUOTE]

mabye that's what im thinking of.

basically, im working on my carputer project (which is now on sourceforge, yay!) and I want to be able to enable or disable certain features at build time.  for example, if the usr did not have a gps attachment for their carputer, they could build it with 
```
./configure --disable-gps
```
either that or plugins. because I want other people to be able to easily add features, so maybe a plugin system is what im looking for...

---

