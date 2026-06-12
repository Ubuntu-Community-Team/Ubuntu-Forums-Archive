---
title: "C++ Virtual Functions and Function Overloading"
date: 2007-08-09
forum: Programming Talk
---

### Post by SNYP40A1 on 2007-08-09
I am building a compiler and I am able to build parse trees.  I have several types of objects used for storing information -- Types which record variable type, Variable Declarations which hold a Type and an Identifier, function declarations, etc.  I am at the part where I am building my symbol table.  I only need to put variable declarations in my symbol table so the only object that will make an entry is a variable declaration.  All my objects are based on a node class.  So I want to crawl over my parse tree and at this point, just simply print back out all the variable declarations.  I want to assign a function in my node class which will most of the time do nothing, but then I want to over-ride it for certain classes to do something.  How do I do this?

---

### Post by sonofusion82 on 2007-08-09
you would want to use virtual table.. [http://en.wikipedia.org/wiki/Virtual_table](http://en.wikipedia.org/wiki/Virtual_table)

---

### Post by slavik on 2007-08-09
ooh, interesting? any sample code for your new compiler yet? would be fun to play around with it? is there a name for the language or are you building your own C++ compiler of sorts?

---

### Post by aks44 on 2007-08-09
> **slavik said:**
> ooh, interesting? any sample code for your new compiler yet? would be fun to play around with it

+1 :KS

---

