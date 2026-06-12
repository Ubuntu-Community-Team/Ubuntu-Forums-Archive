---
title: "Who reads the shebang?"
date: 2013-11-05
forum: Programming Talk
---

### Post by sha1sum on 2013-11-05
Hello guys, I'm learning to make shell scripts, and I've got a doubt regarding the shebang (the **#!/bin/bash** thing).

My question is: who/what reads the shebang? It starts with a #, so that would make it a comment. But it isn't actually ignored. I've found that if you have a shebang with: **#!/bin/bash **then the script behaves as if you type every line on the terminal, while if you have a shebang like **#!/bin/cat**, the whole thing gets treated as input for the cat command, and the scripts contents (including shebang) get printed as standard output.

So something is reading the shebang. Is it the Bourne Again shell? And if yes, does it ignore the hash that should make it a comment? Or is a comment that starts with **#!** not actually a comment?

---

### Post by ofnuts on 2013-11-05
It's the program loader. The shebang starts with a # because the # is a comment on most script languages (and other languages will recognize a shebang in the first line). See [http://en.wikipedia.org/wiki/Shebang_%28Unix%29](http://en.wikipedia.org/wiki/Shebang_%28Unix%29)

---

### Post by vasa1 on 2013-11-05
Also [http://unix.stackexchange.com/questions/98993/what-is-the-language-that-appears-on-the-first-line-of-a-script](http://unix.stackexchange.com/questions/98993/what-is-the-language-that-appears-on-the-first-line-of-a-script) and the other links in there

---

