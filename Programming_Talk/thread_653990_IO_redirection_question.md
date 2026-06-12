---
title: "I/O redirection question"
date: 2007-12-30
forum: Programming Talk
---

### Post by kvorion on 2007-12-30
I was reading Richard Stevens' book where I found this example to see whether the standard input is capable of seeking.

```

#include "apue.h"

int
main(void)
{
    if (lseek(STDIN_FILENO, 0, SEEK_CUR) == -1)
       printf("cannot seek\n");
    else
       printf("seek OK\n");
    exit(0);
}

```

I understood the code as such, but I did not exactly understand how it is used.

The usage of the program is shown as:

```

$ ./a.out < /etc/motd
   seek OK
   $ cat < /etc/motd | ./a.out
   cannot seek
   $ ./a.out < /var/spool/cron/FIFO
   cannot seek

```

What exactly is happening here?

---

### Post by kvorion on 2007-12-31
Somebody respond please?

---

### Post by samjh on 2007-12-31
From lseek documentation: [http://www.opengroup.org/onlinepubs/000095399/functions/lseek.html](http://www.opengroup.org/onlinepubs/000095399/functions/lseek.html)

Basically, the lseek function returns -1 if a device is unable to perform seek.  If successful, it will return the offset in bytes from beginning of the file.

[FONT="Courier New"]**lseek(STDIN_FILENO, 0, SEEK_CUR)**[/FONT]

STDIN_FILENO is the file number of stdin (others include STDERR_FILENO for stderr and STDOUT_FILENO for stdout).
0 is the specified offset value in bytes.
SEEK_CUR means the file offset shall be set to current offset plus the value of the previous parameter (0).

---

