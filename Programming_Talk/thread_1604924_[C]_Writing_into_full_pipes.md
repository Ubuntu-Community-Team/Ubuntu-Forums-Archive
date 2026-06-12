---
title: "[C] Writing into full pipes"
date: 2010-10-24
forum: Programming Talk
---

### Post by KdotJ on 2010-10-24
Hey guys, I'm new to C programming and playing around with a few things, I also have a book which I'm teaching myself from. I have been looking a system calls (such as fork(), pipe() etc).

Now I understand that a pipe has a buffer capacity and you cannot write into a full pipe... So I have been looking at way to catch this, but I'm not having much luck.

Say I have a pipe that is never read from, how to I check I can't write to it anymore? I would have thought the code below would work but the program just hangs. I know that write() returns the number of bytes written (Am I correct?) and one of the parameters is the bytes to be written (Am I correct again?), so therefor, if the return value for write() is not equal to the size of the expected bytes to be written, then the following loop should break...

```

while (write(descriptor, (char *)&i, sizeof(i)) == sizeof(i)) {
    /* do stuff here */		
}

``` 

(take all other variables as being valid here). Am I missing something simple here? does the program just hang waiting for the pipe to have space?

I also realise I am completely wrong. So any help is appreciated.

---

### Post by jpkotta on 2010-10-24
> **KdotJ said:**
> Hey guys, I'm new to C programming and playing around with a few things, I also have a book which I'm teaching myself from. I have been looking a system calls (such as fork(), pipe() etc).

Now I understand that a pipe has a buffer capacity and you cannot write into a full pipe... So I have been looking at way to catch this, but I'm not having much luck.

Say I have a pipe that is never read from, how to I check I can't write to it anymore? I would have thought the code below would work but the program just hangs. I know that write() returns the number of bytes written (Am I correct?) and one of the parameters is the bytes to be written (Am I correct again?), so therefor, if the return value for write() is not equal to the size of the expected bytes to be written, then the following loop should break...

```

while (write(descriptor, (char *)&i, sizeof(i)) == sizeof(i)) {
    /* do stuff here */		
}

``` 

(take all other variables as being valid here). Am I missing something simple here? does the program just hang waiting for the pipe to have space?

I also realise I am completely wrong. So any help is appreciated.

When creating/opening the pipe, use the O_NONBLOCK flag.  Then write() will return with an error instead of just sitting there.

```
apt-get install manpages-dev
man 7 pipe
```

---

### Post by Lux Perpetua on 2010-10-24
You can use poll() to check if a write to a given file descriptor would block. It works for pipes. Here's an example: ```
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <poll.h>

int is_writeable(int fd) {
    struct pollfd p;
    int ret;

    p.fd = fd;
    p.events = POLLOUT;

    ret = poll(&p, 1, 0);

    if (ret < 0) {
        /* We could check the value of errno here
         * to find out why it failed.
         */
        fprintf(stderr, "poll failed\n");
        exit(EXIT_FAILURE);
    }

    return p.revents & POLLOUT;
}

int main(void) {
    int pipefds[2];
    int chars = 0;

    char c;

    if (pipe(pipefds)) {
        fprintf(stderr, "pipe failed\n");
        exit(EXIT_FAILURE);
    }

    while (is_writeable(pipefds[1])) {
        write(pipefds[1], &c, 1);
        ++chars;
    }

    printf("%d bytes written before poll returned `false'.\n", chars);
    getc(stdin);

    /* The following loop confirms that we can write a further
     * 4095 bytes after poll returns false (I guess because we can't
     * write a full 4096 bytes (= PAGE_SIZE? PIPE_BUF?))
     */
    
    chars = 0;

    while (1) {
        write(pipefds[1], &c, 1);
        ++chars;
        printf("%d\t", chars);
        fflush(stdout);
    }

    exit(EXIT_FAILURE);
}
```I don't understand it completely, but the data granularity of poll() on Linux (and select()) seems to be larger than 1 byte (4096 bytes, to be exact). Unfortunately, I can't find any documentation about this. The code above illustrates the granularity issue by trying to write to the pipe even after poll() says we can't. When I run the code on my Arch Linux machine, I get 61441 bytes from the first loop and 4095 bytes from the second loop. (Note that 61441 + 4095 = 65536, the full Linux pipe capacity.) I get very different results on FreeBSD and SunOS.

---

