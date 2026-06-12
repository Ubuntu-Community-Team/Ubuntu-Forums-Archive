---
title: "Problem with older version of gcc"
date: 2012-06-25
forum: Programming Talk
---

### Post by MKam on 2012-06-25
Hi
I have installed a gcc-3.3 on Ubuntu 12. the installed gcc is worked and I can compiled simple codes. However, when the code contains include files, the gcc gives a bunch of errors which all of them about the header files. 

This is the code:

#include <stdlib.h>
int main(){
    int a =0;
    int c = 1;
    int b= 4;
    for(a = 0; a < 100; a++)
    {
        c += b;
        b += a;
    }
    return c;
}

The errors after "gcc-3.3  m.c" command

```
In file included from /usr/include/stdlib.h:25,
                 from m.c:1:
/usr/include/features.h:324:26: bits/predefs.h: No such file or directory
/usr/include/features.h:357:25: sys/cdefs.h: No such file or directory
/usr/include/features.h:389:23: gnu/stubs.h: No such file or directory
In file included from m.c:1:
/usr/include/stdlib.h:42:29: bits/waitflags.h: No such file or directory
/usr/include/stdlib.h:43:30: bits/waitstatus.h: No such file or directory
In file included from m.c:1:
/usr/include/stdlib.h:68: error: syntax error before "typedef"
/usr/include/stdlib.h:98: error: syntax error before "typedef"
/usr/include/stdlib.h:116: error: syntax error before "__BEGIN_NAMESPACE_C99"
/usr/include/stdlib.h:140: error: syntax error before "extern"
/usr/include/stdlib.h:140: error: syntax error before "__THROW"
/usr/include/stdlib.h:145: error: syntax error before "extern"
/usr/include/stdlib.h:146: error: syntax error before "__THROW"
/usr/include/stdlib.h:149: error: syntax error before "__THROW"
/usr/include/stdlib.h:152: error: syntax error before "__THROW"
/usr/include/stdlib.h:159: error: syntax error before "__THROW"
/usr/include/stdlib.h:165: error: syntax error before "extern"
/usr/include/stdlib.h:167: error: syntax error before "__THROW"
/usr/include/stdlib.h:173: error: syntax error before "extern"
/usr/include/stdlib.h:174: error: syntax error before "__THROW"
/usr/include/stdlib.h:178: error: syntax error before "__THROW"
/usr/include/stdlib.h:184: error: syntax error before "extern"
/usr/include/stdlib.h:186: error: syntax error before "__THROW"
/usr/include/stdlib.h:190: error: syntax error before "__THROW"
/usr/include/stdlib.h:198: error: syntax error before "__THROW"
/usr/include/stdlib.h:203: error: syntax error before "__THROW"
/usr/include/stdlib.h:212: error: syntax error before "__THROW"
/usr/include/stdlib.h:217: error: syntax error before "__THROW"
/usr/include/stdlib.h:311: error: syntax error before "extern"
/usr/include/stdlib.h:311: error: syntax error before "__THROW"
/usr/include/stdlib.h:315: error: syntax error before "__THROW"
/usr/include/stdlib.h:320:49: sys/types.h: No such file or directory
/usr/include/stdlib.h:327: error: syntax error before "__THROW"
/usr/include/stdlib.h:330: error: syntax error before "__THROW"
/usr/include/stdlib.h:337: error: syntax error before "__THROW"
/usr/include/stdlib.h:341: error: syntax error before "__THROW"
/usr/include/stdlib.h:351: error: syntax error before "int32_t"
/usr/include/stdlib.h:353: error: syntax error before '*' token
/usr/include/stdlib.h:357: error: syntax error before '*' token
/usr/include/stdlib.h:358: error: syntax error before '}' token
/usr/include/stdlib.h:361: error: syntax error before "int32_t"
/usr/include/stdlib.h:364: error: syntax error before "__THROW"
/usr/include/stdlib.h:369: error: syntax error before "__THROW"
/usr/include/stdlib.h:373: error: syntax error before "__THROW"
/usr/include/stdlib.h:380: error: syntax error before "extern"
/usr/include/stdlib.h:380: error: syntax error before "__THROW"
/usr/include/stdlib.h:382: error: syntax error before "__THROW"
/usr/include/stdlib.h:387: error: syntax error before "extern"
/usr/include/stdlib.h:387: error: syntax error before "__THROW"
/usr/include/stdlib.h:395: error: syntax error before "__THROW"
/usr/include/stdlib.h:396: error: syntax error before "__THROW"
/usr/include/stdlib.h:399: error: syntax error before "__THROW"
/usr/include/stdlib.h:401: error: syntax error before "__THROW"
/usr/include/stdlib.h:404: error: syntax error before "__THROW"
/usr/include/stdlib.h:406: error: syntax error before "__THROW"
/usr/include/stdlib.h:409: error: syntax error before "__THROW"
/usr/include/stdlib.h:411: error: syntax error before "__THROW"
/usr/include/stdlib.h:412: error: syntax error before "__THROW"
/usr/include/stdlib.h:429: error: syntax error before "__THROW"
/usr/include/stdlib.h:432: error: syntax error before "__THROW"
/usr/include/stdlib.h:437: error: syntax error before "__THROW"
/usr/include/stdlib.h:441: error: syntax error before "__THROW"
/usr/include/stdlib.h:446: error: syntax error before "__THROW"
/usr/include/stdlib.h:450: error: syntax error before "__THROW"
/usr/include/stdlib.h:454: error: syntax error before "__THROW"
/usr/include/stdlib.h:457: error: syntax error before "__THROW"
/usr/include/stdlib.h:461: error: syntax error before "__THROW"
/usr/include/stdlib.h:471: error: syntax error before "extern"
/usr/include/stdlib.h:471: error: syntax error before "__THROW"
/usr/include/stdlib.h:474: error: syntax error before "__THROW"
/usr/include/stdlib.h:479: error: syntax error before "__BEGIN_NAMESPACE_STD"
/usr/include/stdlib.h:485: error: syntax error before "extern"
/usr/include/stdlib.h:486: error: syntax error before "__THROW"
/usr/include/stdlib.h:488: error: syntax error before "__THROW"
/usr/include/stdlib.h:493: error: syntax error before "extern"
/usr/include/stdlib.h:493: error: syntax error before "__THROW"
In file included from /usr/include/stdlib.h:497,
                 from m.c:1:
/usr/include/alloca.h:33: error: syntax error before "extern"
/usr/include/alloca.h:33: error: syntax error before "__THROW"
In file included from m.c:1:
/usr/include/stdlib.h:503: error: syntax error before "extern"
/usr/include/stdlib.h:503: error: syntax error before "__THROW"
/usr/include/stdlib.h:509: error: syntax error before "__THROW"
/usr/include/stdlib.h:514: error: syntax error before "extern"
/usr/include/stdlib.h:514: error: syntax error before "__THROW"
/usr/include/stdlib.h:518: error: syntax error before "__THROW"
/usr/include/stdlib.h:536: error: syntax error before "extern"
/usr/include/stdlib.h:537: error: syntax error before "__THROW"
/usr/include/stdlib.h:544: error: syntax error before "extern"
/usr/include/stdlib.h:544: error: syntax error before "__THROW"
/usr/include/stdlib.h:557: error: syntax error before "__BEGIN_NAMESPACE_C99"
/usr/include/stdlib.h:560: error: syntax error before "extern"
/usr/include/stdlib.h:560: error: syntax error before "__THROW"
/usr/include/stdlib.h:565: error: syntax error before "__BEGIN_NAMESPACE_STD"
/usr/include/stdlib.h:567: error: syntax error before "extern"
/usr/include/stdlib.h:567: error: syntax error before "__THROW"
/usr/include/stdlib.h:572: error: syntax error before "extern"
/usr/include/stdlib.h:573: error: syntax error before "__THROW"
/usr/include/stdlib.h:579: error: syntax error before "__THROW"
/usr/include/stdlib.h:586: error: syntax error before "__THROW"
/usr/include/stdlib.h:589: error: syntax error before "__THROW"
/usr/include/stdlib.h:596: error: syntax error before "__THROW"
/usr/include/stdlib.h:606: error: syntax error before "__THROW"
/usr/include/stdlib.h:620: error: syntax error before "__nonnull"
/usr/include/stdlib.h:642: error: syntax error before "__nonnull"
/usr/include/stdlib.h:663: error: syntax error before "__THROW"
/usr/include/stdlib.h:717: error: syntax error before "extern"
/usr/include/stdlib.h:717: error: syntax error before "__wur"
/usr/include/stdlib.h:734: error: syntax error before "extern"
/usr/include/stdlib.h:735: error: syntax error before "__THROW"
/usr/include/stdlib.h:755: error: syntax error before "extern"
/usr/include/stdlib.h:757: error: syntax error before "__nonnull"
/usr/include/stdlib.h:762: error: syntax error before "__nonnull"
/usr/include/stdlib.h:771: error: syntax error before "__THROW"
/usr/include/stdlib.h:771: error: syntax error before "__wur"
/usr/include/stdlib.h:772: error: syntax error before "__THROW"
/usr/include/stdlib.h:772: error: syntax error before "__wur"
/usr/include/stdlib.h:777: error: syntax error before "__THROW"
/usr/include/stdlib.h:777: error: syntax error before "__wur"
/usr/include/stdlib.h:785: error: syntax error before "extern"
/usr/include/stdlib.h:786: error: syntax error before "__THROW"
/usr/include/stdlib.h:786: error: syntax error before "__wur"
/usr/include/stdlib.h:788: error: syntax error before "__THROW"
/usr/include/stdlib.h:788: error: syntax error before "__wur"
/usr/include/stdlib.h:795: error: syntax error before "__THROW"
/usr/include/stdlib.h:795: error: syntax error before "__wur"
/usr/include/stdlib.h:808: error: syntax error before "extern"
/usr/include/stdlib.h:809: error: syntax error before "__THROW"
/usr/include/stdlib.h:815: error: syntax error before "__THROW"
/usr/include/stdlib.h:821: error: syntax error before "__THROW"
/usr/include/stdlib.h:828: error: syntax error before "__THROW"
/usr/include/stdlib.h:831: error: syntax error before "__THROW"
/usr/include/stdlib.h:833: error: syntax error before "__THROW"
/usr/include/stdlib.h:840: error: syntax error before "__THROW"
/usr/include/stdlib.h:843: error: syntax error before "__THROW"
/usr/include/stdlib.h:848: error: syntax error before "__THROW"
/usr/include/stdlib.h:852: error: syntax error before "__THROW"
/usr/include/stdlib.h:860: error: syntax error before "extern"
/usr/include/stdlib.h:860: error: syntax error before "__THROW"
/usr/include/stdlib.h:864: error: syntax error before "__THROW"
/usr/include/stdlib.h:867: error: syntax error before "__THROW"
/usr/include/stdlib.h:872: error: syntax error before "__THROW"
/usr/include/stdlib.h:876: error: syntax error before "__THROW"
/usr/include/stdlib.h:885: error: syntax error before "extern"
/usr/include/stdlib.h:885: error: syntax error before "__THROW"
/usr/include/stdlib.h:899: error: syntax error before "__THROW"
/usr/include/stdlib.h:949: error: syntax error before "__THROW"
m.c:2: error: syntax error before "int"
```

---

### Post by oldos2er on 2012-06-25
Moved to Programming Talk.

---

### Post by trent.josephsen on 2012-06-26
Never seen messages like this before, but I'd guess it's because your headers make use of features that have changed in their implementation since 3.3. You need... probably an equally old libc and maybe some other packages.

Why do you need such an old version of gcc?

---

### Post by MKam on 2012-06-26
Because I need it to compile a gcc cross-compiler. Exactly, as you mentioned, I think I should use older header package. But, I don't know, how I can force the gcc-3.3 to use the older header package. Additionally, I don't know how I can install the older header package.

---

