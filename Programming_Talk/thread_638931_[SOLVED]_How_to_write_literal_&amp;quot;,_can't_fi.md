---
title: "[SOLVED] How to write literal &amp;quot;, can't find out how online :/"
date: 2007-12-12
forum: Programming Talk
---

### Post by cerealtx on 2007-12-12
anyone know? i assumed /" but not that easy :(

---

### Post by vambo on 2007-12-12
What like 

```
echo \"
```?

---

### Post by jken146 on 2007-12-12
Back slash is usually used to escape characters, not forward slash.  What are you trying to write it in?

---

### Post by cerealtx on 2007-12-12
ive got to use Vbscript for some ajax and im not familar with vb, id use php  but the dam server is ******* up with php so im just switching over to vb ill try \ ty

edit: nvm im just going to use PHP its so much easier heh ty anyway guys

---

### Post by jviscosi on 2007-12-12
In regular VB you escape a quote by doing it twice, e.g., "" (which is not the easiest thing in the world to read).  So you'd end up with something like this:

```

Debug.Print "Jim said, ""Why do I have to escape quotes in this stupid fashion?"""

```

---

