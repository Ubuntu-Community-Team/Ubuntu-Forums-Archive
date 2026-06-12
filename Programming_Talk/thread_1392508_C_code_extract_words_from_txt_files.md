---
title: "C code: extract words from txt files"
date: 2010-01-28
forum: Programming Talk
---

### Post by erotavlas on 2010-01-28
Hi,
I'm searching a program capable to locate a words from a text file.

Before to write a C code I'm trying with a bash command

```
grep -e video -e audio uac_modificato_3261_messages.log | awk '{print $2}' | awk 'NR ==3, NR==4' > prova.txt


```

How can I store the result in two different C variables?

Thank

---

