---
title: "need help c++ semaphores"
date: 2007-11-12
forum: Programming Talk
---

### Post by realitybites on 2007-11-12
i have writer and reader processes (two instances of writer process)
i want to use semaphores, with down and up operations

i have no problem implementing semaphores or creating processes  but,
my problem using interprocess communication. how can i use the shared resource (an array for example) between processes? how can i make them use the same array? 

i also guess i need to use another semaphore to lock and unlock the array?

here are my processes:
```

        pid0= fork();			
	if(pid0==0){
		execl("writer", (char *)0);
	}
		
	pid1= fork();
	if(pid1==0){
		execl("reader", (char *)0);
	}	
	
	pid2= fork();
	if(pid2==0){
		execl("reader", (char *)0);
	}
```

any useful link or suggestion is appreciated. i found many detailed info about thread synchronization but i need to use processes.

---

### Post by bunker on 2007-11-12
You can use pretty much all the same techniques with threads and processes, however if you're doing an exec call the exec'd command (here 'reader' and 'writer') won't be able to have access to the calling process.  Instead, they need to be part of your program, eg:
```

if (!fork()) {
  reader();
}

```
You can see that's almost the same as launching a thread anyway.

If you have to use a separate command, you would need to redirect stdin/stdout and use pipe() for communication, or possibly think something up using other modes of IPC like sockets and named pipes.

---

### Post by realitybites on 2007-11-12
i have to use seperate processes.
i will give those a try, i have read about pipe but i wasn't so sure if i can use that

---

### Post by slavik on 2007-11-12
use pipes for interprocess communication and global buffer for threads.

---

### Post by aks44 on 2007-11-12
> **slavik said:**
> use [...] global buffer for threads.

Better use message queues, they are sooo easy to manage... :)

---

### Post by realitybites on 2007-11-12
i piped the stdin and stdout. but since the stdout of one process is connected to the other process' stdin, i can't print messages from that process, which i need to do

but i think there should be a solution, which i don't know:)

this is an assignment by the way. that's why i'm saying "i should" or "i have to"

---

### Post by slavik on 2007-11-12
> **aks44 said:**
> Better use message queues, they are sooo easy to manage... :)
Are they? (have never seen the code)

I find that lock, read/write, unlock is pretty simple, too. But I don't do much parallel programming atm.

---

### Post by the_unforgiven on 2007-11-13
> **realitybites said:**
> i have writer and reader processes (two instances of writer process)
i want to use semaphores, with down and up operations

i have no problem implementing semaphores or creating processes  but,
my problem using interprocess communication. how can i use the shared resource (an array for example) between processes? how can i make them use the same array? 

i also guess i need to use another semaphore to lock and unlock the array?

here are my processes:
```

        pid0= fork();			
	if(pid0==0){
		execl("writer", (char *)0);
	}
		
	pid1= fork();
	if(pid1==0){
		execl("reader", (char *)0);
	}	
	
	pid2= fork();
	if(pid2==0){
		execl("reader", (char *)0);
	}
```

any useful link or suggestion is appreciated. i found many detailed info about thread synchronization but i need to use processes.
If you need to use a data structure across processes (**not** threads), then [shared memory]("http://en.wikipedia.org/wiki/Shared_memory") is the way to go.
It's a standard POSIX IPC mechanism.

And yes, to serialize the access to the shared data structures, you would need some sort of lock/mutex (either with a semaphore or some other mechanism) to protect the data structure.

---

### Post by realitybites on 2007-11-13
do you know any useful tutorial about shared memory?
i found this: [shmdemo.c]("http://www.ecst.csuchico.edu/~beej/guide/ipc/shmdemo.c")
but i didn't understand how to make processes communicate and couldn't find a way to use it with an array. 
this is my first experience with IPC :)

---

### Post by aks44 on 2007-11-13
> **slavik said:**
> [QUOTE=aks44]Better use message queues, they are sooo easy to manage...Are they? (have never seen the code)

I find that lock, read/write, unlock is pretty simple, too. But I don't do much parallel programming atm.[/QUOTE]


Locking individual variables is OK for small scale projects IMHO. But you can hardly sustain fine-grained locking when your project grows (number of variables and number of threads).


Even the famous guru Herb Sutter warns about locks (emphasis mine):
[quote=Herb Sutter]- Locks are **not composable**. You can’t take two pieces of code that use locks, each of them provably correct, and put them together and get something new that’s sure to be correct. You **can’t test** for that. And it’s common now for two pieces of software to be composed for the first time on the user’s machine.
- Locks are hard for **experts** to get right.[/quote]


So you're basically left with coarse-grained locking (which denies the whole point of concurrent programming), or with endless hours of hair-pulling. The only other practical option I know of are indeed message queues.


Each queue (a double-linked list is probably the best choice to implement it) has its own mutex controlling pushes/pops, and each thread has just *one* input message queue (several threads can share a single queue though). On Windows I also use a helper *event* (not sure if events exist on Linux though) to wake up the slave thread as soon as possible without constantly polling the queue. A message should be self-contained as much as possible, ie. a thread should be able to work exclusively on the message it is currently processing, without need to acquire any lock on external data.


Depending on your requirements it may (often will not) involve some copying overhead, but the benefits WRT enhanced concurrency generally beat the cost of that overhead.

Of course as any concurrent programming it needs to be designed very carefully, but in my experience it alleviates many problems related to fine-grained locking (ever rewrote some code from scratch because you just couldn't determine where the dead/livelock comes from?) and it really increases concurrency compared to coarse-grained models. The real good part is that the message-queue model is totally asynchronous so the "non-composability" evoked by Sutter disappears.


To sum it up: the design can hardly be more simple, it has almost zero risk and many benefits. Win-win... :)

---

### Post by slavik on 2007-11-13
> **aks44 said:**
> Each queue (a double-linked list is probably the best choice to implement it) has its own mutex controlling pushes/pops, and each thread has just *one* input message queue (several threads can share a single queue though). On Windows I also use a helper *event* (not sure if events exist on Linux though) to wake up the slave thread as soon as possible without constantly polling the queue. A message should be self-contained as much as possible, ie. a thread should be able to work exclusively on the message it is currently processing, without need to acquire any lock on external data.

What you can do is sleep until a variable has changed (I forgot what this is called).

---

