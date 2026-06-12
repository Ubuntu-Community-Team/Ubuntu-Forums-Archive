---
title: "Help with semaphore"
date: 2009-12-02
forum: Programming Talk
---

### Post by NielsBhor on 2009-12-02
What I am trying to do is have two process or more use a semaphore so that only one may enter the critical section. I am having a problem with implementing. I played around with the code. Can someone help? Thank you! This is simulated so I won't be using sem_t open(file).

```

#include <stdio.h>
#include <sys/types.h>
#include <sys/ipc.h>
#include <sys/shm.h>
#include <time.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/sem.h>
#define KEY (1492)

typedef struct {
           int value;
           }  shared_mem;

           shared_mem   *counter;

int s;

union semun {
        int val;
        struct semid_ds *buf;
        ushort * array;
    } argument;

    argument.val=0;

    s=semget(KEY, 1, 0666 | IPC_CREAT);

    semctl(s,0, SETVAL, argument);

    int retval;

    int signal(){
        operations[0].sem_num=0;
        operations[0].sem_op=1;
        operations[0].sem_flg=0;
        return retval=semop(s,operations,1);
    }
    
    int wait(){
        operations[0].sem_num=0;
        operations[0].sem_op=-1;
        operations[0].sem_flg=0;
        return retval=semop(s,operations,1);
    }
    


   /* This fcn should increase the value of the shared variable "counter" all the way
   up to 50000 */

    clock_t         start, stop;
    double          elapsed;
    double        clock_per_second=10000;
    
   process1()
    {
    int i;        
    while(1){
    wait();
    start=clock();
    for(i=0;i<3000000;i++){
        counter->value++;
    }
    stop=clock();
    elapsed =((double) (stop - start)/clock_per_second);
 
     fprintf(stderr,"Elapsed time of process 1 = %lf\n The value of counter is %d\n", elapsed, counter->value);
    signal();

    exit(0);}

    }

   /* This fcn should also increase the value of the shared memory variable "counter" all the way
   up to 50000 */

   process2()
    {
        
    int i;        
    while(1){
    wait();
    start=clock();
    for(i=0;i<3000000;i++){
        counter->value++;
    }
    stop=clock();
    elapsed =((double) (stop - start)/clock_per_second);
 
     fprintf(stderr,"Elapsed time of process 1 = %lf\n The value of counter is %d\n", elapsed, counter->value);
    signal();

    exit(0);}

    }

/*        The Main Body                    */

 main()
  {
        key_t        key = IPC_PRIVATE;  /* shared memory key */
        int        shmid;      /* shared memory ID */
        shared_mem    *shmat1;   /* function to allocate shared memory */
        int        pid1;        /* process id for child1 */
        int        pid2;        /* process id for child2 */
        clock_t         start, stop;
        double         elapsed;
        int         i;

    

        
        /* attempts to attach to an existing memory segment    */

        if (( shmid = shmget(key, sizeof(int), IPC_CREAT | 0666)) < 0)
            {
             perror("shmget");
             exit(1);
             }

        /*attempts the shared memory segment    */

        if((counter = (shared_mem *)shmat(shmid, NULL, 0)) == (shared_mem *) -1)
            {
            perror("shmat");
            exit(2);
            }

        /*initializing shared memory to 0 */
         
         counter->value = 0;
    
        /* fork process one here */    
        pid1=fork();
        if(pid1<0){
            fprintf(stderr,"Fork() failed\n");
            exit(3);
        }

        if (pid1 == 0) {
            fprintf(stderr,"Hello from Child (No. %i)\n", getpid());
            process1();
            exit(0);
        }
        
        
        /* fork process two here */
        pid2=fork();
        if(pid2<0){
            fprintf(stderr,"Fork() failed\n");
            exit(4);
        }

        if (pid2 == 0) {
                fprintf(stderr,"Hello from Child (No. %i)\n",getpid());
            process2();
            exit(0);
        }

        
        /* parent waits (use wait();) for child processes to finish. */
        if (pid1>0){
            fprintf(stderr,"Parent Process with PID: %d\n", getpid());
                        
            wait(pid1);
            
                        
        }

        if (pid2>0){
            start=clock();                
            wait(pid2);
            stop=clock();            
            fprintf(stderr,"Elapsed time of the parent process = %lf\n", elapsed);    
            
            }

                
           /*deallocate shared memory */
              if(shmctl(shmid, IPC_RMID, (struct shmid_ds *)0)== -1){
                perror("shmctl");
              exit(-1);
             }
        exit(0);

    }

```

