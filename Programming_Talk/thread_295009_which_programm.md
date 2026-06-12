---
title: "which programm"
date: 2006-11-07
forum: Programming Talk
---

### Post by helphope on 2006-11-07
Hi there.

I was wondering if you can help me in this: I need a program which can open doc files (txt files is OK) and search text through regex and boolean operators.
I want to build it, only I don't know which program is better to learn.
My experience so far? A bit of python, javascript and php. That's all. 
Thanks for any help and hint:)

---

### Post by ansi on 2006-11-07
> **helphope said:**
> 
I was wondering if you can help me in this: I need a program which can open doc files (txt files is OK) and search text through regex and boolean operators.

*/bin/grep* ;).

---

### Post by helphope on 2006-11-07
Do you mean that grep can open doc files and has function such as highligthing of the searched text?

---

### Post by ansi on 2006-11-07
> **helphope said:**
> Do you mean that grep can open doc files and has function such as highligthing of the searched text?

Sorry for my inattention :(. For doc files you can use *catdoc* + *grep*. Catdoc extracts texts from .doc files. More details about last program:
```
apt-cache show catdoc | grep "^ "
```

---

### Post by helphope on 2006-11-08
> **ansi said:**
> Sorry for my inattention :(. For doc files you can use *catdoc* + *grep*. Catdoc extracts texts from .doc files. More details about last program:
```
apt-cache show catdoc | grep "^ "
```

Great. Thanks a lot. I'll try it

---

