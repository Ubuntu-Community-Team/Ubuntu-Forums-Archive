---
title: "Where are the antlr3 C headers?"
date: 2010-10-27
forum: Repositories &amp; Backports
---

### Post by aof_doomchild on 2010-10-27
I've installed antlr from the repo, and I can use it to generate C source files from a grammar file just fine (e.g., "antlr3 grammar.g").  However, it looks like the necessary headers aren't being installed, because I get a message about antlr3.h not being found when I try to use the generated lexer and parser.

Here are the packages I've installed:

[LIST=1]
[*]antlr
[*]antlr3
[*]antlr3-gcj
[*]libantlr-dev
[*]libantlr-java
[/LIST]

Am I just not seeing something else, or is this a problem with the package?

---

