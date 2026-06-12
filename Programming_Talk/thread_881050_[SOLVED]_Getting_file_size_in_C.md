---
title: "[SOLVED] Getting file size in C"
date: 2008-08-05
forum: Programming Talk
---

### Post by wtfnomorenames on 2008-08-05
I was wondering if there was any fairly straight-forward way to retrieve the size of a file in C without using any external libraries, using the system() call, or having to open the file and scan it?

Thanks in advance!

---

### Post by Lster on 2008-08-05
Have a look at the example code here:

[http://www.cplusplus.com/reference/clibrary/cstdio/fread.html](http://www.cplusplus.com/reference/clibrary/cstdio/fread.html)

The bit just under:

[PHP]// obtain file size:[/PHP]

:KS

---

### Post by geirha on 2008-08-05
stat is also an option:
[php]
#include <stdio.h>
#include <sys/stat.h>
int main()
{
    struct stat stat_result;
    char filename[]= "test.txt";
    if ( stat(filename, &stat_result) == -1 )
        return 1;
    printf("Size of \"%s\" is %ld bytes\n", filename, stat_result.st_size);
    return 0;
}
[/php]

```

sudo aptitude install manpages-dev
man 2 stat

```

---

### Post by wtfnomorenames on 2008-08-05
Thank you both!

---

### Post by hod139 on 2008-08-05
sys/stat.h is not portable.  Take a look at Boost's filesystem for a portable solution: [http://www.boost.org/doc/libs/1_35_0/libs/filesystem/doc/index.htm](http://www.boost.org/doc/libs/1_35_0/libs/filesystem/doc/index.htm)

---

### Post by slavik on 2008-08-05
> **hod139 said:**
> sys/stat.h is not portable.  Take a look at Boost's filesystem for a portable solution: [http://www.boost.org/doc/libs/1_35_0/libs/filesystem/doc/index.htm](http://www.boost.org/doc/libs/1_35_0/libs/filesystem/doc/index.htm)
boost is an external library, not good enough according to OP's first post.

---

