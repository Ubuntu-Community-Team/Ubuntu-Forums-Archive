---
title: "stdout redirection"
date: 2008-08-06
forum: Programming Talk
---

### Post by tageiru on 2008-08-06
Alright kids, time to have some fun with glibc! May I direct your attention to exhibit A and B.

```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(int argc, char *argv[])
{
    int outp[2], old;
    char buf[20] = {0};

    old = dup(STDOUT_FILENO);
    if (pipe(outp) != 0) {
	perror("pipe");
	exit(1);
    }
    dup2(outp[1], STDOUT_FILENO);
    close(outp[1]);
    printf("work, please");
    read(outp[0], buf, 20);
    dup2(old, STDOUT_FILENO);
    printf("read: %s\n", buf);
    return 0;
}

```

```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(int argc, char *argv[])
{
    int outp[2], old;
    char buf[20] = {0};

    old = dup(STDOUT_FILENO);
    if (pipe(outp) != 0) {
	perror("pipe");
	exit(1);
    }
    dup2(outp[1], STDOUT_FILENO);
    close(outp[1]);
    write(STDOUT_FILENO, "work, please", 12);
    read(outp[0], buf, 20);
    dup2(old, STDOUT_FILENO);
    printf("read: %s\n", buf);
    return 0;
}

```

Both examples redirects the stdout file descriptor to a pipe, but one uses printf to write data to stdout and the other uses the file descriptor directly. The version that uses printf doesn't write any data to the pipe while the version using write works correctly.

In my mind they should both work, so how have I managed to screw this up?

EDIT: Seems like printf does some zealous buffering preventing the data from reaching the pipe. A fflush() before reading from the pipe solved the issue.

---

### Post by cszikszoy on 2008-08-06
Try using fprintf instead of printf.

---

### Post by tageiru on 2008-08-06
> **cszikszoy said:**
> Try using fprintf instead of printf.
printf(...) is the same as fprintf(stdout, ...) so it would make no difference in this case.

---

