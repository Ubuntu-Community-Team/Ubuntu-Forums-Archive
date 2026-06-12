---
title: "[SOLVED] warning: implicit declaration of function"
date: 2007-09-06
forum: Programming Talk
---

### Post by jordanmthomas on 2007-09-06
I'm writing a shell for a school assignment in c, and it has to compile without any warnings.  To get the current directory, I am using get_current_dir_name.

Here's what I think is the relevant code (snipped up for clarity):
```
#include <unistd.h>
int main(int argc, char** argv)
{
     char* cwd = (char*)get_current_dir_name();
}

```
When I compile, this warning is given:
```

jshell.c:19: warning: implicit declaration of function ‘get_current_dir_name’
```

I don't understand why this is happening because according to **man get_current_dir_name**, I should just have to include unistd.h

```
man get_current_dir_name
...SYNOPSIS
       #include <unistd.h>
...
...
      char *get_current_dir_name(void);

```

The code works fine, but I don't know how to get rid of the warning.  Any help is appreciated.  I'm sure it's something stupid on my part, but I can't figure it out.

Thanks in advance.

**edit** This warning doesn't come up if I don't use -Wall when compiling, but I am required to use it  :).
**edit2**  Using other functions from unistd.h does not result in the warning.

---

### Post by Wybiral on 2007-09-06
```

#define _GNU_SOURCE
#include <unistd.h>
int main(int argc, char** argv)
{
     char* cwd = (char*)get_current_dir_name();
}

```

Man page: "get_current_dir_name(), which is only prototyped if _GNU_SOURCE is defined"

You should probably stick with "getcwd" though.

```

#include <stdio.h>
#include <unistd.h>

int main(int argc, char** argv)
{
    char my_cwd[1024];
    getcwd(my_cwd, 1024);
    printf("%s\n", my_cwd);
    return 0;
}

```

---

### Post by jordanmthomas on 2007-09-06
Aha!  Thanks a lot.

---

### Post by jordanmthomas on 2007-09-06
Well, almost got it.  It doesn't say that in my manpage anywhere, but at least I have a hunch.  I'm sure I'll get it figured out now though.

---

### Post by Wybiral on 2007-09-06
> **jordanmthomas said:**
> Well, almost got it.  It doesn't say that in my manpage anywhere, but at least I have a hunch.  I'm sure I'll get it figured out now though.

I read it from: [http://linux.die.net/man/3/get_current_dir_name](http://linux.die.net/man/3/get_current_dir_name) (I thought it was a replica of the normal man pages, must not be).

But like I said, getcwd it more commonly used, so if you can use it, you should.

---

### Post by jordanmthomas on 2007-09-06
OK, I have switched over to getcwd and no more errors.
I guess the warning was related to _GNU_SOURCE like you said, but maybe my system's a little screwy or something.

Thanks again for the help

---

