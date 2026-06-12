---
title: "[C++] Traversing a linked list"
date: 2008-07-21
forum: Programming Talk
---

### Post by ogwilson on 2008-07-21
[http://pastebin.com/m90476f](http://pastebin.com/m90476f)

I try to compile the source code there and I get this error.

```
main.cpp(26): error C2470: 'traverseList' : looks like a function definition, but there is no formal parameter list; skipping apparent body

```I have no clue what it would mean by this. It's a perfectly valid method, no?

EDIT - NVM. I used an opening brace instead of a parenthesis for my parameter list lol. Sorry. Ill keep this thread open though just in case I have any questions later on while im studying lists and linked lists.

---

### Post by Zugzwang on 2008-07-22
Note that that is no g++ compiler error message. If you use anything else than the standard compilers, you should state that.

---

### Post by dwhitney67 on 2008-07-22
There is a syntax error on line 26 of the code you posted.  The open curly-brace '{' should be an open parenthesis '('.

Don't depend on a compiler to always find the syntax errors.  Just use your eyes/mind.

P.S.  That code looks very much like C code, not C++.  Oh wait, it's using iostream and cout.  :rolleyes:

---

### Post by ogwilson on 2008-07-24
Yea sorry guys, I'm using Visual Studio on windows. I still like to come to the linux boards to get help though as they are much more helpful.

---

