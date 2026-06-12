---
title: "write a system log for admins with C"
date: 2012-02-22
forum: Programming Talk
---

### Post by conradin on 2012-02-22
Hi All,
I want to write errors in my program to the local 7 of syslog.
Im reading:
[http://www.linuxselfhelp.com/gnu/glibc/html_chapter/libc_18.html](http://www.linuxselfhelp.com/gnu/glibc/html_chapter/libc_18.html)
but what I really need is some specific examples.
I'm not really sure how writing to a syslog is different than writing to a file?

---

### Post by gateway67 on 2012-02-22
> **conradin said:**
> Hi All,
I want to write errors in my program to the local 7 of syslog.
Im reading:
[http://www.linuxselfhelp.com/gnu/glibc/html_chapter/libc_18.html](http://www.linuxselfhelp.com/gnu/glibc/html_chapter/libc_18.html)
but what I really need is some specific examples.
I'm not really sure how writing to a syslog is different than writing to a file?
Surely you were able to reference the examples given in the link you provided?

Here's a simple example:
```

#include <syslog.h>

int main()
{
    openlog("foo_app", LOG_CONS | LOG_PID | LOG_NDELAY, LOG_LOCAL7);

    syslog(LOG_INFO, "Using syslog is easy.");

    closelog();

    return 0;
}

```
The string passed to syslog() can contain any message you desire.

---