Any input or help is greatly appreciated. I used the peterson solution, that came out good. But the semaphores is different.

---

### Post by grayrainbow on 2009-12-02
If I'm getting it right you want one process to do ++ 50000 times, then wait while another process do ++ 50000 times, and then same thing all over until every process do it 30000000. If that's the case you'll need two semaphores, and every process should signal to other process semaphore, and wait to it's own, just be careful to not ended with single process "owning" both at the same time. Wait and signal should happen in the loop, and one of semaphores should be in signal state or signaled by the parent process. If you going to wait only for second process, first one should have its semaphore signal at beginning, otherwise you want get exact time.

---

### Post by NielsBhor on 2009-12-02
Thank you for your input. I fail to update my comments.

Further clearification, my problem is implementing a semaphore. I never did this before. Looked up google and learned about semctl, semget...

If I want say to implement two semaphores as you said I sould do

int id;
id=semget(KEY,0,2);
semctl(id,...)

However, the operations of wait and signal must be atomic. When you said use wait and signal inside the loop, will that make it atomic? 

Another thing is I learned of semop which would make a decrement or increment by using

semaphore.semop=-1 for increment or semaphore.semop=1

I worked really hard on this. Right now, I'm very confused how semop works, semctl, and semget works.

---

### Post by dwhitney67 on 2009-12-02
For those who prefer to use sem_open() and sem_wait(), I've included a modified version of the OP's code below.

It's my first time using a sem_t object, so I do not know if I used it correctly.  The program runs, produces output, but I do not know if it is correct.
```

#include <stdio.h>
#include <sys/shm.h>
#include <sys/wait.h>
#include <semaphore.h>
#include <fcntl.h>
#include <time.h>
#include <stdlib.h>
#include <unistd.h>
#include <assert.h>

typedef struct
{
   int    value;
   sem_t* semaphore;
} shared_mem;

const char* sem_name  = "/mySemaphore";
int         shmid     = -1;
shared_mem* counter   = 0;

double time_elapsed(struct timespec stop, struct timespec start)
{
   struct timespec delta;

   delta.tv_sec  = stop.tv_sec  - start.tv_sec;
   delta.tv_nsec = stop.tv_nsec - start.tv_nsec;

   if (delta.tv_nsec < 0)
   {
      --delta.tv_sec;
      delta.tv_nsec += 1000000000L;
   }

   return (double)(delta.tv_sec + (double)delta.tv_nsec / 1000000000L);
}

void teardown()
{
   if (counter && counter->semaphore)
   {
      assert(sem_close(counter->semaphore) == 0);
   }
   if (sem_name)
   {
      assert(sem_unlink(sem_name) == 0);
   }

   shmctl(shmid, IPC_RMID, (struct shmid_ds*)0);
}

int setup()
{
   /* create semaphore */
   sem_t* semaphore = sem_open(sem_name, O_CREAT);

   if (semaphore == (sem_t*) SEM_FAILED)
   {
      perror("sem_open");
      return -1;
   }

   /* attempts to attach to an existing memory segment */
   key_t key   = IPC_PRIVATE;
   shmid = shmget(key, sizeof(shared_mem), IPC_CREAT | 0666);

   if (shmid < 0)
   {
      teardown();
      perror("shmget");
      return -2;
   }

   /* attempts the shared memory segment */
   counter = (shared_mem*) shmat(shmid, NULL, 0);

   if (counter == (shared_mem*) -1)
   {
      teardown();
      perror("shmat");
      return -3;
   }
   counter->value = 0;
   counter->semaphore = semaphore;

   return 0;
}

void childProcess()
{
   struct timespec start;
   struct timespec stop;

   for (int iter = 0; iter < 25; ++iter)
   {
      sem_wait(counter->semaphore);

      clock_gettime(CLOCK_REALTIME, &start);

      for (int i = 0; i < 3000000; ++i)
      {
         ++counter->value;
      }

      clock_gettime(CLOCK_REALTIME, &stop);

      fprintf(stdout, "Elapsed time of child process = %lf\nThe value of counter is %d\n",
              time_elapsed(stop, start), counter->value);
   }
}

int main()
{
   if (setup() != 0)
   {
      return -1;
   }
   
   /* fork process one here */
   int pid1 = fork();

   if (pid1 == 0)
   {
      fprintf(stdout, "Hello from Child (No. %i)\n", getpid());
      childProcess();
      exit(0);
   }

   /* fork process two here */
   int pid2 = fork();

   if (pid2 == 0)
   {
      fprintf(stdout, "Hello from Child (No. %i)\n", getpid());
      childProcess();
      exit(0);
   }

   struct timespec start;
   struct timespec stop;
   int             childStatus = 0;

   clock_gettime(CLOCK_REALTIME, &start);

   fprintf(stdout, "Parent Process with PID: %d\n", getpid());

   if (pid1 > 0)
   {
      /* parent waits for first child process to finish */
      waitpid(pid1, &childStatus, 0);
   }
   if (pid2 > 0)
   {
      /* parent waits for second child process to finish */
      waitpid(pid2, &childStatus, 0);
   }

   clock_gettime(CLOCK_REALTIME, &stop);

   fprintf(stdout, "Elapsed time of the parent process = %lf\n", time_elapsed(stop, start));

   teardown();

   return 0;
}

```

