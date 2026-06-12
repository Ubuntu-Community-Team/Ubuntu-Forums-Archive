---
title: "c statement execution order reversed"
date: 2010-03-12
forum: Programming Talk
---

### Post by Robert Wamg on 2010-03-12
Hello all

I am having problem with the following C code.  The code is extracted from a large program for simplicity.   The code is suppose to print a string of 0s using fprintf() then a string of 1s using write().  Somehow, these two calls are combined by the compiler into one write() and strings are printed  in reverse order.  

```

#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <string.h>
#include <unistd.h>

int main(void) {

    char *fphrase = "00000000000000000000";
    char *phrase = "11111111111111111111 ";
    int fd;

    fd = fileno(stdout);

    //flockfile(stdout);
    fprintf( stdout, "%s", fphrase);
    //funlockfile(stdout);
    write( fd, phrase, strlen(phrase));
    printf("\n");

    return 0;
}

```
 
I tried making the fprintf() atomic using flockfile() and funlockfile() to lock stdout, but it didn't work.  I am working on a Atom330  machine under Ubuntu 9.04.  The gcc version is 4.33 and libc-2.9.s0. 

Please enlighten  me if you know the cause or better the cure of this problem, thank in advance. 

Sincerely yours
Bob

---

### Post by MadCow108 on 2010-03-12
I'm not quite sure why it happens. My guess is that fprintf uses a buffered output and write does not (or not the same buffer)
so when the fprintf call ends stdout may not have decided to flush its buffer before write outputs its information. But this is a pure guess, I don't know much about the internals of write.

Solution:
don't mix write and fprintf (or generally avoid the low level write)
or if not possible
flush the stream after the fprintf using fflush(stdout)

---

### Post by Robert Wamg on 2010-03-12
> **MadCow108 said:**
> I'm not quite sure why it happens. My guess is that fprintf uses a buffered output and write does not (or not the same buffer)
so when the fprintf call ends stdout may not have decided to flush its buffer before write outputs its information. But this is a pure guess, I don't know much about the internals of write.

Solution:
don't mix write and fprintf (or generally avoid the low level write)
or if not possible
flush the stream after the fprintf using fflush(stdout)


As usual, MadCow108 you are amazingly correct.
Thanks a lot. 

Bob

---

### Post by Lux Perpetua on 2010-03-12
> **MadCow108 said:**
> I'm not quite sure why it happens. My guess is that fprintf uses a buffered output and write does not (or not the same buffer)
so when the fprintf call ends stdout may not have decided to flush its buffer before write outputs its information. But this is a pure guess, I don't know much about the internals of write. For the record, your "pure guess" is completely correct.
write() is the most basic way to produce output, and pretty much all other output mechanisms end up calling write() at the end. Here's a good approximation to the implementation of file I/O via stdio.h:

- When a file is opened for output, fopen() allocates a buffer of some size. The "FILE" data structure (whose pointer fopen() returns) contains a pointer to this buffer (among other things). 
- When fprintf(), fwrite(), fputs(), etc. are called, they don't directly output anything to the opened file; they actually copy data into the buffer. When the buffer fills up, write() is called to output the buffer to the file all at once. 
- fflush() can be called to write() whatever is sitting in the buffer.
- fclose() frees the buffer. 

Reading is very similar: fopen() allocates a buffer, and when you try to read from the file, it actually gives you data from the buffer...unless the buffer is empty, in which case it calls read() to fill the buffer first. 

Based on that, I think you can see why mixing calls to stdio.h functions and the I/O system calls might give you strange results. :-)

---

