---
title: "Fork in Unix C"
date: 2011-03-11
forum: Programming Talk
---

### Post by petersmith01115 on 2011-03-11
[COLOR=black][FONT=&quot]Can someone please e[/FONT][/COLOR][COLOR=black]xplain what happens in the parent and child when the following statement is executed:  x = fork();[/COLOR]

---

### Post by petersmith01115 on 2011-03-11
[COLOR=black][FONT=&quot]Can someone please e[/FONT][/COLOR][COLOR=black][FONT=&quot]xplain in detail what happens when each of the following statements are executed. [/FONT][/COLOR][FONT=&quot]You may assume all variables have been properly declared and this code. 
[/FONT]





[FONT=&quot][COLOR=black][/COLOR][/FONT]
  [FONT=&quot]var1 = 1;[/FONT]
  [FONT=&quot]var2 = fork();[/FONT]
  [FONT=&quot]if ( var2 <= 0 )[/FONT]
  [FONT=&quot]  {[/FONT]
  [FONT=&quot]     var1 = 33;[/FONT]
  [FONT=&quot]  }[/FONT]
  [FONT=&quot]else[/FONT]
  [FONT=&quot]  {[/FONT]
  [FONT=&quot]    var1 = 22;[/FONT]
  [FONT=&quot]  }[/FONT]
  [FONT=&quot]printf(“var1 = %d\n”, var1);[/FONT]
  [FONT=&quot]wait(&temp);[COLOR=red][/COLOR][/FONT]

---

### Post by petersmith01115 on 2011-03-11
Can someone please xplain what happens in the parent and child when the following statement is executed:  x = fork();

---

### Post by Arndt on 2011-03-11
> **petersmith01115 said:**
> [COLOR=black][FONT=&quot]Can someone please e[/FONT][/COLOR][COLOR=black][FONT=&quot]xplain in detail what happens when each of the following statements are executed. [/FONT][/COLOR][FONT=&quot]You may assume all variables have been properly declared and this code. 
[/FONT]





[FONT=&quot][COLOR=black][/COLOR][/FONT]
  [FONT=&quot]var1 = 1;[/FONT]
  [FONT=&quot]var2 = fork();[/FONT]
  [FONT=&quot]if ( var2 <= 0 )[/FONT]
  [FONT=&quot]  {[/FONT]
  [FONT=&quot]     var1 = 33;[/FONT]
  [FONT=&quot]  }[/FONT]
  [FONT=&quot]else[/FONT]
  [FONT=&quot]  {[/FONT]
  [FONT=&quot]    var1 = 22;[/FONT]
  [FONT=&quot]  }[/FONT]
  [FONT=&quot]printf(“var1 = %d\n”, var1);[/FONT]
  [FONT=&quot]wait(&temp);[COLOR=red][/COLOR][/FONT]

Homework.

How far have you got yourself?

---

### Post by petersmith01115 on 2011-03-11
just need some idea. i want to understand.

---

### Post by overdrank on 2011-03-11
Threads merged. :)

---

### Post by anatolik on 2011-03-12
> **petersmith01115 said:**
> just need some idea. i want to understand.

