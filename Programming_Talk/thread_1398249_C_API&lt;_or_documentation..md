---
title: "C API&lt; or documentation."
date: 2010-02-04
forum: Programming Talk
---

### Post by Bucephalus01 on 2010-02-04
I'm just going out of this book for some linux programming and it used a function called getopt. It said that depending on what version of getopt you have, you may see slightly different output.

so, how do I find the documentation for this function?
I looked it up with man but I think they aren't the same because I think the getopt in man is a function I would use with shell programming. I.e. it's a function I could use on the command line, not a function I would use in c code.

Is there a place I could find documentation for the c language on my computer? Ubuntu.

thanks for reading
Bucephalus01

---

### Post by Zugzwang on 2010-02-04
When looking at the man page of "getopt", notice the following lines:
```

SEE ALSO
       getopt(3), bash(1), tcsh(1).

```

Thus, by running "man 3 getopt", you will see another manpage for "getopt", this time for the C function.

---

