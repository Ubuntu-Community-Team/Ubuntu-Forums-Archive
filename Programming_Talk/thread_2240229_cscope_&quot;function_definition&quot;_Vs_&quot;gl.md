---
title: "cscope &quot;function definition&quot; Vs &quot;global definition&quot;"
date: 2014-08-18
forum: Programming Talk
---

### Post by 3246251196 on 2014-08-18
man cscope:
```

   Requesting the initial search
       After the cross-reference is ready, cscope will display this menu:

       Find this C symbol:
       Find this function definition:
       Find functions called by this function:
       Find functions calling this function:
       Find this text string:
       Change this text string:
       Find this egrep pattern:
       Find this file:
       Find files #including this file:

```

This is the same in the two versions I am testing. 15.5 and 15.7a. Actually, there is no such thing as "Find this function definition", there is only the following menu:

```

Find this C symbol:
Find this global definition:
Find functions called by this function:
Find functions calling this function:
Find this text string:
Change this text string:
Find this egrep pattern:
Find this file:
Find files #including this file:

```

I would very much like to restrict to function definitions when looking at a large code base.

Cheers.

---

### Post by ofnuts on 2014-08-19
You'll notice that "Find this function definition:" is replaced by "Find this global definition". That may not be a coincidence.

---