[The man page is a good place to start from](http://linux.die.net/man/3/fork)

fork() function asks the underlying operation system to create a new process. Right after the fork() you have 2 *identical* processes that have their own memory/file descriptors/...

The only difference that fork() returns zero in the child process and non-zero in the parent.

```
pid_t child_pid = fork();

if (child_pid) {
  // if child_pid is not equal 0 then we are in the parent (original) process
  // Most of the time you run exec() function here (see "man exec")
} else {
  // this code executes in the child process
}
```

---

### Post by cguy on 2011-03-12
I suggest you get this book:
**Advanced Programming in the UNIX® Environment: Second Edition**
By W. Richard Stevens, Stephen A. Rago

It's awesome.

> Can someone please explain in detail what happens when each of the following statements are executed. You may assume all variables have been properly declared and this code. 

[php]var1 = 1;
var2 = fork();
if ( var2 <= 0 )
{
var1 = 33;
}
else
{
var1 = 22;
}
printf(“var1 = %d\n”, var1);
wait(&temp);[/php]

So we have a process running this ^^^ code; let's name it process A. Inside process A we have a  variable var1 whose value is 1.

Then we have this line:
[php]var2 = fork();[/php]
which means execute the function fork() and *then* assign its return value to variable var2.

fork() creates a new process (let's name it "process B"), which is A's child.
Being A's child means that B will execute the same instructions following fork() as A does, but receives *a copy* of A's variables.

Therefore, modifying var1 inside process A will not alter var1 inside process B and viceversa.

Also: fork() returns a negative value (-1) if it failed to create a child or, if it succeeds, it returns 0 inside the child and it returns the child's process ID to its parent.

**1st case:** Let's assume that fork() failed to create a child.
var2 (inside the parent, since we have no child) will be -1, so the first branch of the if will be executed, i.e. var1=33.
Afterwards, var1 is printed to the standard output and our process will wait for one of its children to terminate (if it has any children whose creation was not shown in your code)

If our process has no previously created children, wait(&temp) will cause our process to BLOCK (ie: get stuck).

wait() receives a pointer to an int as an argument, where it will store the return status of a terminated child.



**2nd case:** fork() could create a child process. We will have two distinct processes: parent and child. As I said earlier, the child receives *a copy* of the parent's variables.
Therefore:
child process: var1 = 1; var2 = 0; (because fork() returns 0 to the child)
parent process: var1 = 1; var2 = child's PID (a number greater than 0)

These two processes, the child and the parent, will share any code following fork(), but each will execute that code in it's own way.

For the child, var2==0, so the first branch of the if will be executed: var1=33. The child will then print "var = 33" to the standard output. Then, the child will wait for one of its children to terminate and fetch its status inside temp, but Alas! it HAS NO CHILDREN, therefore it will get stuck (the proper way of saying is that it will block).

For the parent, var2 will be greater than 0, so the second branch of the if will be executed: var1 = 22; the parent will then print "var1 = 22" to the standard output and then wait for one of its children to terminate. The child which was created with our fork() here will never terminate, so unless the parent has other children which will terminate soon of which have already terminated(*), the parent will also block.


Beware that the child and the process run in parallel and there's no way of knowing which executes its instructions first, so the output on the standard output could be either
```
var1 = 33
var1 = 22
```
OR
```
var1 = 22
var1 = 33
```


explanation of the (*):
The kernel will remember any terminated child's PID, termination status, CPU time (and possibly other details) until that child's parent calls *wait(<pointer>)*. Such children for whom has not been called wait(<pointer>) are called *zombie processes*. (the **ps** command will show a Z for them)

If a parent has zombie children, *wait(<pointer>)* will return immediately with the PID and termination status of the first-in-line zombie child (and that child will be forgotten by the kernel); otherwise, calling *wait(<pointer>)* causes the parent to wait for a child to terminate.
edit:I should have said that wait() has no effect if a process has no children, instead of causing the calling process to block.


I hope that I was clear enough.
Get that book! :D

---

### Post by petersmith01115 on 2011-03-12
Thanks :)

Can someone please explain:

Semaphores are used to control access to resources.  
a.    Explain why we might need to control two users’ access to a printer.
b.    Assume the value of my_semaphore is 1. Explain what happens if a P/down P(my_semaphore) operation is performed on the semaphore.
c.    Assume the value of my_semaphore is 0. Explain what happens if a V/up V(my_semaphore) operation is performed on the semaphore.

---

### Post by petersmith01115 on 2011-03-12
Can someone please explain:

Semaphores are used to control access to resources.  
a.    Explain why we might need to control two users’ access to a printer.
b.    Assume the value of my_semaphore is 1. Explain what happens if a P/down P(my_semaphore) operation is performed on the semaphore.
c.    Assume the value of my_semaphore is 0. Explain what happens if a V/up V(my_semaphore) operation is performed on the semaphore.

Thanks :)

---

### Post by johnl on 2011-03-12
Hi,

Perhaps you should do some reading and attempt to answer your homework questions on your own.  What good will it do for someone else to answer it for you?

---

### Post by cguy on 2011-03-12
We need to control the access to a printer/memory location for the same reason there's a single steering wheel inside a car: more than one car driver would result in things getting ugly.

As for the rest of the questions: you are lazy, aren't you? Find the answers with Google.

---

### Post by Iowan on 2011-03-12
Closed.

---

