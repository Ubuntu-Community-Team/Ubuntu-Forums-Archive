---
title: "Creating a folder if it doesn't exists in C, with fopen? How?"
date: 2008-12-07
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-12-07
So how to do this? fopen doesn't do it automatically, it just returns NULL if folder doesn't exists.

I'm stuck. Nothing with google. And any of my C books don't help it.

---

### Post by WW on 2008-12-07
You can use the **stat** library function get information about a file or directory, and the **mkdir** library function to create a directory.  Here's an example you can experiment with:

stat_test.c
```

#include <sys/types.h>
#include <sys/stat.h>
#include <errno.h>
#include <stdio.h>

extern int errno;

int main()
    {
    int e;
    struct stat sb;
    char *name = "tmp999";

    e = stat(name, &sb);
    printf("e=%d  errno=%d\n",e,errno);
    if (e == 0)
        {
        if (sb.st_mode & S_IFDIR)
            printf("%s is a directory.\n",name);
        if (sb.st_mode & S_IFREG)
            printf("%s is a regular file.\n",name);
        // etc.
        }
    else
        {
        printf("stat failed.\n");
        if (errno = ENOENT)
            {
            printf("The directory does not exist. Creating new directory...\n");
            // Add more flags to the mode if necessary.
            e = mkdir(name, S_IRWXU);
            if (e != 0)
                {
                printf("mkdir failed; errno=%d\n",errno);
                }
            else
                {
                printf("created the directory %s\n",name);
                }
            }
        }
    return 0;
    }

```

Compile and run:
```

$ gcc stat_test.c
$ ./stat_test 
e=-1  errno=2
stat failed.
The directory does not exist. Creating new directory...
created the directory tmp999
$ ./stat_test 
e=0  errno=0
tmp999 is a directory.
$ 

```

---

### Post by wmcbrine on 2008-12-07
BTW, one reason this might not show up in a general C book is that, unlike fopen(), it's not part of ANSI standard C -- mkdir() is POSIX-specific. Just something to be aware of if portability is an issue. (There is no ANSI way to create directories.)

---

