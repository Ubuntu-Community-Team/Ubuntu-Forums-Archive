---
title: "AWK... printing last record (NOTE: Record, not Field)"
date: 2006-02-11
forum: Programming Talk
---

### Post by nsa_767 on 2006-02-11
Hi there,

I'm very new to programming/scripting and I've been playing around with AWK... I would like some pointers as to how I would get AWK to print last record in a file... I've tried 
basing my work on this example:

```
# print the first five input lines of a file, bit like head
        FNR == 1, FNR == 5  {  print $0 }

```
I attempted setting the FNR to NR-1 and NR, ie ```
 FNR == (NR-1), FNR == NR  {  print $0 }
```, but it doesn't work.

Maybe my direct approach is too simplistic? Was wondering, should I maybe use a loop of some sort?

Before anyone asks, I have googled for this, but I didn't find anything.

BTW: If PERL can do this then I'm open to suggestions as to use it.

---

### Post by kabus on 2006-02-11
```
awk 'END{print}' *filename*
```

---

### Post by nsa_767 on 2006-02-11
It works!! Cool, thanks man! I would never have thought it was that simple! Thanks again!

---

