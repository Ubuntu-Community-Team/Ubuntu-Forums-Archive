---
title: "using wait to remove zombie process from ps"
date: 2012-10-01
forum: Programming Talk
---

### Post by IAMTubby on 2012-10-01
Hey,
I understand that calling wait() is essential to remove details about a zombie process from the process table and ps output.

But my doubt is,
1)"*When a child exits, the parent process will receive a SIGCHLD signal to indicate that one of its children has finished executing.*"
Then what's the need of wait(), the parent is getting a notification anyways right ? Is it only to get the ZombiePID ?

2)Does wait() take care of removing from the process table or,
when wait() returns ZombiePID, you again have to write some code to kill the zombie process ?

Please advise.
Thanks.

---

### Post by IAMTubby on 2012-10-01
Ok, I get till here.
When a child process terminates, it sends a SIGCHLD to it's parent.

What I don't get is, 
The parent **THEN** calls wait(), in order to get the exit status of it's child.

What does that mean ?
1) wait() only returns the pid of the child right ? what do they mean by exit status ?

2)pid_t wait(int* status)
what is the status here ?
how do you pass the status ?

3)The parent calls wait() only after it has received a SIGCHLD ?

I'm confused !

---

### Post by Bachstelze on 2012-10-01
> **IAMTubby said:**
> 
1) wait() only returns the pid of the child right ? what do they mean by exit status ?

The exit status of the child is the argument to the call to exit() that terminated it.

> 2)pid_t wait(int* status)
what is the status here ?
how do you pass the status ?

You pass a pointer to int. That is, a memory address where an int can be stored. Then wait() will store the exit status of the child at that memory address.

> 3)The parent calls wait() only after it has received a SIGCHLD ?


The parent calls wait(). Typically there is no need to do anything with SIGCHLD.

---

### Post by azzamite on 2012-10-01
> **IAMTubby said:**
> 
What does that mean ?
1) wait() only returns the pid of the child right ? what do they mean by exit status ?
int main(){
   return 1; //this is the exit status
}

> **IAMTubby said:**
> 
2)pid_t wait(int* status)
what is the status here ?
how do you pass the status ?
You don't pass the status, you RETRIEVE the exit status

int status;
wait(&status);

> **IAMTubby said:**
> 
 3)The parent calls wait() only after it has received a SIGCHLD ? 
Not necessarily:
> If a child has already changed state, then these calls return immediately. Otherwise they block until either a child changes state or a signal handler interrupts the call

---

### Post by IAMTubby on 2012-10-01
> **Bachstelze said:**
> 
> **azzamite said:**
> 
Thanks for the replies. Almost get it now.

So the exit status is a number like 0,1 etc. And int* status, holds the address of a memory location which holds the exit status(an integer).

Have a couple of doubts more
1)So, you call the wait function giving the address of a memory location as argument ? When does this location get filled ?
2)What does the parent do depending on the exit status ? On what basis do these exit status vary ?
3)Please can you explain in a couple of sentences what happens after the wait function is called by the parent. as in, how the zombie is removed from the process table.

---

### Post by Bachstelze on 2012-10-01
> **IAMTubby said:**
> 
1)So, you call the wait function giving the address of a memory location as argument ? When does this location get filled ?

wait() fills it, that's part of its job.

> 2)What does the parent do depending on the exit status ? On what basis do these exit status vary ?

The parent does whatever its code says.

There is no rule governing exit statuses. The closest thing there is is that 0 indicates success and anything else indicates failure, but even that is not an absolute requirement. Typically, the documentation of a program will describe what it means when it exits with a given error code.

> 3)Please can you explain in a couple of sentences what happens after the wait function is called by the parent. as in, how the zombie is removed from the process table.

No. This is why I told you to get a book on operating systems, and I still strongly believe you should.

---

### Post by IAMTubby on 2012-10-01
> **Bachstelze said:**
> wait() fills it, that's part of its job.



The parent does whatever its code says.

There is no rule governing exit statuses. The closest thing there is is that 0 indicates success and anything else indicates failure, but even that is not an absolute requirement. Typically, the documentation of a program will describe what it means when it exits with a given error code.



No. This is why I told you to get a book on operating systems, and I still strongly believe you should.
Thanks a lot Bachstelze. About the last answer, I shall refer an OS book as you said and get back to you with the answer.

Thanks a lot :)

---

