---
title: "Makefile that reads a separate list of sources"
date: 2008-12-17
forum: Packaging and Compiling Programs
---

### Post by night_fox on 2008-12-17
Hi, I have been using a makefile that contains a single massive line specifying all my source code files. I would like to have a separate file containing a neat list of source code files. Why won't this line work:

```
SRC = `cat sourcefiles.lst`
```
It gives me an error message: no rule to make target |||||`cat |||||

or this one:

```
SRC = $(`cat sourcefiles.lst`)
```

SRC becomes an empty string and nothing gets compiled, so it links the result and gives me |||||Undefined reference to main|||||

I also have this similar line which has worked for ages:

```
LIBS =  `pkg-config --libs gtk+-2.0 gdk`
```

What is going on? How can I make this work?

---

