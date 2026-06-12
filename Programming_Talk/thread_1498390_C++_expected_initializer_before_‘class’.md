---
title: "C++: expected initializer before ‘class’"
date: 2010-05-31
forum: Programming Talk
---

### Post by James78 on 2010-05-31
Hello,

I cannot for the life of me, figure out WHAT the error is! I've checked the code over and over for errors, and cannot find any. If I remove the class from the file it says the error is coming from (parseargs.h), it pops up another error...
With class:
```
/home/user/Projects/rsuploader/src/parseargs.h:21: error: expected initializer before ‘class’
```
With class removed:
```
In file included from /usr/include/c++/4.4/bits/ios_base.h:43,
                 from /usr/include/c++/4.4/ios:43,
                 from /usr/include/c++/4.4/ostream:40,
                 from /usr/include/c++/4.4/iostream:40,
                 from /home/user/Projects/rsuploader/src/main.cpp:29:
```

And here's a zip of my project...

---

### Post by gmargo on 2010-05-31
In functions.h, the printError declaration is missing a semi-colon.

---

### Post by James78 on 2010-05-31
It would be wouldn't it. Thanks. How we even miss such simple things... >.<

---

