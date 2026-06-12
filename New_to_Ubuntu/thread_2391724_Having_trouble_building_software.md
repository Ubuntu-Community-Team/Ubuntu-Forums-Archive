---
title: "Having trouble building software"
date: 2018-05-12
forum: New to Ubuntu
---

### Post by cryptoshun on 2018-05-12
Hello. I am trying to build [this software]("https://github.com/owner232/USDEX/releases"). I am fine in following the build instructions until I get to

```
make
```

then I get

```
make: *** No targets specified and no makefile found.  Stop.
```

Please help. Thanks.

FYI - I'm super new to linux, crypto, code, etc. - please bear with me.

---

### Post by TheFu on 2018-05-12
make really means gmake on linux.  It will look for a Makefile/makefile as the filename in the current working directory which contains instructions about dependencies for different targets. A target is the result/output of one of the stanzas inside the makefile.  It is common to have a makefile for each directory - lib/ would build the libraries for the project. bin/ would build the tools/programs for the project.   docs/ would transform any documents into desired output formats like text, markdown, xml, pdf or html.

I looked at the source tree.  They didn't name their makefiles with the default names. You can either rename them or pass an argument into make with the name of the makefile you want to be used. It is sorta odd to have a plain makefile distributed with a project these days.  Normally, they'd use autoconfig which would build the makefile for your system after checking for all the dependencies. 

TL;DR
$ make -f makefile.unix

---

