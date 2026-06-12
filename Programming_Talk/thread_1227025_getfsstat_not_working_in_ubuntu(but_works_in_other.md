---
title: "getfsstat not working in ubuntu(but works in other os)"
date: 2009-07-30
forum: Programming Talk
---

### Post by AndreiMe on 2009-07-30
Hello... this is a new one:
this code works in FreeBSD, Solaris, Mac OS X and even RHEL Linux.
On this page [http://manpages.ubuntu.com/manpages/jaunty/man2/getfsstat.2freebsd.html](http://manpages.ubuntu.com/manpages/jaunty/man2/getfsstat.2freebsd.html) they say that getfsstat is a standard c library. I researched it a bit and it turns out that it should work in ubuntu. 
It is very important to the project that i am working on to get getfsstat to work properly, and i think the only problem with this example to run well is the fact that somewhere ubuntu can't find, or lacks a proper library.
Thank you.

```

#include <sys/param.h>
#include <sys/mount.h>
 
#include <errno.h>
#include <stdio.h>
#include <stdlib.h>
 
#define MAX_FS 128
 
void
print_mounted_fs(void)
{
        struct statfs buf[MAX_FS];
        int fs_count;
        int i;
 
        fs_count = getfsstat(NULL, 0, MNT_NOWAIT);
        if (fs_count == -1) {
                fprintf(stderr, "Error: %d\n", errno);
                exit(1);
        }
        printf("%d file systems found.", fs_count);
 
        getfsstat(buf, fs_count * sizeof(buf[0]), MNT_NOWAIT);
 
        printf("\n");
        for (i = 0; i < fs_count; ++i) {
                printf("%s\n", buf[i].f_mntonname);
        }
}
 
int
main(void)
{
        print_mounted_fs();
 
        return 0;
}

```

---

### Post by Zugzwang on 2009-07-30
> **AndreiMe said:**
> 
On this page [http://manpages.ubuntu.com/manpages/jaunty/man2/getfsstat.2freebsd.html](http://manpages.ubuntu.com/manpages/jaunty/man2/getfsstat.2freebsd.html) they say that getfsstat is a standard c library. 

No, certainly not as this is a system-type dependent function. In fact, the manual page you refer to just states that it appeared in BSD 4.4 first. Note that this is a manual page imported from FreeBSD which is packaged for Ubuntu for convenience, but does not reflect Ubuntu's actual behaviour.

If you want to use Linux-compatible functions, have a look here, maybe that's useful for you:
[http://linux.die.net/man/2/statvfs](http://linux.die.net/man/2/statvfs)

---

### Post by AndreiMe on 2009-07-30
it's very strange because it is considered standard library in c.... oh well, i'll look into it. do you have something like an example you can share?

---

### Post by Zugzwang on 2009-07-30
> **AndreiMe said:**
> do you have something like an example you can share?

Erm, no, sorry, I just looked it up. Note that the "standard C library" is not necessarily the same under FreeBSD and Linux (in Linux, the GNU LibC is used). Watch out for functions that are part of the POSIX standard if you want compatibility. However, for such a system-dependent purpose I doubt that there are any.

---

### Post by AndreiMe on 2009-07-30
i'm making an app in qt cross platform and i need to have a way to show get the mounted partitions.
so is there something like
ifndef WIN32
endif
but for bsd/linux?

---

### Post by Zugzwang on 2009-07-30
> **AndreiMe said:**
> i'm making an app in qt cross platform and i need to have a way to show get the mounted partitions.
so is there something like
ifndef WIN32
endif
but for bsd/linux?

I'm sure there is - Look up the GNU compiler manual for details. You can however always use different Makefiles for the individual platforms to circumvent the problem.

For finding out how to get your data in Linux, you might want to have a look at the source code of the "df" utility which is part of the "coreutils" package: [http://packages.ubuntu.com/jaunty/coreutils](http://packages.ubuntu.com/jaunty/coreutils)

It will however be simpler just to parse the output of that program for your purpose.

---

### Post by AndreiMe on 2009-07-30
thank you for the swift help, it is really helpful. 
now if you can(or someone else) help me figure this out it would be great.
here's what i have:
```

#ifndef WIN32
void
fileHandler::print_mounted_fs(void)
{
     struct statfs FSBuf;
        int fs_count;
       fs_count = statfs("/", &FSBuf);
       qDebug() << "file systems found: " <<fs_count;//this outputs in 
                                                   //the debug view
   
}
#endif
```
this returns 0. i think it is doing just what it should do, because the root is 1 filesystem and so on. but my quest is to find all mounted media, in a similar way to how the function i supplied up there does inside the unix platform.
i know that the two functions are different and behave different but there has to be a way in which i can get all the mounted drives.
and for the other thing... i am using the ifndef win32 but due to the fact that it should work on multiple platforms i have to find a way in which to separate the platforms.
thank you.

---

### Post by Zugzwang on 2009-07-30
> **AndreiMe said:**
> ... but there has to be a way in which i can get all the mounted drives.

As already stated, look into the source code of the "df" tool which does precisely that.

> **AndreiMe said:**
> 
and for the other thing... i am using the ifndef win32 but due to the fact that it should work on multiple platforms i have to find a way in which to separate the platforms.
thank you.

As already stated, use different Makefiles, i.e., put the platform-dependent code into separate source files and use different Makefiles to include only the code your need for the respective platform.

---

