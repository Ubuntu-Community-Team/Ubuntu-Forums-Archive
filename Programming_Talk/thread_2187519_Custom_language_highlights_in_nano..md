---
title: "Custom language highlights in nano."
date: 2013-11-12
forum: Programming Talk
---

### Post by yyttr3 on 2013-11-12
I'm reading a book on compilers and I want to make my own small language for the project. As a smaller poject to become familiar with regular expressions and lexical specifications I want to make a coloring for my language in nano, coloring things like identifiers,operators, delimiters, etc.

I have two files right now in ~/nano, tex.nanorc and sl.nanorc. tex.nanorc was already in the directory and sl.nanorc was created by me.
Both files contain about the same content right now:
```

##tex.nanorc:
syntax "tex" "\.tex$"
color red  "(-|\+)"

```
```

##sl.nanorc
syntax "sl" "\.sl$"
color red ("-|\+)"

```
.tex files work and color properly but .sl files will not. How do I enable sl.nanorc?

---

### Post by oldos2er on 2013-11-12
Moved to Programming Talk.

---

### Post by spjackson on 2013-11-13
Add a line to ~/.nanorc
```

include "~/nano/sl.nanorc"

```

---

