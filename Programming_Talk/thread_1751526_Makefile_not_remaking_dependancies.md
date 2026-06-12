---
title: "Makefile not remaking dependancies"
date: 2011-05-06
forum: Programming Talk
---

### Post by nolag on 2011-05-06
This is my Makefile:

```
CXX = g++
LEXER = lexer
LEXFLAGS = -lfl

lexer: lex.yy.c badCode.h badCode.o
    $(CXX) $(LEXFLAGS) lex.yy.c badCode.o -o $(LEXER)

badCode.o:
    $(CXX) -c badCode.cpp

lex.yy.c:
    flex lexer.l

clean:
    rm *.o $(LEXER) *.yy.c

```

What I want:
If I edit badCode.c it should remake badCode.o and if I change lexer.l it should remake lexer.l

I was under the assumption that this was the whole reason for the make file, it would update the stuff that needs to be.  

What it dose:
Won't remake lex.yy.c if lexer.l is changed and won't update badCode.o if badCode.cpp is changed.  I don't get it please HELP

---

### Post by nolag on 2011-05-06
Sorry I see my error.

---

### Post by dwhitney67 on 2011-05-06
Does your Makefile work if you "touch" (or modify) badcode.cpp?

Would your Makefile work if you had N-number of modules.?

P.S.  You do not need to define CXX; 'make' is already aware of this.

---

