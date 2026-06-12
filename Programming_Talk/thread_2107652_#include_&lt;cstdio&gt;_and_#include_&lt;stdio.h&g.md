---
title: "#include &lt;cstdio&gt; and #include &lt;stdio.h&gt; in the SAME FILE?"
date: 2013-01-22
forum: Programming Talk
---

### Post by james_mcl on 2013-01-22
(Cross-posting this to a few different sites - hope that's not in any way a breach of forum etiquette)

I was having a look through the header files for a SAT-solver that I needed to work out how to use, and which for some reason seemed to be using a lot of the C versions of the headers (<stdlib.h> instead of <cstdlib> for instance) alongside C++ headers such as <algorithm>.

Which is how I encountered this:

```

#include <cstdio>
#include <string.h>
#include <stdio.h>

```

Does anyone know of any reason why someone would want to #include both stdio.h and cstdio in the same file? More importantly, are there any potential pitfalls to doing this? If there are, can I just fix them by commenting out the line with stdio.h?

A slightly less important question as well - does anyone know of any reason not to change <string.h> to <cstring> in the above? I can easily go through the file putting std:: before function names and the like.

Many thanks,

James McLaughlin.

---

### Post by spjackson on 2013-01-23
The standard library headers are idempotent, which means that including them many times is equivalent to including them once. This is achieved by wrapping the whole header in #ifndef . cstdio pulls in stdio.h, so including it again is pointless but harmless. Well, there is harm which is: confuse the reader.

I can't think of any reason not to use <cstring> instead of <string.h>, if you are prepared to use std:: when necessary.

---

### Post by dwhitney67 on 2013-01-23
> **spjackson said:**
> 
... if you are prepared to use std:: when necessary.

I agree; it is prudent to use std:: when using certain C functions (I learned this recently when compiling under Solaris.  Linux compiled s/w ok, but Solaris complained).

Do you know how to force the g++ compiler under Linux to generate warnings (or preferably errors) when one does not specify std:: for C functions?

For example, this program compiles fine under Linux, but may not under Solaris:
```

#include <cstring>

int main()
{
    char buf[20];
    strncpy(buf, "Hello World", sizeof(buf));
}

```

---

### Post by spjackson on 2013-01-23
> **dwhitney67 said:**
> Do you know how to force the g++ compiler under Linux to generate warnings (or preferably errors) when one does not specify std:: for C functions?

I'm not aware of such an option, unfortunately, and it's a pain! There may be one, but I don't know it.

See [http://gcc.gnu.org/onlinedocs/libstdc++/manual/bk01pt01ch03s02.html]("http://gcc.gnu.org/onlinedocs/libstdc++/manual/bk01pt01ch03s02.html")
> 
The standard specifies that if one includes the C-style header (<math.h> in this case), the symbols will be available in the global namespace and perhaps in namespace std:: (but this is no longer a firm requirement.) One the other hand, including the C++-style header (<cmath>) guarantees that the entities will be found in namespace std and perhaps in the global namespace.


I don't know whether this mess has been addressed in C++11, and I'm not in a position to check just at the moment.

---

### Post by james_mcl on 2013-01-23
Thanks everyone.

dwhitney and spjackson: I don't have the C++11 standard (too expensive), but I checked the "working draft" (N3337) and it's not good news:

> 
Every C header, each of which has a name of the form name.h, behaves as if each name placed in the standard library namespace by the corresponding cname header is placed within the global namespace scope. It is unspecified whether these names are first declared or defined within namespace scope (3.3.6) of the namespace std and are then injected into the global namespace scope by explicit using-declarations (7.3.3).
(Example: The header <cstdlib> assuredly provides its declarations and definitions within the namespace std. It may also provide these names within the global namespace. The header <stdlib.h> assuredly provides the same declarations and definitions within the global namespace, much as in the C Standard. It may also provide these names within the namespace std. &#8212; end example)


---

