---
title: "undefined reference - libnetpbm"
date: 2009-01-16
forum: Programming Talk
---

### Post by daniel1985 on 2009-01-16
Hi
I have installed libnetpbm10 and libnetpbm10-dev.
When i try to link a simple c-file containing

```
#include <pam.h>
..
pnm_readpaminit(file, &inpam, sizeof(inpam));
```

i get the following error:

```
Invoking: GCC C Linker
gcc  -o"follSeg2"  ./main.o   
./main.o: In function `main':
/media/sda3/Daniel/uni/Bachelor Thesis/follSeg2/Debug/../main.c:18: undefined reference to `pnm_readpaminit'
collect2: ld gab 1 als Ende-Status zurück
```

i also get the same error when i do it as a c++-project (linking with g++)!

thanks for any help or suggestions!

Daniel

---

### Post by Zugzwang on 2009-01-17
> **daniel1985 said:**
> i also get the same error when i do it as a c++-project (linking with g++)!

thanks for any help or suggestions!

Daniel

We're having the same question almost every week here (but with different libraries): You also need to *link* against that library, i.e. add "-lnetpbm" to the command for linking.

Just search for "undefined reference to" in this forum. You'll get plenty of explanations!

---

### Post by daniel1985 on 2009-01-17
thank you very much!
(I thought I searched - but maybe I didn't really know what to look for..)

---

