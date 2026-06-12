---
title: "stop / start execution of program using  C  newbie question."
date: 2010-06-23
forum: Programming Talk
---

### Post by cristiangarofalo on 2010-06-23
Hey Guys, 
i've been back and forth with a problem That I dont' know how to resolve.
I have a program called server , i need to create an interface to stop and start this program in the background.
I need to be able to launch the process and then using that pid be able to kill it stop etc, 

i need something like this:

switch (pid = fork())
{
case -1:
exit(1)
case 0:
// here I need to be able to call server(); get its pid
// and automatically continue with the execution of my program (parent)
// if its not possible I can compile server and call system(server)
// but how do I know the pid of server? 
// I need the pod to be able to kill it later on the main if the customer chose "stop server"
default:
Menu();
}

any clue? advice?

Thanks!

---

### Post by johnl on 2010-06-23
When you do fork(), you get two copies of your program, a parent and a child.  The return value of fork() is 0 in the child process and **the child's pid** in the parent process.  So you have already solved one problem (get the pid of your child process).  You can use this pid to **kill** (man 2 kill) the child process if necessary.

There is a family of functions called **exec** that allow you to replace a running process with a different image.  This is what you need to do. 


Check **man 3 exec** for information.

```

pid_t pid;

switch (pid = fork())
{
  case -1:
    exit(1);
  case 0:
     /* call one of the exec() functions to launch server */
     /* the exec() calls do not return except in case of error */
  default:
    printf("my child's process ID is %d\n", pid);
    /* call kill() here to terminate the child process */
    break;
}

```

Hopefully this will point you in the right direction.

---

### Post by cristiangarofalo on 2010-06-23
Thank you!!!

---

