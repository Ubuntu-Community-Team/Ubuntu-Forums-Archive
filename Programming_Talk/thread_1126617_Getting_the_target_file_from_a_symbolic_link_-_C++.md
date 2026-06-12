---
title: "Getting the target file from a symbolic link - C++"
date: 2009-04-15
forum: Programming Talk
---

### Post by iharrold on 2009-04-15
Question.  

Anyone have an idea, snippet, on how to get the target file of a symbolic linked file into a std::string?

i.e. for timezone I have:
ln -sf /usr/share/zoneinfo/US/Central /usr/share/zoneinfo/localtime

I want to look at the symbolic file "/usr/share/zoneinfo/localtime" and get the target string of "/usr/share/zoneinfo/US/Central"

Any ideas of a library call to do this?

---

### Post by johnl on 2009-04-15
Hi,

Check out 'readlink'.  You should also use stat() (or maybe lstat?) first to make sure that what you are trying to dereference is actually a link.

```

#include <stdlib.h>
#include <stdio.h>
#include <unistd.h>

int main(int argc, char* argv[])
{
    if (argc != 2) {
        printf("usage: %s <link>\n", argv[0]);
        return 0;
    }

    char buf[512];
    int count = readlink(argv[1], buf, sizeof(buf));
    if (count >= 0) {
        buf[count] = '\0';
        printf("%s -> %s\n", argv[1], buf);
    }

    return 0;

}

```

---

### Post by iharrold on 2009-04-16
thank you johnl.

readlink solved my problem.

---

