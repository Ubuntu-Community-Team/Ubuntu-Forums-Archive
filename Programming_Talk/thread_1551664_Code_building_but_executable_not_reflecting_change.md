---
title: "Code building but executable not reflecting changes..."
date: 2010-08-12
forum: Programming Talk
---

### Post by ThesaurusRex on 2010-08-12
I've been trying to muck around with the gedit source code recently. I've successfully observed simple changes to the main source file, but whenever I modify other files they don't seem to actually be reflected in the executable. For instance, I type:
```
make
``` and all the files I modified show up as recompiling. But then I run the executable and I don't notice anything different. I've commented out the interior of functions, but then the parts of gedit which relies on them still works. Is there something I'm doing wrong?

---

### Post by cliffdodger on 2010-08-12
After that you probably need to try a "make install" in order to make your changes go live.

---

