---
title: "[C] IPC: Shared Memory and Semaphore"
date: 2008-01-22
forum: Programming Talk
---

### Post by iddqd on 2008-01-22
Hello everybody,

i'm new to Linux and have to code a small "client/server" app with Linux Processes. The Processes use a shared memory to transfer the messages, the server simply prints it on the console, the clients read from stdin. 

Server:
```
#include <sys/types.h>
#include <sys/stat.h>
#include <sys/wait.h>
#include <sys/ipc.h>
#include <sys/shm.h>
#include <sys/sem.h>

#include <stdlib.h>
#include <string.h>
#include <stdio.h>

#include <unistd.h>
#include <errno.h>

#define SHM_KEY 12
#define SEM_KEY 5


int main(int argc, char** argv) {
	printf("starting server\n");
	int shm_id = shmget(SHM_KEY, 10000, IPC_CREAT | 0666); 			// get shared memory 
	const void* shm_pointer = shmat(shm_id, 0, 0); 							
	
	int sem_id = semget(SEM_KEY, 1, IPC_CREAT | 0666); 					// get semaphore 
	semctl(sem_id, 0, SETVAL, 5);																// init semaphore 

	if (errno) {
		fprintf(stderr, "error: %s\n", strerror(errno));
		exit(-1);
	}
	struct shmid_ds* shm_status;																// get shm status 

	struct sembuf op[1];							
	int retval;								

	op[0].sem_num = 0;							
	op[0].sem_flg = 0;							

	printf("server up and running\n");
	do {
		printf("running...\n");
		shmctl(SHM_KEY, IPC_STAT, shm_status);								// shm status 
		wait(&shm_status->shm_lpid);													// wait for last process 
		printf("p()\n");
		op[0].sem_op = 0;																			// P Operation
		if((retval = semop(sem_id, op, 1)) == 0) {						// ecexute P
			printf("message from %d ", &shm_status->shm_lpid);
			printf("%s\n", shm_pointer); 												// read shm
		} 
		else {																								// P operation error
			fprintf(stderr, "error: %s\n", strerror(errno));
			exit(-1);
		}
		printf("v()\n");
		op[0].sem_op = 1;																			// V Operation
		if((retval = semop(sem_id, op, 1)) != 0) {						// execute V and handle errors
			fprintf(stderr, "error: %s\n", strerror(errno));
			exit(-1);
		}
	} while(true);
	return 0;
}



```

Client
```
#include <sys/types.h>
#include <sys/stat.h>
#include <sys/wait.h>
#include <sys/ipc.h>
#include <sys/shm.h>
#include <sys/sem.h>
#include <signal.h>

#include <stdlib.h>
#include <string.h>
#include <stdio.h>

#include <unistd.h>
#include <errno.h>

#define SHM_KEY 12 
#define SEM_KEY 5

bool timeout = false;																		// timeout init
void timeout_handler(int sig);							

int main(int argc, char** argv) {
	printf("starting client\n");
 	int shm_id = shmget(SHM_KEY, 10000, 0666);						// get shared memory 
	const void* shm_pointer = shmat(shm_id, 0, 0); 				// attach shared memory 
												
	int sem_id = semget(SEM_KEY, 1, 0666);								// get semaphore

	if (errno) {
		fprintf(stderr, "error: %s\n", strerror(errno));
		exit(-1);
	}
	
	struct sembuf op[1];																	// Semaphore operations
	int retval;																						// return value semop()
	op[0].sem_num = 0;																		
	op[0].sem_flg = 0;																		// flag: wait 

	signal(SIGALRM, timeout_handler);											// set timeout handler 
	alarm(60);																						// alarm signal 60 seconds

	printf("client started\n");
	do {
		printf("sleep\n");
		sleep(3);																						// wait 3 seconds
		printf("wake-up\n");
		printf("p()\n");
		op[0].sem_op = 0;																		// P operation
		if((retval = semop(sem_id, op, 1)) == 0) {					//  execute P 
			printf("enter message: ");
			scanf("%s\n", shm_pointer);												// write in shared memory 
			printf("sending message ...");
		}	
		else {																							// P Operation error
			fprintf(stderr, "error: %s\n", strerror(errno));
			exit(-1);								
		}
		printf("V()\n");
		op[0].sem_op = 1;																		// V Operation
		if((retval = semop(sem_id, op, 1)) != 0) {					// execute V and handle errors
			fprintf(stderr, "error: %s\n", strerror(errno));
			exit(-1);
		}
	} while(!timeout);
	return 0;
}

void timeout_handler(int sig) {
	timeout = true;																				// timeout = true 
	printf("server timed out! exiting\n");								
}

```

The problem is that both parts dont do anything when executing p() from the semaphore. I tried debugging with printf()'s, but i dont get behind whats going on. 

I hope you can help me, i dont know whats wrong :(

I'm using gedit and compile it wth gcc by the way (no errors)

thanks a lot in advance

---

### Post by pedro_orange on 2008-01-22
I might be missing something, but you're using sem_op for all your semaphore signals/waits?

Have you tried using sem_wait(sem) and sem_post(sem)?

I recently did a patch for a client using a semaphore and I lost alot of hair from the experience!

I found this info useful: [http://www.linuxdevcenter.com/pub/a/linux/2007/05/24/semaphores-in-linux.html?page=1](http://www.linuxdevcenter.com/pub/a/linux/2007/05/24/semaphores-in-linux.html?page=1)

---

### Post by stroyan on 2008-01-22
I have several comments.

You should not use the IPC_STAT mechanism at all for this.
It is for tools like ipcs and not for normal programs using IPC.
(The wait for shm_lpid is really strange.)

You should not test for an error with just "if (errno)".
There is no convention that says a successfull call will set errno to 0.
You should test return values to look for errors and use errno for details.

You started the semaphore with a value of 5.  I can't imagine why.

All of your semops either test for 0 or increase the semaphore.
You never lower the semaphore value.  That can't be good.

You may need multiple semaphores to accomplish your goal.
Consider how many states the different processes may be in.
Draw a diagram with the different states and lines between those
states with labels showing how the transition will be triggered.
Consider that both reading and writing the shared memory need
to lock out changes by other processes.
Will you have multiple clients?  How will they interact with eachother?

---

### Post by iddqd on 2008-01-22
thanks a lot, its allready doing something and almost working.
T initialized the semaphore with 1.

I missunderstood the sem_op values, because they are just added to the current value.
 
So i use 
sem_op = -1 to lock 
and 
sem_op = 1 to unlock. 

Works fine, but the server doesnt wait for an action of the client, it keeps on printing the last message (or whatever is in memory).

wait(&shm_status->shm_lpid) seems not to work. 
I tried sem_wait() but the compiler didnt find it (its in a posix header i guess, but i want to stay in these).
I tried multiple clients as well, it works because the other client is locked then. 

Another problem is that the message appears on the serverside after a new one has been sent and not right away. Its allways "1 round" late.

Any ideas? I'll try out a little bit more tomorrow and maybe post the new code, but first i'll go to bed now since its 1 A.M. :)

---

