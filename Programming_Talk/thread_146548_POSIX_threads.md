---
title: "POSIX threads"
date: 2006-03-18
forum: Programming Talk
---

### Post by zootreeves on 2006-03-18
I've been trying to figure this out for a while now.

I am processing one line of a file at once and i need to process three lines at a time using 3 seperate threads. I can do this by opening three threads, then waiting for them all to finish then opening three more. 

But i need to do it so as soon as one thread finishes then another one is started (so there is always 3 working threads). 

Do you think this i possible using posix threads? Could someone show me how it could be done..

---

### Post by pharcyde on 2006-03-18
Did you try something like this?  I'm not sure if the syntax is 100% correct as I didn't try to compile it, but I'm fairly certain you get the Idea of what I'm trying to do.  This also doesn't take into account mutual exclusion so I don't know how a single file buffer will respond with multiple threads in this manner.

```

#include <pthread.h>
#include <stdio.h>
#define NUM_THREADS 3

/*Global File  Stream/Buffer*/

void *FileIO(void)
{
   while(/*Global FILE Stream/BUFFER IS != EOF*/)
   {
      /*DO STUFF on File Stream*/
   }
   pthread_exit(NULL);
}

int main (int argc, char *argv[])
{
  /*init Global File Stream/Buffer*/
   pthread_t threads[NUM_THREADS];
   int t;
   for(t = 0; t < NUM_THREADS; t++)
      pthread_create(&threads[t], NULL, FileIO, NULL);
}

```

---

### Post by zootreeves on 2006-03-18
thanks pharcyde but that's not really what i mean. I already have the file eopen, i need to process three lines at a time in parallel.


I don't think anyone will be able to follow this, but if it helps it is what i have got do far:

```
  x = 0;
  char current_ftp_lines[10][1000];
    /* foreach line of the file (which is an ftp) get the files */
  while(fgets(ftp_list_line, sizeof(ftp_list_line), ftp_file_pointer) != NULL ) {
    tidy_string(ftp_list_line);
   //parse_and_save_ftp_list_line(ftp_list_line, path);
      if (x < 3) {
       sprintf(current_ftp_lines[x], "%s", ftp_list_line);
      } else {
        printf("%s \n%s \n%s \n%s \n\n", current_ftp_lines[0], current_ftp_lines[1], current_ftp_lines[2], current_ftp_lines[3]);


  pthread_t             thread[THREADGROUPSIZE];
  void                 *status[THREADGROUPSIZE];
  int                   i;
  int                   rc=0;


  printf("Create/start some worker threads\n");
  for (i=0; i <THREADGROUPSIZE; ++i)
 {
    char ftp_line[] = "My line";
    rc = pthread_create(&thread[i], NULL, parse_and_save_ftp_list_line, current_ftp_lines[i]);
    checkResults("pthread_create()\n", rc);
  }
 
  printf("Wait for worker threads to complete, release their resources\n");
  for (i=0; i <THREADGROUPSIZE; ++i) {
    rc = pthread_join(thread[i], &status[i]);
    checkResults("pthread_join()\n", rc);
  }


  printf("\nContinue from here\n");


       x = 0;

      }
   x++;
  }
```

---

### Post by pharcyde on 2006-03-18
What i meant by my above code is allow each thread's callback to have access to your buffer variable, create the appropriate lock on the buffer var, and allow each thread to loop until the buffer end is reached.  This has the potential to operate on the data in an out of order fashion depending on how the O/S timeslices the appropriate threads.

Based on your code it looks like you are spawning three threads, then waiting for all three to finish before spawning three new threads.  What you want to do is spawn the appropriate # of threads in the beginning, and have each thread reference the buffer globally.  The 3 threads will continue to operate on the data until the end of buffer/file is reached.  I will try to show this in some pseduo-code below.

```


global char[255] mybuffer;
global buffer_count = 0;

main()
{
   mybuffer = open(somefile);

   for(i = 0; i < 3; i++)
      create_thread(myCallbackFunction);

   join_threads(i);
}

myCallbackFunction()
{
   while(buffer_count < 255)
   {
      mutex.lock()
      print mybuffer[buffer_count];
      buffer_count++;
      mutex.unlock()
   }
   thread_exit();
}


```

