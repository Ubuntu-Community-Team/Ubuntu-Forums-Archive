---
title: "Process Population Explosion"
date: 2008-07-27
forum: Programming Talk
---

### Post by 3370318 on 2008-07-27
I'm trying to write a multithreaded application (pthreads in c) which must utilize an external program.  As such, I wrote the following type of fork-exec function:

```
// Error checking and most of the functionality has been
// removed for simplicity sake.  Functions called with r_
// or _r are re-entrant.
int test_output(const char* test, const char* directory)
{
    char buffer[BUF_SIZE];
    char* check;
    char* tok;
    int fd[2];

    pipe(fd);
    if(fork() == 0)
    {
        r_dup2(fd[1], STDOUT_FILENO); 
        r_close(fd[0]);
        r_close(fd[1]); 
        execlp("fs", "fs", "examine", directory, NULL);
    }
    else
    {
        r_read(fd[0], buffer, BUFSIZE);
        r_close(fd[0]);
        r_close(fd[1]);
        check = strtok_r(buffer, " \n", &tok);
        while (check)
        {
            if (strcmp(check, test) == 0)
                return 1;
            check = strtok_r(NULL, " \n", &tok); 
        }
    }
    return 0;
}
```

I've run the aforementioned function with multiple threads calling it and with a single thread calling it (repeatedly).  In both cases, the amount of processes spawned (and persisting through the execution) explodes.  From what I've read, it would seem that each child created when this function is called should die off whenever the parent process tests the output...  Clearly, they're still living somehow.  Does anyone have any ideas on what I'm doing wrong or how to keep the amount of processes from exploding?  I suppose I could have the parent kill off its child explicitly, but this seems like a poor solution.

Thanks

---

### Post by slavik on 2008-07-27
once fork() is called, you get 2 processes even if the function calling fork returns ... if you want the process to exit, then call exit.

---

### Post by 3370318 on 2008-07-27
The thing is, exec() does not return unless there was an error; thus I can't make the child process call exit().  Also, I don't want to exit the parent process (the only process that should be able to call exit() in the event of correct operation).

I was under the impression that, after the finishing the program specified by exec(), the process owning the exec() call (namely the child in my example) would terminate.  I suppose, then, that processes don't terminate after exec() even though they don't return?  If that's the way things are supposed to work, I guess my only option is to have the parent explicitly kill its child.

Please let me know if I'm missing something here and thank you for the quick response.

---

### Post by slavik on 2008-07-27
no, when you issue an exec, your program ceases to be and is replaced by another program, if that program doesn't terminate your child stays alive. :)

could you tell us what you are trying to do?

---

### Post by 3370318 on 2008-07-27
Well yes, that's what I meant when I spoke of the child owning the exec() call terminating.  By the way, part of my application (the part that uses the function I included) crawls through directories, but only those that are on the same AFS volume (hence the exec() call to fs).  Now, I know that fs always terminates when run in a shell.  Also, I believe that the children are lingering after fs terminates...  After running the function only once (and waiting for fs to output results to the parent process), I've verified that the child process indeed lingers.

---

### Post by WW on 2008-07-28
Sorry for asking the obvious, but are you sure that the execlp is not generating an error?  It wouldn't hurt to check the return value.

---

### Post by 3370318 on 2008-07-28
The sample code I posted excluded all error checking just for the purposes of being concise.  The code that I actually use does print an error if exec() ever returns (this error message is never printed).  As such, I'm certain that exec() isn't producing any error...

Anyway, I finally figured out what was going on.  After looking through ps results, it was apparent that the fs process always entered into a zombie state.  I've corrected it by forcing the parent process to wait() for its child.  I guess waiting is pretty much a required step for exec calls.

Thanks for your help to those that responded.

---

