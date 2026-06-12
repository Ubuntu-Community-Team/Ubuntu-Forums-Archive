---
title: "clone() and the CLONE_CHILD_CLEARTID flag"
date: 2012-03-24
forum: Programming Talk
---

### Post by misterade on 2012-03-24
First of all: hello to everybody ):P, I'm new to this forum but not to ubuntu. I used to post on the italian ubuntu forum and now I'm moving here :-).

I have a quite frustrating problem with the clone() system call in the C language.
I'm trying to use it with the flag CLONE_CHILD_CLEARTID but I cant see any change in the value of the field I specify as argument. Here it is a simple code:
```

int the_child(){
   exit(0);
}
int main(int argc, char * argv[])
{
    pid_t child_id = 99;
    printf("child %p\n",child_id);

    clone((int (*)(void *))the_child,
          NULL,
          CLONE_VM | CLONE_CHILD_CLEARTID | SIGCHLD,
          NULL, NULL,NULL, child_id);

    sleep(1);
    printf("child %p\n",child_id);
 }

```
However when the two printf display always 99, What am I doing wrong?

---

### Post by r-senior on 2012-03-24
Welcome :)

I don't know, but you ought to check the return value:

```
RETURN VALUE
       On success, the thread ID of the child process is returned in the call&#8208;
       er's  thread  of execution.  On failure, -1 is returned in the caller's
       context, no child process will be created, and errno will be set appro&#8208;
       priately.

```

---

### Post by misterade on 2012-03-24
Thank you for your reply.
I know that I can use different way but I'm interested in that flag because I really would like to understand what's wrong.

---

### Post by misterade on 2012-03-24
I get it. I necessary have to specify a value for the child stack. I realized that ```
the_child()
``` wasn't called at all -.-".

---

### Post by r-senior on 2012-03-24
I know, I thought clone might be throwing up an error, in which case testing the return value and using perror might give you a clue?

EDIT: That was a reply to #3 but great that you figured it out.

---