So each of the 3 theads will access the global buffer and operate on the data coming in. and exit once the buffer count is larger than the # of lines in the buffer.  Since each thread is incrementing the count you need to mutex that data so that multiple threads do not try to modify the variable simultaneously.

---

### Post by thumper on 2006-03-19
My first question would be WHY?  Why use three worker threads?  Adding threading a lot of the time just adds complexity for no real benefit.  In order to get your three worker threads using the same file handle you'll need to protect it with a mutex.  If the actual work that they are doing is trivial then adding threads will just slow it down due to the increased contention and locking.

If the work that they are doing is significant (for some definition of significant) and they are CPU bound then you may see a benefit with multiple threads **only if you have multiple processors**.  If there is network latency problems then threads may help.

---

### Post by zootreeves on 2006-03-19
Thanks again pharcyde, I think I understand what you mean now. But in your code would each thread process all the buffer? I need threads to do some very slow http downloading, I have two load blanace interent connection, so 4 downloads at the same time is much faster than one after the other.

---

### Post by LordHunter317 on 2006-03-19
I'll put it this way: unless the file is much, much larger than memory, there's no point in spawning multiple threads.  The I/O contention on trying to access the FD simulatenously will kill you.

In any case, the correct thing if that were the case would be to read n buffers of data from a single thread.  Each one of n workers gets a single buffer with enough data to busy it for a while, and works on it.  When a buffer is emptied, the I/O process refills it.  

If you're retrieving data over a slow network connection, then each worker thread should be responsible for a seperate connection: initialization, retrieving the data, etc.  The eaisest way to avoid contention problems and all the headaches they cause is to remove them completely.

---

### Post by zootreeves on 2006-03-19
When i try and use global:

    ```
global int timeout;
```

I get error: global undeclared (first use in this function). Are there special gcc flags needed to compile with global?

---

### Post by LordHunter317 on 2006-03-19
'global' isn't a valid C keyword.  NEver has been, never will be.  Global variables are defined through scope.

---

### Post by zootreeves on 2006-03-19
so how do i define a global var?

---

### Post by zootreeves on 2006-03-19
Is it possible to have a global variable that i could pass in an out of a thread. So this would work:

```
#define _MULTI_THREADED
#include <pthread.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>


//This is the global variable
int *j;

//This is the function run by the thread
void theThread(int *j)
{
  
  while (1) {
    j = (rand() / (int) 100000000) / 2;
    printf("thread set j as %d \n", j);
    sleep(5);
  }

}
 
int main(int argc, char **argv)
{
  pthread_t             thread[1];
  int                   rc=0;


//Create a thread
rc = pthread_create(&thread[0], NULL, theThread, j);

 
  while(1) {
    printf("but j is actually: %d \n", j);
    sleep(5);
  }
}

```

---

### Post by LordHunter317 on 2006-03-19
Yes, but you'll need to declare it **volatile** so that it isn't cached incorrectly.

---

### Post by zootreeves on 2006-03-19
thanks for your help LordHunter but even if i declare it as volatile it still won't work:

```
#define _MULTI_THREADED
#include <pthread.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>


//This is the global variable
volatile int j;

//This is the function run by the thread
void theThread(int *j)
{
  
  while (1) {
    j = (rand() / (int) 100000000) / 2;
    printf("thread set j as %d \n", j);
    sleep(5);
  }

}
 
int main(int argc, char **argv)
{
  pthread_t             thread[1];
  int                   rc=0;


//Create a thread
rc = pthread_create(&thread[0], NULL, theThread, j);

 
  while(1) {
    printf("but j is actually: %d \n", j);
    sleep(5);
  }
}

```

produces:

but j is actually: 0
thread set j as 9
but j is actually: 0
thread set j as 4
but j is actually: 0
thread set j as 8

---

### Post by LordHunter317 on 2006-03-19
Well, of course it didn't.  Your function is setting the passed pointer-to-int named j to a random address.  It's not affecting the global variable at all, it's scope is obscured by the function parameter.

Your thread doesn't even need to take an argument, but if you're going to make it take one, don't call it 'j'.

---

### Post by zootreeves on 2006-03-19
lol why did i not notice that. It working fine now. Thanks LordHunter

---

### Post by zootreeves on 2006-03-19
Is it possible to kill a thread from the main process?

---

### Post by zootreeves on 2006-03-19
sorry doesn't matter found pthread_kill

---

