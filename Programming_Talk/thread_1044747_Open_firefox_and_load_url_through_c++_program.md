---
title: "Open firefox and load url through c++ program"
date: 2009-01-19
forum: Programming Talk
---

### Post by Despot Despondency on 2009-01-19
Hi,

Question is in the title really. I want to write a program to open firefox and load a url. Does anyone have any good links to tutorials or examples of similar things? Thanks in advance.

---

### Post by Zugzwang on 2009-01-20
I don't know of any real cross-platform solution. But here's one for Linux:

```

#include <stdlib.h>

int main() {
    system("xdg-open www.google.com &");
}

```

---

### Post by hessiess on 2009-01-20
Use #ifdef to run differnt commands on differant platforms.

---

