---
title: "need insight of fork()"
date: 2010-08-10
forum: Programming Talk
---

### Post by piyush.neo on 2010-08-10
As fork() is known to be a function which is called once but return twice....
What i know about the fork:
when fork is called it replicates the whole program and create a process and return with pid in parent.
The replicated program also runs from the  point after which fork is called b'coz it copied parent's stack(PC etc) also and return 0.
Am i right?
if no plz correct n if yes plz en-light me by further giving some refence to study
Thanks..:p

---

### Post by Bachstelze on 2010-08-10
Yes.

---

### Post by dwhitney67 on 2010-08-10
Your answer is here:
```

man fork

```

---

### Post by piyush.neo on 2010-08-11
> **dwhitney67 said:**
> Your answer is here:
```

man fork

```
have already done that....i have 1 doubt-
do child process start from the instruction fork() or the instruction next to fork?
if it start form fork then why doesn't it create a new process too, and if from next instruction after fork() then how does 0 value is returned by fork to child process as in

pid=fork()
...
.....
....

---

### Post by dwhitney67 on 2010-08-11
Maybe I don't quite understand your question.  In the example you provided, the value of pid is 0 for the child; but for the parent, it is the process-id of the child.  Don't try to interpret more into this than what I have already described.

P.S.  The child process begins after the fork().  Thus it does not invoke the fork() call; the parent does.

---

### Post by piyush.neo on 2010-08-11
> **dwhitney67 said:**
> Maybe I don't quite understand your question.  In the example you provided, the value of pid is 0 for the child; but for the parent, it is the process-id of the child.  Don't try to interpret more into this than what I have already described.

P.S.  The child process begins after the fork().  Thus it does not invoke the fork() call; the parent does.

i know i am getting more into it than need. Actully thats part of my assignment..
If fork in not invoked in child, then how it can return 0 to child ?

---

### Post by Bachstelze on 2010-08-11
> **piyush.neo said:**
> i know i am getting more into it than need. Actully thats part of my assignment..
If fork in not invoked in child, then how it can return 0 to child ?

It places the value 0 on the child's stack frame, where the value returned by fork() is supposed to be.

---

### Post by piyush.neo on 2010-08-12
Thanks...

---

