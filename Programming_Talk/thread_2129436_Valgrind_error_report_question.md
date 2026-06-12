---
title: "Valgrind error report question"
date: 2013-03-26
forum: Programming Talk
---

### Post by heatblazer on 2013-03-26
Hello,  I need some help with valgrind`s output. I will attack valgrind`s log so if somebody have time to check on it and report why exactly there are these mysterious 27 errors. As far as I know I`ve freed all allocated memory blocks, but I still don`t get where the error is. The compiler does not complain. The program runs with no segfaults or other problems but in valgrind there are these strannge 27 errors form 11 contexts :(
Please advice!

---

### Post by spjackson on 2013-03-26
Debugging without source code is hard. However, it looks like:
[LIST=1]
[*]You need to check what you are passing to printf in printTextNodeList.
[*]Something's not right in addTextNode or splitToData.
[*]Something's not right in clearTextNode (or perhaps memory's corrupted before you get there.)
[/LIST]

---

### Post by MadCow108 on 2013-03-26
--db-attach=yes and --track-origins=yes are two useful flags which might help

also build your program with debugging information (-g) for better reports

---

