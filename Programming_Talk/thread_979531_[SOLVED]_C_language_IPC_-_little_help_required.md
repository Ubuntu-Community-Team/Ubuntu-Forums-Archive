---
title: "[SOLVED] C language IPC - little help required"
date: 2008-11-12
forum: Programming Talk
---

### Post by Penteado on 2008-11-12
Hello, i've an assigment to my C programming class for creating multiple processes aceding a shared memory segment.

      I've managed to get my program to work but it happens that allows 2 different processes access at the same type the shared memory. All semaphore seems to be implemented ok. Dont know where the problem is. So if anyone understands the concept and have some experience with this issue i would appreciate a lot if you can help me figure this out.
 
     I'll post my program file and the sema.h file that support the interface for this IPC programming.

prod_cons.c :

```
#include <stdio.h>
#include "sema.h"


#define MAX_CHILD 7
#define N 10
#define LIFETIME 30
#define SHMKEY (key_t)0x10

/**
* Functions declaration
*/

void producer();
void consumer();


/**
* Globals var
*/
int in,out;
int buf[N];
int shmid;




int *ptr;
char *addr;

semaphore mutex,full,empty;



int main()
{

/**
* Shared memory allocation
*/

shmid = shmget(SHMKEY, 128,0777|IPC_CREAT);
addr = (char*)shmat(shmid, 0, 0);
ptr = (int*)addr;

/**
* Sempahore Init
*/

mutex = init_sem (1);
empty = init_sem (N);
full = init_sem(0);

/**
* Variables
*/

in = 0;
out = 0;

pid_t child_pid[MAX_CHILD],wait_pid;
int i,j,child_stat;

//srand((unsigned int)time(NULL));

for(i = 0;i < MAX_CHILD;i++)
{
	child_pid[i] = fork();
	switch(child_pid[i])
	{
		case -1:
			perror("fork failed");
			exit(1);
		break;
		
		case 0:    /**  CHILD PROCESS, producer or consumer */
			alarm(LIFETIME);
			
			
			if(i<1){  /** one producer and multiple consumers */
			
				producer();
			}
			else 
			{
				
				consumer();
			};
		break;

		default: /** PARENT PROCESS ,only controls child processes termination*/
		if (i == (MAX_CHILD - 1))
		{				
	  		for (j = 0; j < MAX_CHILD; ++j)
	  		{
	    			wait_pid = wait (&child_stat);
	    			if (wait_pid == -1)
	    			{
	      				perror ("wait failed");
	      				errno = 0;
	    			}
	  		}
	  		printf ("All child processes have terminated.\n");
	  		rel_sem(full);    /** release memory blocks */
			rel_sem(empty);
			rel_sem(mutex);
	}
			

	}
}

return 0;
}

/**
* Functions
*/

void producer()
{
	
	//alarm(LIFETIME);
	for(;;)
	{	
		
		sleep(2);
		int item=rand () % 50;
		printf("[PRODUCER] waiting to enter critical region \n");
		P(empty);
		P(mutex);
			ptr[in] = item;
			//*(ptr+in) = item;
			in = (in+1)%N;
			printf("Produced item: %d item at critical region \n", item);
			
		V(mutex);
		V(full);
		printf("[PRODUCER] out of critical region \n");
		sleep(2);
	}


}

void consumer()
{
	int item=0;
	//alarm(LIFETIME);
	for(;;)
	{	
		
		sleep(2);
		printf("[CONSUMER] Waiting to enter critical region \n");
		P(full);
		P(mutex);
			item = ptr[out];
			//item = *(ptr+out);
			out = (out+1)%N;
			printf("Consumed item %d on critical region \n",item);
			
		V(mutex);
		V(empty);
		printf("[CONSUMER] Out of critical region \n");
		sleep(2);

	}


}
```

