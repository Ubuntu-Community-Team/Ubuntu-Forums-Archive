---
title: "What does &quot;!fork()&quot; mean?"
date: 2008-10-30
forum: Programming Talk
---

### Post by f.ben.isaac@gmail.com on 2008-10-30
What does this piece of code mean?

```

if (!fork()) { 
      close(sockfd);
      if (send(new_fd, "Hello, world!", 13, 0) == -1)
           perror("send");
      close(new_fd);
      exit(0);
}

```

"**If (!fork())**" does it mean, if there is no child process, just make one. right?

---

### Post by uljanow on 2008-10-30
"if (!fork()) {...}" only refers to the child process. fork() returns zero in the child process.

---

### Post by supirman on 2008-10-30
The fork call returns 0 to the child created by the fork.  

Typically you'd see something more like
[PHP]
pid = fork();

if(pid == 0)
{
  // this is the child, act accordingly
} else {
  // this is the parent, and the child's process id is in pid
}
[/PHP]

The snippet you posted is just short-handing the check to do a certain action in the child process using the fact that if(!fork()) is essentially the same as if(fork() == 0).

---

### Post by f.ben.isaac@gmail.com on 2008-10-30
I'm new to forks and child process, so bear with me.

Isn't swapper or sched has process ID zero and is responsible for paging & scheduling processes, how come fork() returns 0? child process usually have pid such as 32453, 162, etc...

Can you clarify please

---

### Post by Felson on 2008-10-30
In the child you can get it's PID using $$ so you don't need fork to tell you. (if you are using perl)

---

### Post by rnodal on 2008-10-30
[http://www.manpagez.com/man/2/fork/]("http://www.manpagez.com/man/2/fork/")

-r

---

### Post by supirman on 2008-10-30
> **f.ben.isaac@gmail.com said:**
> I'm new to forks and child process, so bear with me.

Isn't swapper or sched has process ID zero and is responsible for paging & scheduling processes, how come fork() returns 0? child process usually have pid such as 32453, 162, etc...

Can you clarify please

fork() simply returns zero to the child so that there is some way for the parent and child to know which is which.  The zero doesn't mean its process id is zero, it's just an indicator saying "hey, you're the child process".  The reason the id of the child is returned to the parent is because the parent may need to wait() for the child.  If the parent remains running, and doesn't wait() for the child to exit, then the child will become a zombie when it exits.

---

