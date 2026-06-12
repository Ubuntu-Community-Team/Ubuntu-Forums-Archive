---
title: "Writing own shell"
date: 2011-05-04
forum: Programming Talk
---

### Post by zobayer1 on 2011-05-04
I was trying to write a program which is similar to "sh" shell. However, I am having problem dealing with background process. Everything is working fine except the following case:

As it should be, I fork() a child process and use execvp() in child to load the target program in it. And for a background process, in parent process, instead of waiting for this process to terminate, I add it to a list of currently background processes. Now, if somehow execvp() fails (for example: for bad names which are not correct program names) I still add that in main process.

My question is, how I can notify parent process that whether execvp() actually worked or not? Can this be done without IPC? Like just checking process id of child or anything else?

Thanks in advance.

---

### Post by MrStill on 2011-05-04
Perhaps this helps: [http://stackoverflow.com/questions/1822557/determine-if-a-process-is-dead-or-not-by-pid](http://stackoverflow.com/questions/1822557/determine-if-a-process-is-dead-or-not-by-pid)

Some of the other responses make good arguments about not using PID. Perhaps a mailbox or shared memory may be best.

---

### Post by heyandy889 on 2011-05-04
well, when I implemented backgrounding in a shell, here's how I did it (in pseudocode)
```

main(){
infinite loop 
    prompt for input
    foo=fork()
    if(foo>0) //parent process
        if they used backgrounding &
            continue. <-- this is the "keyword" continue, go to next loop iteration
        else if they didn't "background," this is a normal command
            waitpid(foo,0,0); //this is a system call in C.
            //              try "man waitpid" in terminal to learn about waitpid
    else if(foo==0) //child process
        do the command (involves execvp, looking for pipes)
    else //fork returned a negative value
        printf("fork error\n");
        return -1; //indicates error
return 0 //indicates success
} //end main()


```

---

### Post by zobayer1 on 2011-05-05
Thanks for replying, I also did the same in my main(), I mean same algorithm. The problem is with implementing the "jobs" command which lists all the running background processes initiated by my shell. How can I do that? Should I check all the processes having same parent id / group id with main process? or there are smarter ways?

---

### Post by johnl on 2011-05-05
I assume your code looks something like this:

```

    int rc = 0;
    pid_t pid = fork();

    switch(pid) {
    case 0:
        /* child */
        execvp(argv[0], argv);
        /* if exec returns there was an error. */
        perror(argv[0]);
        exit(-1);
    case -1:
        perror("fork");
        return -1;
    default:
        /* parent */
        if (in_bg) {
            printf("[proc %d started]\n", pid);
            /* add pid to some list to track jobs */
        } else {
            /* wait for child to exit */
            if ((waitpid(pid, &rc, 0) != -1)) {
                shell->rc = WEXITSTATUS(rc);
            }
        }
        return 0;
    }

```

Now, regardless of whether exec() succeeds or not, you have a new child process because of the fork.  So there's no reason to worry about that when adding the process id to your list in the parent.

What you then need to do is occasionally check to see if any of your child processes have exited (you can also get this in a signal via SIGCHLD but I like the following approach better):

```

    int status;
    pid_t pid;
    /* waitpid() returns a PID on success */
    while((pid = waitpid(-1, &status, WNOHANG)) > 0) {
        printf("[proc %d exited with code %d]\n",
               pid, WEXITSTATUS(status));
        /* here you can remove the pid from your jobs list */
    }

```

Generally you can do this right after running any other command -- for example, try in bash:

```

$ ls &

```

You won't see that the job has exited until you press enter again.


Hope this helps.

---

### Post by slavik on 2011-05-05
> **heyandy889 said:**
> well, when I implemented backgrounding in a shell, here's how I did it (in pseudocode)
```

main(){
infinite loop 
    prompt for input
    foo=fork()
    if(foo>0) //parent process
        if they used backgrounding &
            continue. <-- this is the "keyword" continue, go to next loop iteration
        else if they didn't "background," this is a normal command
            waitpid(foo,0,0); //this is a system call in C.
            //              try "man waitpid" in terminal to learn about waitpid
    else if(foo==0) //child process
        do the command (involves execvp, looking for pipes)
    else //fork returned a negative value
        printf("fork error\n");
        return -1; //indicates error
return 0 //indicates success
} //end main()


```
your shell should prompt until it gets an EOF, not in an infinite loop.

---

### Post by zobayer1 on 2011-05-06
Thanks to johnl and slavik. That was a great help :)
I solved it using hints from your pseudo-codes. I used a map to store the pids, and in main, I used wait() instead of waitpid() in a slightly different way:

```

    else if(pid) {
        if(bg) {
            // add pid to map
            // continue to read instructions
        }
        else {
            while(1) {
                wpid = wait(&status);
                if(wpid != pid) {
                    // in this case, wpid should be in map
                    // it is a background process
                    // print info and remove it from map
                }
                else if(wpid == pid) {
                    // current child terminated
                    break;
                }
            }
        }
    }

```

I did this because, the background process may terminate anytime and wait will get their pids as well. And it worked so far. But I am going to give it a try the way you have done here.

Thanks :D

---

### Post by bnsk on 2012-10-04
execvp() returns -1 on error.So,if it is returning -1 donot add it to the list...If execvp() is successful then u can use the above approaches...

---