sema.h (provided by teacher):
```
/* Implementing P(s) and V(s) using UNIX semaphores.
 *
 * exit (1):	error calling fork ()
 * exit (2):	error calling semget ()
 * exit (3):	error calling semctl ()
 * exit (4):	error calling semop ()
 *
 * "union semun" isn't declared using SunOS or Linux 2.2.x and above.
 * Starting with Linux 2.2.x the macro _SEM_SEMUN_UNDEFINED must be
 * checked to determine if Linux knows about the union. Up to Linux
 * 2.0.x "semctl" needs all four paramters (even then when the last
 * parameter isn't used, e.g. using IPC_RMID).
 *
 * gcc [-DSunOS] [-DLinux] -o sema_pv sema_pv.c
 *
 * File: sema_pv.c			Author: S. Gross
 * Date: 18.01.2001
 *
 */

/* starting with Linux 2.2.x the macro "_SVID_SOURCE" must be defined
 * for "System V IPC"
 */
#ifdef Linux
  #define _SVID_SOURCE
#endif

#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <sys/ipc.h>
#include <sys/sem.h>
#include <unistd.h>
#include <errno.h>
#include <time.h>

#define SEM_KEY	      IPC_PRIVATE	/* create private semaphore	*/
#define SEM_PERM      0600		/* access permissions		*/

typedef int	semaphore;		/* semaphore (handle) type	*/
#if (_SEM_SEMUN_UNDEFINED == 1) || defined(SunOS)
  typedef union semun
    {
      int		val;		/* cmd: SETVAL			*/
      struct semid_ds	*buf;		/* cmd: IPC_STAT, IPC_SET	*/
      ushort		*array;		/* cmd: GETALL, SETALL		*/
    } semunion;
#endif

/* Create and initialize a semaphore set with one semphore. The
 * semaphore has index 0.
 *
 * input parameter:	value		initial value for semaphore
 * output parameter:	none
 * return value:	semaphore handle
 * side effects:	none
 *
 */
semaphore init_sem (int value)
{
  union semun arg;			/* parameter for semctl		*/
  int	      semid;			/* semaphore handle		*/

  semid = semget (SEM_KEY, 1, IPC_CREAT | SEM_PERM);
  if (semid == -1)
  {
    perror ("init_sem: semget failed");
    exit (2);
  };
  arg.val = value;
  if (semctl (semid, 0, SETVAL, arg) == -1)
  {
    perror ("init_sem: semctl failed");
    exit (3);
  };
  return semid;
}


/* Release a semaphore set.
 *
 * input parameter:	sem	semaphore handle
 * output parameter:	none
 * return value:	none
 * side effects:	none
 *
 */
void rel_sem (semaphore sem)
{
  union semun tmp;			/* for Linux up to 2.0.x	*/

  if (semctl (sem, 0, IPC_RMID, tmp) == -1)
  {
    perror ("rel_sem: semctl failed");
    exit (3);
  };  
}


/* P() operation for a semaphore set with one semaphore.
 *
 * input parameter:	sem	semaphore handle
 * output parameter:	none
 * return value:	none
 * side effects:	none
 *
 */
void P (semaphore sem)
{
  struct sembuf tmp;

  tmp.sem_num = 0;
  tmp.sem_op  = -1;
  tmp.sem_flg = 0;
  if (semop (sem, &tmp,  (size_t) 1) == -1)
  {
    perror ("P: semop failed");
    exit (4);
  };
}


/* V() operation for a semaphore set with one semaphore.
 *
 * input parameter:	sem	semaphore handle
 * output parameter:	none
 * return value:	none
 * side effects:	none
 *
 */
void V (semaphore sem)
{
  struct sembuf tmp;

  tmp.sem_num = 0;
  tmp.sem_op  = 1;
  tmp.sem_flg = 0;
  if (semop (sem, &tmp,  (size_t) 1) == -1)
  {
    perror ("V: semop failed");
    exit (4);
  };
}
```


If you can find something else that is not properly coded, please let me know so i can trully understand the concept.

Thank You a zillion times.

---

### Post by Penteado on 2008-11-12
I figured out that variables in e out are not inherit to the separated processes. actually the semaphore's are OK.

   How come they are not inherit?

   Consumer keeps consuming at the same position!


   Thank you.

---

### Post by dwhitney67 on 2008-11-12
I think the main thing that is confusing you is the use of fork().

The fork() call will create a separate process, which will inherit some of the attributes of the parent.  However, the attributes that are inherited are NOT shared between sibling processes.

Thus, if the forked process inherits an integer variable, it can modify the value all day long, and the parent and any sibling process(es) will never see the change.  This is what is occurring with respect to your consumer processes.  They each have a copy of the 'out' variable, thus when you increment the value within one consumer process, the others do not see the change.

You need to consider placing the 'out' variable within shared memory.  As for the 'in' variable used by the producer, this is not an issue in your application because you only have one producer.  If you had 2 or more, then it would be an issue.

In case you do not have manpages installed on your system, I'd suggest you get them:
```
sudo apt-get install manpages-dev
```

