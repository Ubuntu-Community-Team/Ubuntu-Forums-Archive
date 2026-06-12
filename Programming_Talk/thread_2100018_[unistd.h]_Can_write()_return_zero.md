---
title: "[unistd.h] Can write() return zero?"
date: 2012-12-31
forum: Programming Talk
---

### Post by bird1500 on 2012-12-31
Hi,
[PHP]ssize_t write(int filedes, const void *buf, size_t nbyte);[/PHP]Suppose filedes is OK, buf isn't NULL and nbyte > 0.

If read() returns zero it means EOF, not an error.
But can write() return zero? If it can what does it mean? EOF (doesn't make sense), error or something else?

---

### Post by MadCow108 on 2012-12-31
I can imagine it can return zero if the descriptor was opened with O_NONBLOCK and the sink is temporarily unavailable.
I don't think there is any special meaning, it just means you need to try again until you have written what you need to (or an error occurs).

---

### Post by Bachstelze on 2012-12-31
First, you should be careful about misusing the term "EOF". In C, EOF refers to something very specific: the value returned by some I/O functions in some specific circumstances. You should not use it as a synonym for "end of file" (notice that the manual pages do not).

About your question the manual page of write() is very clear: a return value of zero means nothing was written and no error occurred (if there is an error, -1 is returned). This means that normally, it should not happen if you ask to write more than 0 bytes, but as a precaution I would still consider that case in code. What you want to do depends on what the code is supposed to be doing, you could either ignore it, or throw a "This should not happen!" message. There is no need to check for zero specifically, though, it is sufficient to check that the resurned value matches what you asked.

> **MadCow108 said:**
> I can imagine it can return zero if the descriptor was opened with O_NONBLOCK and the sink is temporarily unavailable.

No, then it is an error (returns -1 and sets errno to EWOULDBLOCK or EAGAIN).

---

### Post by Bachstelze on 2012-12-31
P.S.: As the name "unistd.h" suggests, write() is only POSIX-standard, not C-standard. Prefer fwrite() if possible.

---

### Post by bird1500 on 2012-12-31
Thanks, so I decided to ignore the zero return value in my writeAll method and continue writing as if nothing happened, just like with the EINTR errno.

Here's the method of the "io" class I came up with which writes to a socket or file descriptor returning the errno value or how many bytes were written.

[PHP]
ssize_t
io::writeAll(int fd, void *buffer, const ssize_t toWrite) {
    char *buf = (char*)buffer;
    ssize_t written = 0, chunk;
    
    while(written < toWrite) {
        chunk = write(fd, buf+written, toWrite-written);
        
        if(chunk == -1) {
            if(errno == EINTR) {
                continue;//interrupted, nothing happened, restart
            }
            return errno;
        }
        
        written += chunk;
    }
    
    return written;
}
[/PHP]In case anyone wonders, here's the readAll method which explicitly deals with zero:
[PHP]
ssize_t
io::readAll(int fd, void *buffer, const ssize_t toRead) {
    char *buf = (char*)buffer;
    ssize_t totalRead = 0, chunk;
    
    while(totalRead < toRead) {
        chunk = read(fd, buf+totalRead, toRead-totalRead);
        
        if(chunk == 0) {//EOF
            return totalRead;
        }
        
        if(chunk == -1) {
            if(errno == EINTR) {//interrupted, restart
                continue;
            } else {
                return errno;
            }
        }
        
        totalRead += chunk;
    }
    
    return totalRead;
}
[/PHP]

---

### Post by Bachstelze on 2012-12-31
With the caveat that I do not know what is kosher in C++, that's essentially how I would do it in C (assuming that for some reason I had to use read()/write() instead of fread()/fwrite()).

---

