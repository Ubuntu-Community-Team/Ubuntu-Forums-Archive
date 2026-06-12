---
title: "Use of &quot;...&quot; in C/C++"
date: 2008-02-14
forum: Programming Talk
---

### Post by uljanow on 2008-02-14
hi,
I was wondering where I could find more information about "..." and how it could be used in C/C++ without going through the standards. Variable argument lists are the obvious use. But it did surprised me that following statements are allowed  (tested with c99/c++98 flags):

```
try {
} catch (...) {
}

switch (5) {
case 0 ... 9: 
    ;
}
```

---

### Post by Martin Witte on 2008-02-14
more on exception handling is here: [http://www.parashift.com/c++-faq-lite/exceptions.html](http://www.parashift.com/c++-faq-lite/exceptions.html)

---

