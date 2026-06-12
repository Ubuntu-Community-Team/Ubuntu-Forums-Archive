---
title: "documentation"
date: 2015-02-09
forum: New to Ubuntu
---

### Post by safraoumohamed on 2015-02-09
i have two main issues 
* why the documentation appears in french 
* how do i learn the "console" part of ubunto 
thanx

---

### Post by Holger_Gehrke on 2015-02-09
> **safraoumohamed said:**
> i have two main issues 
* why the documentation appears in french

For the same reason the documentation appears in German on my machine. Someone set it up that way. Do you mean the help of the various GUI programs or the output of the man command ? 'man' can be told what language to use with the option '-L' followed directly by a language code, for example
```

man -Len ls

```
gives me the manual page for the 'ls' command in English. Of course, it can only give you manual pages which actually are available in the language you chose. If you chose a language for which a given manual page isn't available on your machine, it defaults to English.
> **safraoumohamed said:**
> 
* how do i learn the "console" part of ubunto 
thanx
There's a 'sticky' thread at the top of this forum about just this topic. Work through one or more of the tutorials listed in this thread, read a lot of man pages and try and try and ... Basically ? Learning by doing.

---

