---
title: "Compiling - &quot;Objective-C not installed&quot;"
date: 2008-06-15
forum: Programming Talk
---

### Post by zman0 on 2008-06-15
I'm working with an older program under gcc 3.3, and I keep getting the error that "Objective-C not installed."

This is under the newest release of Ubuntu.  I have installed the latest version of objc, but gcc-3.3 doesn't seem to recognize it.

Any help?

---

### Post by geraldm on 2008-06-15
Compilers are created in suites; find the version of your C compiler, then use exactly the same version of objc.  It is not recommended to use differing versions of the C, objc compilers.  Perhaps you could try to find your matching objc compiler, rather than the latest objc ?

Gerald

---

