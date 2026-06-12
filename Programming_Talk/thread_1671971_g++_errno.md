---
title: "g++ errno"
date: 2011-01-20
forum: Programming Talk
---

### Post by NimReh on 2011-01-20
Hi everybody ,, I need some help here
I need to know how to get the compilation error number for my  application, while my application is close to be an editor for c++..
Iam working under java/Netbeans IDE..
Any help??

---

### Post by worksofcraft on 2011-01-22
> **NimReh said:**
> Hi everybody ,, I need some help here
I need to know how to get the compilation error number for my  application, while my application is close to be an editor for c++..
Iam working under java/Netbeans IDE..
Any help??

Are you writing an application in Java that runs g++ and you want to retrieve the compilation error codes that g++ produces?

I know that with some compilers these are in a standard format so that an IDE can read them from the error output strings and take you directly to the offending source code line.

I don't know if you can rely on the format that g++ produces, but it appears to be:
```

base.cpp:22: error: expected unqualified-id before &#8216;}&#8217; token

```
i.e. file name:line number: "error" or "warning": description... but not actually an error identification code. Is that what you are trying to obtain?

---

### Post by ibuclaw on 2011-01-22
Maybe he means the return code of a failed compilation?

---

