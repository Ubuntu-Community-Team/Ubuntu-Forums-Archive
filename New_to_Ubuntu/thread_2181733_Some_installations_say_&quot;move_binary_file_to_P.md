---
title: "Some installations say &quot;move binary file to PATH&quot;"
date: 2013-10-18
forum: New to Ubuntu
---

### Post by adam20 on 2013-10-18
I know what PATH is but what does a binary file look like?

---

### Post by Impavidus on 2013-10-19
A binary file often refers to an executable file. Stricktly speaking this is a misnomer, as script files are executable but not binary and most images are binary but not executable. In this case it probably is a binary executable. If you're manually installing something, it's best to put it in /home/username/bin/ or in /usr/local/bin/, both of which should be in your PATH by default (the former only if that directory exists).

---

