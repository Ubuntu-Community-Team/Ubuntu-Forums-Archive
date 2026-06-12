---
title: "Need guidance on making a mini shell :/"
date: 2011-10-21
forum: Programming Talk
---

### Post by Pithikos on 2011-10-21
I have to make a mini shell that:

[LIST=1]
[*]executes external programs
[*]can use pipes
[*]can redirect I/O
[/LIST]

My pseudocode for executing a program is this:

```
fork(shell)

if child
    exec(program)
if parent
    wait(child)
```So i fork the shell. The child runs the program I want and the parent waits for the child to finish the execution.

Now I am totally lost on how to add **redirection** and **pipes** into this :?

---

### Post by Arndt on 2011-10-21
> **Pithikos said:**
> I have to make a mini shell that:

[LIST=1]
[*]executes external programs
[*]can use pipes
[*]can redirect I/O
[/LIST]

My pseudocode for executing a program is this:

```
fork(shell)

if child
    exec(program)
if parent
    wait(child)
```So i fork the shell. The child runs the program I want and the parent waits for the child to finish the execution.

Now I am totally lost on how to add **redirection** and **pipes** into this :?

Have you been told about the 'pipe' and 'dup' system calls?

---

### Post by ofnuts on 2011-10-21
> **Pithikos said:**
> I have to make a mini shell that:

[LIST=1]
[*]executes external programs
[*]can use pipes
[*]can redirect I/O
[/LIST]

My pseudocode for executing a program is this:

```
fork(shell)

if child
    exec(program)
if parent
    wait(child)
```So i fork the shell. The child runs the program I want and the parent waits for the child to finish the execution.

Now I am totally lost on how to add **redirection** and **pipes** into this :?
I'll assume it's done in C?

With exec() the child doesn't run the program. The child ***becomes*** the program.

IIRC ( 15 years:) ) the app started by exec() keeps the same file descriptors, so if you don't do anything, it inherits them for the forked() self and so will read from the same stdin stream and write to the same stdout/stderr streams. 

Things get a bit more complicated when you want to feed input to your children process and catch their output or pipe things between child processes. Before calling exec(), your forked process will use dup2() to copy file descriptors prepared by the parent before the fork() to its file descriptors 0,1,2. To connect two children processes by a pipe, the parent uses pipe() to create a pipe, and passes the write descriptor to use as stdout to the first process and the read descriptor to use as stdin to the new       process. So the pseudo code to start one child process would be:
```

open relevant descriptors for child (pipe, open file, or current descriptor), store to childff0,childff1,childff2
fork()
if child
    dup2(childfd0,0)
    dup2(childfd1,1)
    dup2(childfd2,2)
    exec()

```

---

