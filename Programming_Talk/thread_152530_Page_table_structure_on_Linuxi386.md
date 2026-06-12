---
title: "Page table structure on Linux/i386"
date: 2006-03-30
forum: Programming Talk
---

### Post by tepez on 2006-03-30
I have two questions:

1. What is the page size? 

2. For each level in the hierarchy, what is the number of entries to the next level?

---

### Post by LordHunter317 on 2006-03-30
4kiB or 4MiB and you have patches that will configure both.

I forget offhand, but look at the IA-32 Programmers Manual, Part 3.  It explains all of this in exhausting detail.

---

