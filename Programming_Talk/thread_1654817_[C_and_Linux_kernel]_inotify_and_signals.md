---
title: "[C and Linux kernel] inotify and signals"
date: 2010-12-28
forum: Programming Talk
---

### Post by Naaktgeboren on 2010-12-28
inotify should support signal-driven notifications. This is what **man 7 inotify** says:
> Since Linux 2.6.25, signal-driven I/O  notification  is  available  for inotify  file  descriptors;  see the discussion of F_SETFL (for setting the O_ASYNC flag), F_SETOWN, and F_SETSIG in fcntl(2).

The following programme should get terminated by SIGIO once */tmp/testfile* is modified. But it doesn't.

```
#include <unistd.h> 
#include <fcntl.h> 
#include <sys/inotify.h> 

int main() { 
int fd = inotify_init(); 
inotify_add_watch(fd, "/tmp/testfile", IN_MODIFY); 
fcntl(fd, F_SETFL, O_ASYNC); 
fcntl(fd, F_SETOWN, getpid()); 
for (;;) sleep(1); 
}
```

However, the very same programme, just using a named pipe instead of an inotify file descriptor, works just fine. As soon as I write into *testfifo*, the programme receives SIGIO and terminates.

```
#include <unistd.h> 
#include <fcntl.h> 

int main() { 
int fd = open("testfifo", O_RDWR); 
fcntl(fd, F_SETFL, O_ASYNC); 
fcntl(fd, F_SETOWN, getpid()); 
for (;;) sleep(1); 
}
```

Anybody knows what's wrong with the first programme? An answer will be much appreciated.

BTW, an identical question was asked [here]("http://translate.google.com/translate?hl=en&sl=auto&tl=en&u=http%3A%2F%2Fubuntu-se.org%2FphpBB3%2Fviewtopic.php%3Ff%3D35%26t%3D47296") a while ago, but no solution was found then.

---

### Post by dwhitney67 on 2010-12-29
I believe the man-page is incorrect (in other words, it has not been properly updated).  From what I have read, the whole purpose of inotify was to do away with signals, which what was offered with dnotify in 2.4.x kernels.

Instead, one can use select() or ioctl() with the file descriptor to determine if there is data to be read.

Here's some additional information:
[http://www.eastman-watch.cn/detailed-explanation-linux26-core-mechanism-in-the-new-file-system/](http://www.eastman-watch.cn/detailed-explanation-linux26-core-mechanism-in-the-new-file-system/)

---

### Post by gmargo on 2010-12-29
From the **open(2)** man page.  It says that O_ASYNC  does not apply to normal files.

> 
       O_ASYNC
                   Enable signal-driven I/O: generate a signal (SIGIO  by  default,
                   but  this  can  be  changed  via  fcntl(2)) when input or output
                   becomes possible on this file descriptor.  This feature is  only
                   available  for  terminals, pseudo-terminals, sockets, and (since
                   Linux 2.6) pipes and FIFOs.  See fcntl(2) for further details.


---

### Post by Naaktgeboren on 2010-12-29
It turns out that this is actually a bug in the kernel. A patch has been prepared, and now it's being tested before getting committed.
Thank you, dwhitney67 and gmargo, for your suggestions.

---

### Post by ataraxic on 2011-03-17
Hi, do you know if the bug was fixed or not?
I did not find any discussion on the kernel mailing list...
Thanks.

---

### Post by ubtroy on 2011-03-30
I would also like to know if this was confirmed as a kernel bug and fixed. I can't find any references via search or on kerneltrap.

---

