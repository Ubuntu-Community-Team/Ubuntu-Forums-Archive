---
title: "hrtime_t and gethrtime()"
date: 2007-08-08
forum: Programming Talk
---

### Post by Hospadar on 2007-08-08
This is probably pretty simple, I want to use hrtime_t and gethrtime() from sys/time.h

Is there something I need to do to make this work other than #include<sys/time.h> ?
my code is like so:
```

#include<sys/time.h>
<other imports>

using namespace std;
int main() {
  hrtime_t start = gethrtime();
  <the function I want to time>
  hrtime_t stop = gethrtime();
}

```

I'm just getting a general "‘gethrtime’ was not declared in this scope" error when I try to compile this.

Thanks!

---

### Post by Hospadar on 2007-08-08
bump

---

### Post by Nakarian on 2008-09-14
bump again...

---

### Post by dwhitney67 on 2008-09-14
What OS are you using?  I recall using hrtime_t (for declaration) and the gethrtime() system function on Solaris 8.  Undoubtedly it is also available with later releases of Solaris (e.g. 10).

AFAIK, gethrtime() has not made its way onto Linux systems.

---

