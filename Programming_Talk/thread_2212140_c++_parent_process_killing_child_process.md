---
title: "c++ parent process killing child process"
date: 2014-03-19
forum: Programming Talk
---

### Post by thisisbasil on 2014-03-19
I am stuck on a piece of code similar to the following

[HTML]...
pid_t pid = fork();
if (pid == 0) 
{
    //in child process
    do_something();
}
else
{
    cout << "Press enter to end\n";
    cin.get();
    prctl(PR_SET_PDEATHSIG,SIGHUP);
}

return 0;[/HTML]

What I thought was supposed to happen here is that, after the fork, the child process goes off and does something, while the parent process waits on user input (i.e. press enter), and then terminates. I was under the assumption that the prctrl statement above would terminate all child processes. However, when I execute my program and monitor the processes with "ps -a", I notice that the parent process and (I assume) the child process is left stranded. How would I go about killing the child process when the parent process ends?

---

### Post by ofnuts on 2014-03-19
What your prctl() call does is set the signal your parent process would receive if its own parent dies (and gettting a SIGHUP in this case is the default behavior): 
> 
**PR_SET_PDEATHSIG **(since Linux 2.1.57)
              Set the parent process death signal of the calling process to
              *arg2* (either a signal value in the range 1..maxsig, or 0 to
              clear).  This is the signal that the calling process will get
              when its parent dies.  This value is cleared for the child of
              a [fork(2)]("http://man7.org/linux/man-pages/man2/fork.2.html") and (since Linux 2.4.36 / 2.6.23) when executing a
              set-user-ID or set-group-ID binary.  This value is preserved
              across [execve(2)]("http://man7.org/linux/man-pages/man2/execve.2.html").


If you want your children process to terminate when your process terminates, there is nothing to do, this is automatic (they will get a SIGHUP)

---

### Post by thisisbasil on 2014-03-19
I thought that would be the case as well, but it is not happening here.

The last run-though (using ps -a), I saw that the parent process had a pid of 14311, and the child had a pid of 14314. I gave the command to terminate the parent process (i.e. pressing enter from the example listed above). I then ran ps -a again and I saw that the parent had indeed terminated, but the child was still alive.

Is there something I am missing here?

---

### Post by ofnuts on 2014-03-20
Sometimes it takes a small while for the children to get killed. Otherwise use prctrl() but in the "child" branch, to make sure the children receive a SIGHUP when the parent ends. You may also set up a SIGKILL instead.

---

### Post by dwhitney67 on 2014-03-22
From the fork(2) man-page:
> 
       *  The prctl(2) PR_SET_PDEATHSIG setting is reset so that the child  does  not  receive  a
          signal when its parent terminates.


If you want to terminate a child process when the parent process is terminated, then use kill(3).  For example:
```

#include <iostream>
#include <csignal>
#include <unistd.h>

void sigHandler(int signo)
{
    std::cout << "Got a signal: " << signo << std::endl;;
    exit(signo);
}

void childProcess()
{
    while (true)
    {
        std::cout << "The child is running" << std::endl;
        sleep(1);
    }
}

int main()
{
    pid_t pid = fork();

    if (pid == 0)
    {
        // child process
        signal(SIGHUP, sigHandler);
        childProcess();
    }
    else
    {
        // parent process
        sleep(2);
        kill(pid, SIGHUP);
    }
}

```

---

