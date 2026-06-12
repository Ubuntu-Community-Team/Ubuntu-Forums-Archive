---
title: "Strange Timings"
date: 2008-11-29
forum: Programming Talk
---

### Post by DBQ on 2008-11-29
I am timing a single threaded program which I wrote (and its pieces of code). It runs on a hyper threaded (not dual core) Pentium 4 processor.

I have noticed that in some instances the cpu time exceeds the wall-clock time. What could this be?  It does not seem to me that in this case the classical explanation of "program runs on a different processors simultaneously" would suffice (program is single threaded). Any ideas?

Thank You.

---

### Post by slavik on 2008-11-29
that would be the only reason I can think of.

---

### Post by Zugzwang on 2008-11-29
Maybe you are using libraries which make use of multi-threading?

---

### Post by DBQ on 2008-11-29
> **Zugzwang said:**
> Maybe you are using libraries which make use of multi-threading?

I do not think so.  Here are the list of libraries I am using:

```

#include <iterator>
#include <vector>
#include <map>
#include <algorithm>
#include <features.h>
#include <stdio.h>
#include <stdlib.h>
#include <sys/time.h>
#include <sys/times.h>
#include <time.h>

```

---

### Post by DBQ on 2008-11-29
Here is another interesting observation. On the same machine I did this:  I simply typed the following at the bash prompt:

```

$ time ls

```

(ie time the ls command).  And here are the results I got.  Again cpu time is higher then the wall clock time:

```

real	0m0.007s
user	0m0.008s
sys	0m0.004s

```

---

