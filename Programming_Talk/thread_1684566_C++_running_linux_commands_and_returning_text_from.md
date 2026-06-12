---
title: "C++ running linux commands and returning text from them"
date: 2011-02-09
forum: Programming Talk
---

### Post by barisurum on 2011-02-09
Hi!

For a program I develop, I need to fetch some system info. Such as kernel, glibc, libstdc++ versions etc. Can you please tell me how it is achieved? The function must run for example "uname -m" and return a char* or string from it. Thanks.

---

### Post by Simian Man on 2011-02-09
That's not directly possible, but you can do this:

```

system("uname -m > /tmp/systeminfo");

/* open file and read it */

```

What are you trying to do though?  This is a recipe for *extremely* brittle and non-portable code.

---

### Post by MadCow108 on 2011-02-09
if you only need uname output you can use the linux C api to get the same
see man 2 uname
```

#include <stdio.h>
#include <sys/utsname.h>

int main(int argc, const char *argv[])
{
  struct utsname buf;
  if (uname(&buf) == 0) {
    printf("%s\n", buf.machine);
  }
}

```

for other stuff (like number of processors etc) you can use sysconf, sysinfo or /proc/sys.

you can also use the uname executable but it requires a bit more work than in higher level languages.
here the possibilities to do it in unix are listed:
[http://beej.us/guide/bgipc/output/html/multipage/index.html](http://beej.us/guide/bgipc/output/html/multipage/index.html)
the simplest way is probably popen

---

### Post by Tony Flury on 2011-02-09
my advice would be - if you think you need to run a linux command - actually get the source code of the command you need to run - and see what it actually does - you might be able to re-use the code - or link to a module - rather than going through the overhead of creating a new process etc.

---

### Post by tCarls on 2011-02-09
You can use popen().

```

char buf[1024];
FILE *fp = popen("ls", "r");
while (fgets(buf, 1024, fp)) {
        printf("%s", buf);
}
fclose(fp);

```

---

### Post by barisurum on 2011-02-09
Thanks tCarls and all the others. Which library do we include to use popen()? And what does "r" mean in this line:

```
FILE *fp = popen("ls", "r");
```

---

### Post by barisurum on 2011-02-09
OK not needed thanks everybody. A little googling enlightened me. popen() is a very efficient and easy way of doing it.

---

