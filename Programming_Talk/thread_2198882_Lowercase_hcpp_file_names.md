---
title: "Lowercase h/cpp file names"
date: 2014-01-11
forum: Programming Talk
---

### Post by kangaba on 2014-01-11
Hi,
Is there any other reason for storing all h/hpp/cpp file names lowercase besides the fear of windows (and Macs with a case insensitive HFS) users forgetting to respect case sensitivity?

---

### Post by spjackson on 2014-01-11
Both lowercase only and mixed case are perfectly valid and workable choices. The standard library and boost stick to lowercase, whereas Qt uses mixed case. Of course, the standard library and boost also opt for lowercase identifiers. My personal preference is to keep to lowercase, probably largely due to historical baggage and my begrudging use of mixed case identifiers.

If you use mixed case for filenames, you may end up typing horrors like e.g.
```

grep foo *[Kk][Ee][Yy]*.[hH]*

```because
```

grep foo *key*.h*

```won't do.

I have found this particularly irksome with sources brought from Windows. I have also been bitten by projects written for Windows that then don't build on Linux because, however well-intentioned the original author, mistakes with the case of filenames don't get picked up until after you move the source from Windows. I find "lowercase only" easier to get right.

---

### Post by Vaphell on 2014-01-11
*shopt -s nocaseglob* FTW :-)

---

### Post by ofnuts on 2014-01-11
and "grep -i"...

---

