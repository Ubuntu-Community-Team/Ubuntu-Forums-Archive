---
title: "system call and file descriptor"
date: 2008-08-18
forum: Programming Talk
---

### Post by cmpn76 on 2008-08-18
Hi guys,

I'm trying to start a java from from C code. I'm using the system() call for doing that.

...
system("/home/marco/runjava.sh");
...

The java process starts correctly but it inherit all the file descriptor that I've opened in the C code before calling system().

Do you know if there is a way to avoid this behaviour?

Thanks in advance

---

### Post by amo-ej1 on 2008-08-18
Hmmmz, the only quick and dirty I can think of right now is first call fork(), in the child process run a for loop and call close on the first 256 integers then call execve() and friends to launch your process. 

But there must be a cleaner solutuion.

---

### Post by cmpn76 on 2008-08-18
> **amo-ej1 said:**
> Hmmmz, the only quick and dirty I can think of right now is first call fork(), in the child process run a for loop and call close on the first 256 integers then call execve() and friends to launch your process. 

But there must be a cleaner solutuion.

It seems to work for me but it create a very annoying side effect. The child process get the control of the stdin on the terminal so my app act like I was running it in background.

---

### Post by kpatz on 2008-08-18
> **cmpn76 said:**
> It seems to work for me but it create a very annoying side effect. The child process get the control of the stdin on the terminal so my app act like I was running it in background.(a) make sure it's the child closing the file descriptors and not the parent.  That is, the fork() that returns 0 should close the descriptors.

(b) There's no need to close stdin, stdout, or stderr (0, 1, and 2).

---

### Post by cmpn76 on 2008-08-18
> **kpatz said:**
> (a) make sure it's the child closing the file descriptors and not the parent.  That is, the fork() that returns 0 should close the descriptors.

(b) There's no need to close stdin, stdout, or stderr (0, 1, and 2).

The "for" that do the close was in the child code. 
I fixed this problem starting the java process from the parent and leaving the child carrying on with the execution of the C code. It is not really nice because now I'm using a sleep call for waiting that the java process start but it works.

---

### Post by kpatz on 2008-08-18
Are your file descriptors opened with open() or fopen()?

If they're fopened, it's better to use fclose() to close them.

This code should give you an idea:

```

#include <stdio.h>
#include <unistd.h>

int main()
{
  ...
  // Here's the files you opened...
  FILE *f1 = fopen(...);
  FILE *f2 = fopen(...);
  ...
  // Now we want to call the java app.
  switch(fork())
  {
    case -1:  // fork failed
       fprintf(stderr, "fork() failed\n");
       return 1;
    case 0:  // is the child
       fclose(f1);
       fclose(f2);
       execl("/home/marco/runjava.sh", "/home/marco/runjava.sh");
       fprintf(stderr, "execl() failed\n");
       return 1;  // shouldn't hit this unless exec failed
  }
  // If we get here, we're the parent.
  ... do whatever can be done while java runs ...
     wait();  // wait for java to finish
  // At this point, the child process calling java has completed,
  // and our file descriptors should still be open.
  ...
  // Close files.
  fclose(f1);
  fclose(f2);
  return 0;
}

```

---

### Post by stroyan on 2008-08-18
Another option is to use the close-on-exec feature.
That allows you to set the option on each file descriptor that you
want to close.  It can be done in advance when you are opening files
instead of needing to decide which ones to close after forking.
```

#include <unistd.h>
#include <fcntl.h>

fcntl(fildes, F_SETFL, FD_CLOEXEC);

```

---