Here's the manpage for fork():
```

FORK(2)                    Linux Programmer&#8217;s Manual                   FORK(2)

NAME
       fork - create a child process

SYNOPSIS
       #include <unistd.h>

       pid_t fork(void);

DESCRIPTION
       fork()  creates a new process by duplicating the calling process.  The new process, referred to as the child, is an exact duplicate of the calling process, referred to as the parent,
       except for the following points:

       *  The child has its own unique process ID, and this PID does not match the ID of any existing process group (setpgid(2)).

       *  The child&#8217;s parent process ID is the same as the parent&#8217;s process ID.

       *  The child does not inherit its parent&#8217;s memory locks (mlock(2), mlockall(2)).

       *  Process resource utilizations (getrusage(2)) and CPU time counters (times(2)) are reset to zero in the child.

       *  The child&#8217;s set of pending signals is initially empty (sigpending(2)).

       *  The child does not inherit semaphore adjustments from its parent (semop(2)).

       *  The child does not inherit record locks from its parent (fcntl(2)).

       *  The child does not inherit timers from its parent (setitimer(2), alarm(2), timer_create(3)).

       *  The child does not inherit outstanding asynchronous I/O operations from its parent (aio_read(3), aio_write(3)).

       The process attributes in the preceding list are all specified in POSIX.1-2001.  The parent and child also differ with respect to the following Linux-specific process attributes:

       *  The child does not inherit directory change notifications (dnotify) from its parent (see the description of F_NOTIFY in fcntl(2)).

       *  The prctl(2) PR_SET_PDEATHSIG setting is reset so that the child does not receive a signal when its parent terminates.

       *  Memory mappings that have been marked with the madvise(2) MADV_DONTFORK flag are not inherited across a fork().

       *  The termination signal of the child is always SIGCHLD (see clone(2)).

       Note the following further points:

       *  The child process is created with a single thread &#8212; the one that called fork().  The entire virtual address space of the parent is replicated in the child, including the states of
          mutexes, condition variables, and other pthreads objects; the use of pthread_atfork(3) may be helpful for dealing with problems that this can cause.

       *  The  child  inherits  copies  of the parent&#8217;s set of open file descriptors.  Each file descriptor in the child refers to the same open file description (see open(2)) as the corre-
          sponding file descriptor in the parent.  This means that the two descriptors share open file status flags, current file offset, and signal-driven I/O attributes (see the  descrip-
          tion of F_SETOWN and F_SETSIG in fcntl(2)).

       *  The  child inherits copies of the parent&#8217;s set of open message queue descriptors (see mq_overview(7)).  Each descriptor in the child refers to the same open message queue descrip-
          tion as the corresponding descriptor in the parent.  This means that the two descriptors share the same flags (mq_flags).

       *  The child inherits copies of the parent&#8217;s set of open directory streams (see opendir(3)).  POSIX.1-2001 says that the correspoding directory streams in the parent  and  child  may
          share the directory stream positioning; on Linux/glibc they do not.

RETURN VALUE
       On  success, the PID of the child process is returned in the parent, and 0 is returned in the child.  On failure, -1 is returned in the parent, no child process is created, and errno
       is set appropriately.

ERRORS
       EAGAIN fork() cannot allocate sufficient memory to copy the parent&#8217;s page tables and allocate a task structure for the child.

       EAGAIN It was not possible to create a new process because the caller&#8217;s RLIMIT_NPROC resource limit was encountered.   To  exceed  this  limit,  the  process  must  have  either  the
              CAP_SYS_ADMIN or the CAP_SYS_RESOURCE capability.

       ENOMEM fork() failed to allocate the necessary kernel structures because memory is tight.

CONFORMING TO
       SVr4, 4.3BSD, POSIX.1-2001.

NOTES
       Under  Linux, fork() is implemented using copy-on-write pages, so the only penalty that it incurs is the time and memory required to duplicate the parent&#8217;s page tables, and to create
       a unique task structure for the child.

EXAMPLE
       See pipe(2) and wait(2).

SEE ALSO
       clone(2), execve(2), setrlimit(2), unshare(2), vfork(2), wait(2), capabilities(7), credentials(7)

COLOPHON
       This page is part of release 2.78 of the Linux man-pages project.  A description of the project, and information about reporting bugs, can be found at  http://www.kernel.org/doc/man-
       pages/.

Linux                             2008-01-13                           FORK(2)

```

---

### Post by Penteado on 2008-11-15
Thanks a lot, you were right.

   Added IN & OUT variables to shared memory they are now visible to all processes. 


   ;) Thanks!

---

