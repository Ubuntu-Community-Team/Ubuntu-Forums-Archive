---
title: "Process started with system() inherits stream redirection."
date: 2009-12-01
forum: Programming Talk
---

### Post by Xyro on 2009-12-01
During some work I came across something interesting. Hopefully someone can shed some light on it for me.

Consider the following example, where one process (loader) executes another (module) via system() after redirecting stderr to a log file. Please forgive the lack of error checking. Security concerns are welcome, however the software I am developing will be a research tool and not distributed.

Loader code:

```

/***** loader.c *****/
# include <stdio.h>
# include <stdlib.h>

int main (int argc, char** argv) {

    FILE* fp;

    fp = freopen("log.txt", "w", stderr);

    fprintf(stderr, "Loader: Executing module.\n");fflush(stderr);

    system("./module");

    fprintf(stderr, "Loader: Done.\n");fflush(stderr);

    // sleep(20);

    fclose(fp);

    return 0;

}

```

Module code:

```

/***** module.c *****/
# include <stdio.h>

int main (int argc, char** argv) {

    fprintf(stderr, "Module: I am running.\n");fflush(stderr);

    return 0;

}

```

The file log.txt contains:

```

Loader: Executing module.
Module: I am running.
Loader: Done.

```

When I insert a sleep() into the loader before it closes the file, run it and then quickly run ./module again ( independently of the loader software, from another terminal while loader is blocked by sleep() ) the independent module's output is not redirected. It seems that the redirection of the stream is inherited by the module when called by system(), which I was unaware of. Does anyone know why it is inherited? If so, can it be relied upon to be inherited? Can it be forced not to be inherited?

Cheers,

Xyro

---

### Post by dwhitney67 on 2009-12-01
system() relies on the use of fork() (probably by use of one of the flavors of exec()).  In any event, because of the fork(), the new process inherits the file-stream(s) of the parent process.

P.S.  Run your loader app as follows:
```

strace -f ./loader

```
In the output that is generated, you will probably/hopefully see one of the exec() type of calls.

EDIT:  Maybe fork() is not used??

Anyhow, from the execve() manpage:
> 
execve()  does  not  return  on  success, and the text, data, bss, and stack of the calling process are overwritten by that of the program loaded.  The program invoked inherits  the calling process's PID, and any open file descriptors that are not set to close-on-exec.


---

### Post by Xyro on 2009-12-01
Thanks!

Do you know of any methods to set the inheritance polity (specifically, stream-related) through a fork()? I did a quick Google search and came up with more questions than answers. A key word or two to get me started would be greatly appreciated.

From manpages for fork():

> For other scheduling policies, the policy and priority settings on fork() are implementation-defined.

Not sure what to make of that. Although, that seems to refer to the scheduling policy, which I am not concerned with.


Note: Wrote this before seeing your edit.

So flagging stderr to close-on-exec might reset stderr once in module? Or does it make no sense to close stderr?

---

### Post by Xyro on 2009-12-01
A bit of progress:

Using fcntl() to set stderr to close-on-exec...

Changing loader.c to look like (changes **bold**):

```

/***** loader.c *****/
# include <stdio.h>
# include <stdlib.h>

[B]# include <unistd.h>
# include <fcntl.h>[/B]

**# define STDERR_FD 2**

int main (int argc, char** argv) {

    **int   flags;**
    FILE* fp;
    
    fp = freopen("log.txt", "w", stderr);
    
    [B]flags = fcntl(STDERR_FD, F_GETFD);
    if (flags == -1)
        printf("Something is wrong...\n");
    flags |= FD_CLOEXEC;
    
    if (fcntl(STDERR_FD, F_SETFD, flags) == -1)
        printf("Something is definitely wrong...\n");[/B]

    fprintf(stderr, "Loader: Executing module.\n");fflush(stderr);

    system("./module");

    fprintf(stderr, "Loader: Done.\n");fflush(stderr);

    fclose(fp);

    return 0;

}

```

Results in the module not writing to the file. However, it doesn't write out on the screen as usual (when stderr is not redirected to a file). This makes sense, I guess, since I closed stderr... How to 'reset-on-exec'...

Any thoughts?

---

### Post by dwhitney67 on 2009-12-01
I have no idea!

