---
title: "popen error handling"
date: 2010-06-02
forum: Programming Talk
---

### Post by rockom on 2010-06-02
Hello,

Using Codeblocks and C (not C++).

```
FILE *printer = popen("/usr/bin/lpr -Pthermal", "w");
fprintf(printer, "line one\n");
fprintf(printer, "line two\n");
pclose(printer);
```The above code works fine...fprintf sends whatever I want to a thermal printer.

I'm having a hard time with error handling.  If 'thermal' is not attached, I get the following error:
```
/usr/bin/lpr: The printer or class was not found.
```How can I handle this error?  I suspect I need to use errno but I have not figured out how to implement the check.  I have logging functions and would like to pass the error string to my logger.

Thanks,
-Rocko

---

### Post by soltanis on 2010-06-02
From what I understand of the GNU libc version of popen, you cannot open a bi-directional pipe to a process. Since the process isn't executing in the same memory space as your program, that program won't set errno or signal errors to you in any way that you could capture them.

However, **pclose(3)** returns the exit value of the process that you were running. Non-zero exit processes are typical of programs to signal error conditions on exit, and some programs are even nice enough to signal to you what the error was based on the exit value.

The other way you could do this is to communicate bi-directionally with the process:

First, use **pipe(2)** to create two pipes, one for sending data to lpr, the other for reading back from it.
Then, use **fork(2)** to create a child process.
In the child process, use **dup2(2)** to re-open fd 0 (stdin) as the read end of the pipe (the one you read from the parent process with). Use it again to re-open fd 1 or 2 (stdout or stderr) as the write end of the pipe (which writes back to the parent process).
Finally, use an **exec(3)** function to replace your process image with lpr.

This takes advantage of the fact that under Unix-like systems, after you execute exec, the file descriptors are inherited by the new process, which means if you change stdin and stdout/stderr, they stay that way, and you can communicate with the process by reading and writing on the pipes you created.

Popen replicates these steps for you but it only seems to be able to open a process for reading or writing but not both.

Obviously just using pclose is probably easier than the second way.

Further note that the constants STDIN_FILENO, STDOUT_FILENO, and STDERR_FILENO are defined in unistd.h (and you should probably use them instead of 0, 1, and 2) and that you can also use the straight dup(2) function on the basis that it allocates the lowest file descriptor first, in place of using dup2, but dup2 is easier.

EDIT:

And I realize I may have been annoying about this but whenever you want to look up the manpage for a function I mentioned, such as **foo(*x*)**, you would type:

```

man x foo

```

Where x is a number 1-9.

If you need to install the manpages:

```

sudo apt-get install manpages-dev

```

They're good to have.

---

### Post by dwhitney67 on 2010-06-02
> **rockom said:**
> 
I'm having a hard time with error handling.

Rather than attempt to use popen() and the lpr directly, why not just use the CUPS API to access your printer?  If an error occurs, the CUPS API will provide you with the reason.

Here's some links to the CUPS documentation:

[http://www.cups.org/documentation.php/doc-1.4/api-cups.html](http://www.cups.org/documentation.php/doc-1.4/api-cups.html)
[http://www.cups.org/documentation.php/doc-1.4/api-ppd.html](http://www.cups.org/documentation.php/doc-1.4/api-ppd.html)
[http://www.cups.org/doc-1.1/sum.html](http://www.cups.org/doc-1.1/sum.html)

Take a look at cupsPrintFile() in the CUPS API; you can create a temporary file (using mkstemp) to write your data, and then send it via CUPS for printing.

I went through this "exercise" recently for a project at work, and the API is real simple to follow.  The best part is that the CUPS library is available on most desktop Linus distros.

---

### Post by rnerwein on 2010-06-03
hi
here your desired coding ( with some extra lines )

#include <errno.h>

errno = 0;
if((printer = popen("/usr/bin/lpr -Pthermal", "w")) == NULL) {  
    perror("open failed");  /* this will give you the error messages from errno.h and <asm-generic/errno-base.h> */
    exit(errno);
}

--> if you don't want to exit - handle the errno to your behavior.
ciao

---

### Post by rockom on 2010-06-10
I ended up not needing to do this however, before that, I found it was simplest to do using cups.h.  I just polled for a list of printers and searched to see if the printer in question was listed.

-Rocko

---

