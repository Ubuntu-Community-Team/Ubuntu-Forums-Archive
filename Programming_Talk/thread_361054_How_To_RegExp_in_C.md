---
title: "How To RegExp in C?"
date: 2007-02-13
forum: Programming Talk
---

### Post by SuperMike on 2007-02-13
I'm trying to relearn C after being away from it for more than 20 years. (God, am I that old??) In C, if I have a file's contents in a variable in memory, how do I apply RegExp's to that variable?

---

### Post by lloyd_b on 2007-02-14
Use the regcomp() and regexec() functions.  Try "man regex" in a terminal window for details on how to use them.

Lloyd B.

---

### Post by SuperMike on 2007-02-14
So I compile a regexp first, and then execute it. I get it. That's sort of like how ngs-js does its regexp.

---

