---
title: "Problem after updating GCC"
date: 2014-04-17
forum: Packaging and Compiling Programs
---

### Post by drek700 on 2014-04-17
Hi, I updated gcc from 4.6 to 4.8, but now my old code doesn't work anymore. I supoussed that the new version would understand the old code (not really old, just normal!), but now the compiler throws a lot or errors, for example using templates it tell me that it needs them like vector<vector<int> > and not like vector<vector<int>>. How can I compile my code again?

Thank for your help.

P.S.: I installed again gcc 4.6 (now I have both) and make it the default compiler, but the problem remains.

---

### Post by spjackson on 2014-04-18
The ability to use '>>' in this context rather than '> >' was new in C++11, see [http://www.stroustrup.com/C++11FAQ.html#brackets](http://www.stroustrup.com/C++11FAQ.html#brackets) . So perhaps you were specifying "-std=" before and are no longer doing so.

---