---

### Post by NielsBhor on 2009-12-02
Thank you for the code. Unfortunately, I'm still having some problems.

It seems that when I compiled this code I get the error in the function childprocess(). I cannot declare an int inside the 'for' loop unless I'm in c99 mode. I fixed this by declaring the 'int' outside, then using it in the 'for' loop.

Furthermore, recompiling it gives me the message that the function teardown() has an undefined reference in 'sem_close', 'sem_unlink'. And a slew of other problems. This may be that I didn't compile it properly. I used the stand cmd: gcc main.c to compile.

Hmm...Semaphores is tougher than I thought.

---

### Post by dwhitney67 on 2009-12-02
> **NielsBhor said:**
> Thank you for the code. Unfortunately, I'm still having some problems.

It seems that when I compiled this code I get the error in the function childprocess(). I cannot declare an int inside the 'for' loop unless I'm in c99 mode. I fixed this by declaring the 'int' outside, then using it in the 'for' loop.

Furthermore, recompiling it gives me the message that the function teardown() has an undefined reference in 'sem_close', 'sem_unlink'. And a slew of other problems. This may be that I didn't compile it properly. I used the stand cmd: gcc main.c to compile.

Hmm...Semaphores is tougher than I thought.

I always use the GNU-1999 version of the GCC compiler.  To build the app I posted, do the following:
```

gcc -Wall -pedantic -std=gnu99 SemTest.c -lrt -o semtest

```

---

### Post by PmDematagoda on 2009-12-03
The code was still a little off because the output is erroneous, the below code produces the correct output:-
```
#include <stdio.h>
#include <sys/shm.h>
#include <sys/wait.h>
#include <semaphore.h>
#include <fcntl.h>
#include <time.h>
#include <stdlib.h>
#include <unistd.h>
#include <assert.h>

typedef struct
{
   int    value;
   sem_t* semaphore;
} shared_mem;

const char* sem_name  = "/mySemaphore";
int         shmid     = -1;
shared_mem* counter   = 0;

double time_elapsed(struct timespec stop, struct timespec start)
{
   struct timespec delta;

   delta.tv_sec  = stop.tv_sec  - start.tv_sec;
   delta.tv_nsec = stop.tv_nsec - start.tv_nsec;

   if (delta.tv_nsec < 0)
   {
      --delta.tv_sec;
      delta.tv_nsec += 1000000000L;
   }

   return (double)(delta.tv_sec + (double)delta.tv_nsec / 1000000000L);
}

void teardown()
{
   if (counter && counter->semaphore)
   {
      assert(sem_close(counter->semaphore) == 0);
   }
   if (sem_name)
   {
      assert(sem_unlink(sem_name) == 0);
   }

   shmctl(shmid, IPC_RMID, (struct shmid_ds*)0);
}

int setup()
{
   /* create semaphore */
   sem_t* semaphore = sem_open(sem_name, O_CREAT);

   if (semaphore == (sem_t*) SEM_FAILED)
   {
      perror("sem_open");
      return -1;
   }

**[COLOR="Red"]   sem_init (semaphore, 1, 1);[/COLOR]**

   /* attempts to attach to an existing memory segment */
   key_t key   = IPC_PRIVATE;
   shmid = shmget(key, sizeof(shared_mem), IPC_CREAT | 0666);

   if (shmid < 0)
   {
      teardown();
      perror("shmget");
      return -2;
   }

   /* attempts the shared memory segment */
   counter = (shared_mem*) shmat(shmid, NULL, 0);

   if (counter == (shared_mem*) -1)
   {
      teardown();
      perror("shmat");
      return -3;
   }
   counter->value = 0;
   counter->semaphore = semaphore;

   return 0;
}

void childProcess()
{
   struct timespec start;
   struct timespec stop;

   for (int iter = 0; iter < 25; ++iter)
   {
      sem_wait(counter->semaphore);

      clock_gettime(CLOCK_REALTIME, &start);

      for (int i = 0; i < 3000000; ++i)
      {
         ++counter->value;
      }

      clock_gettime(CLOCK_REALTIME, &stop);

      fprintf(stdout, "Elapsed time of child process = %lf\nThe value of counter is %d\n",
              time_elapsed(stop, start), counter->value);
[COLOR="Red"]**      sem_post(counter->semaphore);**[/COLOR]

   }
}

int main()
{
  int sem_val;

   if (setup() != 0)
   {
      return -1;
   }
[COLOR="Blue"][B]   sem_getvalue (counter->semaphore, &sem_val);

   printf ("Value of semaphore: %d\n", sem_val);
[/B][/COLOR]
   /* fork process one here */
   int pid1 = fork();

   if (pid1 == 0)
   {
      fprintf(stdout, "Hello from Child (No. %i)\n", getpid());
      childProcess();
      exit(0);
   }

   /* fork process two here */
   int pid2 = fork();

   if (pid2 == 0)
   {
      fprintf(stdout, "Hello from Child (No. %i)\n", getpid());
      childProcess();
      exit(0);
   }

   struct timespec start;
   struct timespec stop;
   int             childStatus = 0;

   clock_gettime(CLOCK_REALTIME, &start);

   fprintf(stdout, "Parent Process with PID: %d\n", getpid());

   if (pid1 > 0)
   {
      /* parent waits for first child process to finish */
      waitpid(pid1, &childStatus, 0);
   }
   if (pid2 > 0)
   {
      /* parent waits for second child process to finish */
      waitpid(pid2, &childStatus, 0);
   }

   clock_gettime(CLOCK_REALTIME, &stop);

   fprintf(stdout, "Elapsed time of the parent process = %lf\n", time_elapsed(stop, start));

   teardown();

   return 0;
}
```
The semaphore was not initialised hence it would not have provided a real lock, and only sem_wait was used which only locks the semaphore(which is not real in the previous case either because sem_wait blocks *only* if the semaphore value is 0) and it is not unlocked once the critical region has passed. The reason the program did not get locked up was because the value of the semaphore was high enough for all the loops.

