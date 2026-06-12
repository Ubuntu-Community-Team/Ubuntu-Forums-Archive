---
title: "Using other programs or commands with C?"
date: 2007-06-25
forum: Programming Talk
---

### Post by MiCovran on 2007-06-25
All programming experience I have for now is from algorithm contests, so I don't have great knowledge of C or C++ and absolutely no "real life" experience.
Anyway, I am beginning to make some real console applications (just for education for now) and I was just wondering if there is a simple way to make my program execute another program (eg. cp and mkdir commands, vim, anything).

Thanks.

---

### Post by AlexThomson_NZ on 2007-06-25
Quite simple really, try system("program_name");

---

### Post by rapolas on 2007-06-25
Check here: [http://www.gidforums.com/t-3369.html](http://www.gidforums.com/t-3369.html)

---

### Post by slavik on 2007-06-27
I reccomend against using system() ... learn fork() and exec() :) (then you can monitor how long the program took and whether it needs to die or some such.

---

