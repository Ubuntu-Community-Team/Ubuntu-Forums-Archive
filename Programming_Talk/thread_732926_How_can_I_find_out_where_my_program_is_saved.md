---
title: "How can I find out where my program is saved?"
date: 2008-03-23
forum: Programming Talk
---

### Post by fhucho on 2008-03-23
Hi,
in my program I want to find out the directory where it is saved. How can I do that?

Example:
Everything my program does is that it prints the directory where it is saved. If the user saves the program to /usr/bin and then runs /usr/bin/program from his home directory (/home/user), the program should print "/usr/bin".

---

### Post by Can+~ on 2008-03-23
Uhm, language?

If it is python, os.getcwd() returns where the .py was executed ("Current working directory").

---

### Post by fhucho on 2008-03-23
I would appreciate solution for any language, I guess the solution is platform independent...

Current working directory is not always the directory where is the program stored (as I showed on an example).

---

### Post by mike_g on 2008-03-23
Well I think that would depend mainly on what IDE you use. Many IDEs like to make their own workspace to save stuff in. Compilers usually dump their output to the CWD. Mabe there are exceptions to this, but that is what is most common. In short: there is no solution for no language.

---

### Post by stroyan on 2008-03-23
The /proc/self/exe feature of linux can make this fairly easy.

```

#include <limits.h>
#include <errno.h>
#include <string.h>
#include <stdio.h>
#include <unistd.h>

int main(int argc, char *argv)
{
    char buf[_POSIX_PATH_MAX];
    ssize_t result;
    char *last_slash;

    result = readlink("/proc/self/exe", buf, _POSIX_PATH_MAX);
    if (result == -1) {
        perror("readlink");
        return 1;
    }
    last_slash = strrchr(buf,'/');
    *last_slash = 0; /* Drop program name */
    printf("program is in directory %s\n", buf);
    return 0;
}

```

---

### Post by pmasiar on 2008-03-23
sys.argv[0] contains mame of running program, including path

[php]
import sys
print sys.argv[0]
[/php]

---