---

### Post by grayrainbow on 2009-12-03
You could try search for something like posix and semophore, and I'm sure you'll find plenty of examples. Also it will be good to install posix man pages.
About the atomic stuff...the place from where you'll call wait/signal want be what defines are they atomic or not. Generally you could look at semaphores as atomic operations only in regardless to your own more "higher level" code, and usually one want they to be interruptable, meaning that something like Unix signal can stop them, btw even win 7 start using Unix like signals for implementing their locks, exactly becouse of interruptability.
If you are curious more in how to implement them yourself:
[http://tomoyo.sourceforge.jp/cgi-bin/lxr/source/kernel/semaphore.c]("http://tomoyo.sourceforge.jp/cgi-bin/lxr/source/kernel/semaphore.c")

---

### Post by dwhitney67 on 2009-12-03
> **PmDematagoda said:**
> The code was still a little off because the output is erroneous, the below code produces the correct output:-


Thanks for the corrections; it was my first stab at using *nix semaphores.

P.S.  I performed further research; I found that one can initialize the semaphore's value using the constructor.  Thus I should have had something like this in my code:
```

   /* create semaphore */
   sem_t* semaphore = sem_open(sem_name, O_CREAT, 0600, 1);

```
This initializes the semaphore to a value of 1.

---

### Post by NielsBhor on 2009-12-03
Okay. Thank you for helping me out. I think I understand Semaphores a little clearer now. I'm going to try and expand this concept a little more. Challenging project for me since I never used semaphores.

---

### Post by Can+~ on 2009-12-03
> **NielsBhor said:**
> Okay. Thank you for helping me out. I think I understand Semaphores a little clearer now. I'm going to try and expand this concept a little more. Challenging project for me since I never used semaphores.

I think you should study them "conceptually" first before attempting to use them on C. I would recommend [Silberschatz' Opearting System Concepts]("http://www.amazon.com/Operating-System-Concepts-Abraham-Silberschatz/dp/0471694665") book.

And also, +1 for using semaphore.h and -lpt, it's way better than System V's counterpart (also, man 3 sem_init).

The most "clear" way to understand semaphores, is considering them as bags with tokens. Each process that wants to enter it's critical section, takes a token out of the bag. Each one that finishes, put one in the bag. If the bag is empty, then it should wait for another process to finish. A single token bag is called a mutex (for mutual exclusion).

---

