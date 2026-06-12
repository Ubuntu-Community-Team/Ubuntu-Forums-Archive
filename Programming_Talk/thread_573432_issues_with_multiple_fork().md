---
title: "issues with multiple fork()"
date: 2007-10-11
forum: Programming Talk
---

### Post by ittiam on 2007-10-11
Hi,

I guess this question has been asked before somewhere but I would just like to clarify somethings

Consider the program

```

void do_fork2()
{
   printf("spawned\n");
}

int main()
{
    fork();
    fork();
}
```

Output
```

spawned
spawned
spawned
spawned
```

i have couple of questions
[LIST=1]
[*]How many process get spawned? I assumed it is 3 including the parent, the parent creates a copy of itself during the first fork and the first child creates a copy of itself using the second fork. But here i see 4 spawned
[*]Since the parent(s) are not waiting for child to finish here, arent zombies getting created?
[/LIST]

Answers will be of great help.

---

### Post by DMills on 2007-10-11
After the first fork you have 2 process, each of which then forks again giving 4 processes total. 

As to zombies, possibly, if the parents outlive the children (otherwise init (or the grandparent) inherits the child processes, and that does wait), but in any case the thing exits quickly and init (or the grandparent) will then handle the cleanup. 

Regards, Dan.

---

### Post by ittiam on 2007-10-11
Thanks. I also figured it out that if you dont check for the pid of child process whatever ensues the fork will be executed by all processes.

---

