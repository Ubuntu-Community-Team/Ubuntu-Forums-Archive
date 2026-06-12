---
title: "execinfo.h under window"
date: 2010-11-03
forum: Programming Talk
---

### Post by erotavlas on 2010-11-03
Hi,

I need to use a source code that contains the execinfo.h header file. I'm under indows 7 x64 with netbeans ide 6.9.1 and cygwin 1.7.7. Is there a way to include the header execinfo.h?

Thank

---

### Post by dwhitney67 on 2010-11-03
```

/* for a local project header */
#include "execinfo.h"

/* or if it is a library */
#include <execinfo.h>

```

---

### Post by erotavlas on 2010-11-03
> **dwhitney67 said:**
> ```

/* for a local project header */
#include "execinfo.h"

/* or if it is a library */
#include <execinfo.h>

```


I have tried it, but it doesn't work. ](*,)

---

### Post by dwhitney67 on 2010-11-03
That's because you probably need to tell GCC where to find the header file.  Since you did not provide the magical information (ie where the header file is located) in your first post, I was not sure how to help you.

Nevertheless, what you are probably missing is a specification where the header file lives.  NetBeans is an IDE, and I personally hate them.  So wrt NetBeans, you are on your own unless someone can chime in with the help you require.  With GCC, one uses the -I (uppercase eye) option

---

### Post by erotavlas on 2010-11-03
> **dwhitney67 said:**
> That's because you probably need to tell GCC where to find the header file.  Since you did not provide the magical information (ie where the header file is located) in your first post, I was not sure how to help you.

Nevertheless, what you are probably missing is a specification where the header file lives.  NetBeans is an IDE, and I personally hate them.  So wrt NetBeans, you are on your own unless someone can chime in with the help you require.  With GCC, one uses the -I (uppercase eye) option


Sorry, perhaps I wasn't quite clear. Under windows with cygwin where can I find execinfo.h? Cygwin doesn't contain it?

---

### Post by dwhitney67 on 2010-11-03
Do you expect to find it?

My feelings about IDEs equal that of Windows.  I barely know enough about cygwin, but if I recall, you can open a terminal and search for the header file using "find.
```

find / -name execinfo.h

```

---

### Post by spjackson on 2010-11-03
> **erotavlas said:**
> Sorry, perhaps I wasn't quite clear. Under windows with cygwin where can I find execinfo.h? Cygwin doesn't contain it?
According to this page [http://www.gnu.org/software/hello/manual/gnulib/execinfo_002eh.html](http://www.gnu.org/software/hello/manual/gnulib/execinfo_002eh.html) Cygwin does not have execinfo.h. Note that you would need more than the header file, you would need the associated library too.

---

### Post by erotavlas on 2010-11-03
> **spjackson said:**
> According to this page [http://www.gnu.org/software/hello/manual/gnulib/execinfo_002eh.html](http://www.gnu.org/software/hello/manual/gnulib/execinfo_002eh.html) Cygwin does not have execinfo.h. Note that you would need more than the header file, you would need the associated library too.

Thank you very much. So the better (simple and faster) solution is to use linux?

---

### Post by dwhitney67 on 2010-11-03
> **erotavlas said:**
> Thank you very much. So the better (simple and faster) solution is to use linux?

That is debatable, but you have my vote to use Linux.

---

