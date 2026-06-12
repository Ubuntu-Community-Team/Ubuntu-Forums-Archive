---
title: "What source-code browsing tools do you use?"
date: 2010-04-19
forum: Programming Talk
---

### Post by icodemonkey on 2010-04-19
I was just wondering what tools other programmers out there use to brows/find a particular piece of code (be it a snippet, function, file or full app) in your collection of source-code?
I'm just wanting to speed up the time it takes to find a block of code (currently about 30mins - 1h).
Also would prefer a GUI app (boss hates CLI (don't ask))

---

### Post by phrostbyte on 2010-04-19
I guess the "Find in Files" Gnome applet. Perhaps not what you mean?

---

### Post by schauerlich on 2010-04-19
grep?

---

### Post by nvteighen on 2010-04-20
emacs?

---

### Post by wmcbrine on 2010-04-20
"grep" (actually fgrep) and "less" here. Yes, they're CLI, but that's why I use, sorry.

---

### Post by Compyx on 2010-04-20
grep

---

### Post by texaswriter on 2010-04-20
If it's *for* your boss, then I'd say make a frontend for grep. Grep really does it's job well. 

As far as "not liking CLI", that's kind of irrelevant if it IS the tool for the job. If it's for you, I imagine grep would work well. It REALLY is a powerful tool. :lolflag:

---

### Post by myrtle1908 on 2010-04-20
Eclipse has excellent search capabilities including workspace and project scoped searches, local and remote file searches and language specific searches.  For example, you could search for source code based on Types, Fields, Packages, Methods, and so on.  If you have other plugins installed eg. an LDAP browser, the search functionality for these are usually seamlessly integrated into the Eclipse search tool.

---

### Post by the_unforgiven on 2010-04-20
ctags/cscope :)

Mind you, cscope can index code in other languages too (given in cscope.files).

---

### Post by dribeas on 2010-04-20
```

find . -name \*.cpp -o -name \*h -o -name \*.py -print0 | xargs -0 grep "" | less

```

Find all code files, pass them onto grep so that it prepends the file name to each line, and list the result in less... And if you wonder about the time it might take... well, I use it regularly and the data less processes is well over 130M worth of source code.

---

