---
title: "#pragma diagnostic doesn't work"
date: 2009-03-30
forum: Programming Talk
---

### Post by cb951303 on 2009-03-30
I need to work with a code full of this warning
```

warning: "/*" within comment

```
I don't want to clean all the comments (laziness) so I tried this
[php]
#pragma GCC diagnostic ignored "-Wcomment"
[/php]
but it doesn't seem to turn of those warnings. Am I misinformed or is this a bug?

Thank you

---

### Post by cb951303 on 2009-04-01
I don't know why it didn't work but a simple **-Wno-comment** flag to the compiler line works okay.

---