The stderr stream is tied to the shell in which an application is executed in.  Your 'module' application is executed in a different shell than your 'loader' application.  Thus I don't quite understand how you expect to see the stderr messages emanating from 'module'.

May I suggest that in lieu of using system(), that you use fork() to run whatever 'module' must do.  Or alternatively, run 'module' as a separate thread.

In 'loader', do not close stderr; just use fopen() to open the "log.txt" file, and use the returned FILE-handler whenever you must fprintf().

---

### Post by Arndt on 2009-12-01
> **dwhitney67 said:**
> I have no idea!

The stderr stream is tied to the shell in which an application is executed in.  Your 'module' application is executed in a different shell than your 'loader' application.  Thus I don't quite understand how you expect to see the stderr messages emanating from 'module'.

May I suggest that in lieu of using system(), that you use fork() to run whatever 'module' must do.  Or alternatively, run 'module' as a separate thread.

In 'loader', do not close stderr; just use fopen() to open the "log.txt" file, and use the returned FILE-handler whenever you must fprintf().

I think the question is whether freopen of stderr should tie the newly opened file to the same file descriptor (which is what happens here), or if it may (on other platforms/compilers) affect just the 'stderr' stream but not file descriptor 2.

Either it makes an explicit effort to tie it to fd 2 (whether because the standard says so, or because it seems like a good idea, I don't know), or this happens because it first closes whatever file descriptor the stream happens to be tied to (2), and then the first available file descriptor (which is again 2) gets tied to the new file.

---

### Post by Xyro on 2009-12-01
Thanks again for the replies. Sorry, I guess I should elaborate now that my software's intent is beginning to play a role.

I have a loader program that links and runs shared library functions, which I call 'plug-ins'. I want the plug-ins and the loader all to write to the same log file, but I don't want to pass the file descriptor all over the place. Hence the redirection of stderr to the log file. The loader also has a list of stand-alone processes (their being completely stand alone is crucial) which I call 'modules'. The loader will execute these modules, one by one, with system(). Since they must be completely separate* from the loader, fork() wont do the job.

Initially, I figured there was no way to have these modules write to the same log file as the plug-ins and loader, without explicitly opening that file. (note: there is no multi-threading or multi-processing going on, so simultaneous access to the log file was not a concern). However, when looking into it, I noticed that stderr remained redirected to the log file inside the modules and my modules could write to it just by writing to stderr. This is very convenient, but I needed to know more about the hows and whys before committing to employing this method. Also, it may be more desirable for these modules to have their own log file. So I was wondering if there was a way to disable this inheritance.

The other important point is I want to use the same static library code for all three elements' logging needs. I think I've solved it, though.

If the log_open function in my logging library opens the log file and redirects stderr to it, then when my modules call log_open, stderr will be redirected from the plug-in/loader's log file to its very own log file (that it just opened). If I want to have a module write to the loader's log file, I simply don't call log_open, but straight to log_write (which writes to stderr, and would be redirected to the loader's log file).

Thanks for the help!

Cheers,

Xyro


* By completely separate, I mean separate source code, compiled independently.

---

### Post by Arndt on 2009-12-08
> **Arndt said:**
> I think the question is whether freopen of stderr should tie the newly opened file to the same file descriptor (which is what happens here), or if it may (on other platforms/compilers) affect just the 'stderr' stream but not file descriptor 2.

Either it makes an explicit effort to tie it to fd 2 (whether because the standard says so, or because it seems like a good idea, I don't know), or this happens because it first closes whatever file descriptor the stream happens to be tied to (2), and then the first available file descriptor (which is again 2) gets tied to the new file.

I'll follow up on my own thoughts. An experiment shows that what happens is that freopen closes the file descriptor of stderr, opens the new file, and saves the file descriptor in the stderr struct. In other words, it doesn't make any special effort to keep stderr tied to file descriptor 2 specifically. The experiment consisted in closing stdout first. Then the new stderr becomes tied to file descriptor 1, and the subprocess when writing to its stderr will be writing to a closed file descriptor 2.

Still, as long as you know that you're not closing either of stdin or stdout, reopening of stderr will keep it tied to file descriptor 2, on Ubuntu 9.10, using gcc. Says the experiment - I don't know what the standard says.

---

