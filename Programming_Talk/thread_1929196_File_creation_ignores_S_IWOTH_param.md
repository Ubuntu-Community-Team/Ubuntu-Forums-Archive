---
title: "File creation ignores S_IWOTH param"
date: 2012-02-21
forum: Programming Talk
---

### Post by t1497f35 on 2012-02-21
Hi,
Any ideas why?

The source code below creates a program which I use (for testing purposes) to copy a file "Makefile" to "Makefile2", and I get (ls -ls):
```

8 -rw-rw-r-- 1 fox fox  4845 2012-02-20 01:22 Makefile
8 -rw-rw-r-- 1 fox fox  4845 2012-02-21 20:55 Makefile2

```

So, S_IWOTH was ignored.

File copy.c:
[PHP]
#include <sys/stat.h>
#include <fcntl.h>
#include <stdlib.h>
#include <unistd.h>
#include <stdio.h>

#define BUF_SIZE 1024

int main(int argc, char *argv[]) {
    int inputFd, outputFd, openFlags;
    mode_t filePerms;
    ssize_t numRead;
    char buf[BUF_SIZE];
    
    if(argc != 3) {
        printf("%s old-file new-file\n", argv[0]);
        return EXIT_FAILURE;
    }
    
    inputFd = open(argv[1], O_RDONLY);
    if(inputFd == -1) {
        printf("Error opening file %s", argv[1]);
        return EXIT_FAILURE;
    }
    
    openFlags = O_CREAT | O_WRONLY | O_TRUNC;
    filePerms = S_IRUSR | S_IWUSR | S_IRGRP | S_IWGRP | S_IROTH | S_IWOTH;
    
    outputFd = open(argv[2], openFlags, filePerms);
    if(outputFd == -1) {
        printf("Error opening file %s\n", argv[2]);
        return EXIT_FAILURE;
    }
    
    while( (numRead = read(inputFd, buf, BUF_SIZE)) > 0) {
        if(write(outputFd, buf, numRead) != numRead) {
            printf("Couldn't write whole buffer\n");
            break;
        }
    }
    
    if(close(inputFd) == -1) {
        printf("close input\n");
        return EXIT_FAILURE;
    }
    
    if(close(outputFd) == -1) {
        printf("close output\n");
        return EXIT_FAILURE;
    }
    
    if(numRead == -1) {
        return EXIT_FAILURE;
    }
    
    exit(EXIT_SUCCESS);
}
[/PHP]

---

### Post by Bachstelze on 2012-02-21
For a permission bit to be set on a file at creation, it must both be specified in open() and NOT be forbidden by the umask. In your case, write-by-others is forbidden by the umask. See [font=monospace]man umask[/font].

*EDIT:* Also, nitpicking but for buffers that contain arbitrary data, it is better to declare them as unsigned char[] rather than just char[], so that signed integer arithmetic won't stab you in the back later.

---

### Post by t1497f35 on 2012-02-21
Thanks a lot

EDIT: and thanks for the unsigned char remark, though I'm not sure how exactly an arithmetic issue might arise in the case above.

---

