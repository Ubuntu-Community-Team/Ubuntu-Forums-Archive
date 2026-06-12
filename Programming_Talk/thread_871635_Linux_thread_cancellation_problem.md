---
title: "Linux thread cancellation problem"
date: 2008-07-27
forum: Programming Talk
---

### Post by arielsegal on 2008-07-27
Hello,
I am learning to code with Linux, and doing some examples with threads. I'm trying to use a cancellation point with no success. I have looked around in the Internet and found an example from an IBM site, compiled and ran it, but it doesn't give me the desired results. The cancellation point just doesn't seem to work. The thread is canceled immediately and does not wait for the cancellation point.
I'm using Ubunto 8.04 on a Pentium 4 machine.
Does anyone know what the problem is?
the code:
> 
#include <pthread.h>
#include <unistd.h>
#include <stdio.h>

#define checkResults printf

void cleanupHandler(void *parm) {
  printf("Inside cancellation cleanup handler\n");
}

void *threadfunc(void *parm)
{
  unsigned int  i=0;
  int           rc=0, oldState=0;
  printf("Entered secondary thread\n");
  pthread_cleanup_push(cleanupHandler, NULL);
  rc = pthread_setcancelstate(PTHREAD_CANCEL_DISABLE, &oldState);
  checkResults("%d = pthread_setcancelstate()\n", rc);
  /* Allow cancel to be pending on this thread */
  sleep(2);
  while (1) {
    printf("Secondary thread is now looping\n");
    ++i;
    sleep(1);
    /* pthread_testcancel() has no effect until cancelability is enabled.*/
    /* At that time, a call to pthread_testcancel() should result in the */
    /* pending cancel being acted upon                                   */
    pthread_testcancel();
    if (i == 5) {
      printf("Cancel state set to ENABLE\n");
      rc = pthread_setcancelstate(PTHREAD_CANCEL_ENABLE,&oldState);
      checkResults("%d = pthread_setcancelstate(2)\n", rc);
      /* Now, cancellation points will allow pending cancels
         to get through to this thread */
    }
  } /* infinite */
  pthread_cleanup_pop(0);
  return NULL;
}

int main(int argc, char **argv)
{
  pthread_t             thread;
  int                   rc=0;
  void                 *status=NULL;

  printf("Enter Testcase - %s\n", argv[0]);

  /* Create a thread using default attributes */
  printf("Create thread using the NULL attributes\n");
  rc = pthread_create(&thread, NULL, threadfunc, NULL);
  checkResults("%d = pthread_create(NULL)\n", rc);

  sleep(1);
  printf("Cancel the thread\n");
  rc = pthread_cancel(thread);
  checkResults("%d = pthread_cancel()\n", rc);

  rc = pthread_join(thread, &status);
  if (status != PTHREAD_CANCELED) {
    printf("Thread returned unexpected result!\n");
    return 1;
  }
  printf("Main completed\n");
  return 0;
}

Results:
Create thread using the NULL attributes
Entered secondary thread
0 = pthread_setcancelstate()
0 = pthread_create(NULL)
Cancel the thread
0 = pthread_cancel()
Secondary thread is now looping
Secondary thread is now looping
Secondary thread is now looping
Secondary thread is now looping
Secondary thread is now looping
Cancel state set to ENABLE
0 = pthread_setcancelstate(2)
Inside cancellation cleanup handler
Main completed

Expected results:
Create thread using the NULL attributes
Entered secondary thread
0 = pthread_setcancelstate()
0 = pthread_create(NULL)
Cancel the thread
0 = pthread_cancel()
Secondary thread is now looping
Secondary thread is now looping
Secondary thread is now looping
Secondary thread is now looping
Secondary thread is now looping
Cancel state set to ENABLE
Secondary thread is now looping
0 = pthread_setcancelstate(2)
Inside cancellation cleanup handler
Main completed

---

### Post by Lster on 2008-07-27
Can you repost your code with "[code]" tags? It makes it a lot easier to read! :)

---

### Post by arielsegal on 2008-07-27
sorry, here is the code again:
```

#include <pthread.h>
#include <unistd.h>
#include <stdio.h>

#define checkResults printf

void cleanupHandler(void *parm) {
printf("Inside cancellation cleanup handler\n");
}

void *threadfunc(void *parm)
{
unsigned int i=0;
int rc=0, oldState=0;
printf("Entered secondary thread\n");
pthread_cleanup_push(cleanupHandler, NULL);
rc = pthread_setcancelstate(PTHREAD_CANCEL_DISABLE, &oldState);
checkResults("%d = pthread_setcancelstate()\n", rc);
/* Allow cancel to be pending on this thread */
sleep(2);
while (1) {
printf("Secondary thread is now looping\n");
++i;
sleep(1);
/* pthread_testcancel() has no effect until cancelability is enabled.*/
/* At that time, a call to pthread_testcancel() should result in the */
/* pending cancel being acted upon */
pthread_testcancel();
if (i == 5) {
printf("Cancel state set to ENABLE\n");
rc = pthread_setcancelstate(PTHREAD_CANCEL_ENABLE,&oldS tate);
checkResults("%d = pthread_setcancelstate(2)\n", rc);
/* Now, cancellation points will allow pending cancels
to get through to this thread */
}
} /* infinite */
pthread_cleanup_pop(0);
return NULL;
}

int main(int argc, char **argv)
{
pthread_t thread;
int rc=0;
void *status=NULL;

printf("Enter Testcase - %s\n", argv[0]);

/* Create a thread using default attributes */
printf("Create thread using the NULL attributes\n");
rc = pthread_create(&thread, NULL, threadfunc, NULL);
checkResults("%d = pthread_create(NULL)\n", rc);

sleep(1);
printf("Cancel the thread\n");
rc = pthread_cancel(thread);
checkResults("%d = pthread_cancel()\n", rc);

rc = pthread_join(thread, &status);
if (status != PTHREAD_CANCELED) {
printf("Thread returned unexpected result!\n");
return 1;
}
printf("Main completed\n");
return 0;
} 

```

---

### Post by drubin on 2008-07-27
> **arielsegal said:**
> sorry, here is the code again:
[PHP]
#include <pthread.h>
#include <unistd.h>
#include <stdio.h>

#define checkResults printf

void cleanupHandler(void *parm) {
printf("Inside cancellation cleanup handler\n");
}

void *threadfunc(void *parm)
{
unsigned int i=0;
int rc=0, oldState=0;
printf("Entered secondary thread\n");
pthread_cleanup_push(cleanupHandler, NULL);
rc = pthread_setcancelstate(PTHREAD_CANCEL_DISABLE, &oldState);
checkResults("%d = pthread_setcancelstate()\n", rc);
/* Allow cancel to be pending on this thread */
sleep(2);
while (1) {
printf("Secondary thread is now looping\n");
++i;
sleep(1);
/* pthread_testcancel() has no effect until cancelability is enabled.*/
/* At that time, a call to pthread_testcancel() should result in the */
/* pending cancel being acted upon */
pthread_testcancel();
if (i == 5) {
printf("Cancel state set to ENABLE\n");
rc = pthread_setcancelstate(PTHREAD_CANCEL_ENABLE,&oldS tate);
checkResults("%d = pthread_setcancelstate(2)\n", rc);
/* Now, cancellation points will allow pending cancels
to get through to this thread */
}
} /* infinite */
pthread_cleanup_pop(0);
return NULL;
}

int main(int argc, char **argv)
{
pthread_t thread;
int rc=0;
void *status=NULL;

printf("Enter Testcase - %s\n", argv[0]);

/* Create a thread using default attributes */
printf("Create thread using the NULL attributes\n");
rc = pthread_create(&thread, NULL, threadfunc, NULL);
checkResults("%d = pthread_create(NULL)\n", rc);

sleep(1);
printf("Cancel the thread\n");
rc = pthread_cancel(thread);
checkResults("%d = pthread_cancel()\n", rc);

rc = pthread_join(thread, &status);
if (status != PTHREAD_CANCELED) {
printf("Thread returned unexpected result!\n");
return 1;
}code
printf("Main completed\n");
return 0;
} 
[/PHP]

Try using the php tags for posting code like this, It has basic syntax highlighting makes things alot easier to read :)
**EDIT** Try indenting your code  as well.Only noticed it when i was looking at the code.

---

### Post by dribeas on 2008-07-27
> **arielsegal said:**
> ```

if (i == 5) {
   printf("Cancel state set to ENABLE\n");
   rc = pthread_setcancelstate(PTHREAD_CANCEL_ENABLE,&oldS tate);
   checkResults("%d = pthread_setcancelstate(2)\n", rc);
   /* Now, cancellation points will allow pending cancels
      to get through to this thread */
}
```

Whether it should or not, I am trying to find out, but printf (checkResults) stablishes a cancellation point in your code. If you comment that line in your code you will get your expected results.

UPDATE: I've read the manpage and tried googling without comming to a conclusion. printf is defined in C standard that ignores threading completely, and without the POSIX standard at hand I could not figure whether POSIX defines printf as interruption point. Then again, in the headers:

> 
// /usr/include/stdio.h

/* Write formatted output to stdout.

   This function is a possible cancellation point and therefore not
   marked with __THROW.  */
extern int printf (__const char *__restrict __format, ...);


   David

---

### Post by arielsegal on 2008-07-27
Thank you for your answer.
I have made my own example now. I avoided this time 'printf'. It still doesn't work. It seems that no matter whether the thread is asynchronous of deffered, the thread doesn't wait for the cancellation point.

[PHP]#include <pthread.h>
#include <stdio.h>
#include <string.h>
#include <unistd.h>

char buff[0x400];

void *print_x(void *params)
{
	int i = 0;
	int *syncstate = (int*)params;
	pthread_setcancelstate (PTHREAD_CANCEL_DISABLE, NULL);
	pthread_setcanceltype(*syncstate, NULL);
	printf("%s> syncstate %d\n", __FUNCTION__, *syncstate);
	sleep(2);
	while(true)
	{
		buff[i++] = '#';
		if(1 == i)
			pthread_setcancelstate (PTHREAD_CANCEL_ENABLE, NULL);
		sleep(1);
		buff[i++]  = '*';
		if(6 == i)
		{
			buff[i++] = '\0';
			pthread_testcancel();	// cancelation point
		}
	}
}

int main(int argc, char **argv)
{
	pthread_t thread_id;
	pthread_attr_t attr;
	int i, ret;
	int syncstate = PTHREAD_CANCEL_DEFERRED;
	if(2 == argc)
	{
		if(!strcmp("-a", argv[1]))
			syncstate = PTHREAD_CANCEL_ASYNCHRONOUS;
		else if(!strcmp("-s", argv[1]))
			syncstate = PTHREAD_CANCEL_DEFERRED;
	}
	printf("%s> syncstate %d\n", __FUNCTION__, syncstate);
	
	pthread_create(&thread_id, NULL, &print_x, &syncstate);
	sleep(1);
	pthread_cancel(thread_id);
	for(i = 0; i < 3; i++)
		printf("main program is running\n");
	pthread_join(thread_id, (void**)(&ret));
	printf("Thread id 0x%08x return %d\n", thread_id, ret);
	printf("thread filled buffer:\n%s\n", buff);
	return 0;
}
[/PHP]

Expected result for 'thread -s'
main> syncstate 1
print_x> syncstate 1
main program is running
main program is running
main program is running
Thread id 0xb7cb1b90 return 0
thread filled buffer:
#*#*#*


Actual results 'thread -s'
main> syncstate 1
print_x> syncstate 1
main program is running
main program is running
main program is running
Thread id 0xb7cb1b90 return 0
thread filled buffer:
#

Results for 'thread -a' are the same

---

### Post by arielsegal on 2008-07-28
Hi,
Is it possible that there is a bug in Ubuntu kernel, that cancellation point just does not work. Did anyone tried to run my code on Ubuntu or any other distro?

---

### Post by loell on 2008-07-28
qouting

from [http://taschenorakel.de/mathias/2007/11/20/g-thread-cancel/]("http://taschenorakel.de/mathias/2007/11/20/g-thread-cancel/")

> I don't really know, why that function is missing, but my guess it, that randomly killing threads is quite dangerous, as threads share the process with your program. Stopping the thread at some random point most certainly will leave your entire program in an inconsistent state. 

---

### Post by dribeas on 2008-07-28
> **arielsegal said:**
> 
[PHP]		if(1 == i)
			pthread_setcancelstate (PTHREAD_CANCEL_ENABLE, NULL);
		sleep(1);
[/PHP]

Expected result is in fact # and the program is running properly. You have traded one cancellation point (printf) for another (sleep):

```

// from /usr/include/unistd.h
/* Make the process sleep for SECONDS seconds, or until a signal arrives
   and is not ignored.  The function returns the number of seconds less
   than SECONDS which it actually slept (thus zero if it slept the full time).
   If a signal handler does a `longjmp' or modifies the handling of the
   SIGALRM signal while inside `sleep' call, the handling of the SIGALRM
   signal afterwards is undefined.  There is no return value to indicate
   error, but if `sleep' returns SECONDS, it probably didn't work.

   This function is a cancellation point and therefore not marked with
   __THROW.  */
extern unsigned int sleep (unsigned int __seconds);

```

For those who cried 'kernel bug'! It is much probable to find a problem in a beginners code/interpretation than in the kernel.

As a general rule of thumb, do not cancel asynchronously. Then when you do deferred cancellation, be aware of where cancellation points are.

If you go back to your first example and just comment the printf after the pthread_setcancelstate() then you'll get your expected results even if instead of canceling in pthread_testcancel() it is after exec-ing the printf above. If you change to asynchronous cancellation there you won't get to the printf and the output will be different.

Coming up with code to do a good test is probably more complex than what you are going to learn from this. Just take it as granted that if cancellation is deferred then it happens only in cancellation points and then again only if cancellation is enabled.

   David

---

### Post by arielsegal on 2008-07-28
loell,
Thank you for your answer. I have looked around in the Internet and found out that some systems don't implement well pthread_cancel().
anyway, there are other ways to cause a thread to cleanup resources and exit, but I'm learning the Linux OS, so I insisted on using pthread_cancel().
It possible that that pthread_setcanceltype() and pthread_setcancelstate() are cancellation points themselves, can that be? If so its a bug.
see: []("http://lists.apple.com/archives/Darwin-userlevel/2004/Mar/msg00016.html")

---

### Post by dribeas on 2008-07-28
> **arielsegal said:**
> It possible that that pthread_setcanceltype() and pthread_setcancelstate() are cancellation points themselves, can that be? If so its a bug.
see: []("http://lists.apple.com/archives/Darwin-userlevel/2004/Mar/msg00016.html")

Yes that would be a bug, but I don't believe that is the case in linux. Just try, as I posted before, your first example commenting the checkResult/printf after the pthread_setcancelstate() and you'll see that if it is DEFERRED the printf in the top of the loop is executed, which means that pthread_setcancelstate() is NOT a cancellation point. On the other hand, if you change the type of cancellation to asynchronous then that first printf will not be shown as the cancellation occurs just after cancellation is enabled.

   David

---

### Post by arielsegal on 2008-07-28
David,
You are right! I put sleep(1) in comment and it works!
I think it is a good thing that I haven't give up, and took it for granted. Digging through code and experiencing is the best way to learn, and I aim to be a pro sometime in the future.

---

### Post by wssoh85 on 2008-12-16
Hi everyone, I'm new to this forum. If my qurestion is in wrong place please correct me.
I'm currently learning about the multithread, and TCP socket. But I was wondering why my code have problem. I search over google still cant fix my problem. Hope anyone can direct me into the right. Thanks

Here is my code

 
[PHP]```
/* threadclient.c */
#include <pthread.h>
#include <sys/socket.h>
#include <sys/types.h>
#include <netinet/in.h>
#include <netdb.h>
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <unistd.h>
#include <errno.h>

void *cthr_do();
void *cthr_send();
void *cthr_recv();


int main()
{	
	int k;
	pthread_t new_thr;
	int check = pthread_create(&new_thr, NULL, cthr_do, NULL );
	
	
	if(check!=0)
	printf("The thread cannot be created!");
	
	pthread_join (new_thr, NULL);
	
	printf("The whole process terminated\n");
	return 0;
}

void *cthr_do()
{	
	printf("thread run sucessful\n");

        int sock, bytes_received, connected, s, r;  
        char send_data[1024],recv_data[1024];
        struct hostent *host;
        struct sockaddr_in6 server_addr;  

        host = gethostbyname("::1");

        if ((sock = socket(AF_INET6, SOCK_STREAM, 0)) == -1) {
            perror("Socket");
            exit(1);
        }

        server_addr.sin6_family = AF_INET6;     
        server_addr.sin6_port = htons(5000);   
        server_addr.sin6_addr= in6addr_any/*((struct in_addr *)host->h_addr)*/;
        /*bzero(&(server_addr.sin_zero),8);*/
	/*memset(&(server_addr.sin_zero),0,8);*/
        
        connected = connect(sock, (struct sockaddr *)&server_addr, sizeof(server_addr));
         
	if (connected== -1) 
        {
            perror("Connect");
            exit(1);
        }

	printf("The connection is established.\n");	
	
	pthread_t send_thr, recv_thr;
              
              int chk_send = pthread_create(&send_thr, NULL, cthr_send, (void *)sock);
              if(chk_send!=0)
              printf("The send message thread cannot be created!");
              
              int chk_recv = pthread_create(&recv_thr, NULL, cthr_recv, (void *)sock);              
              if(chk_recv!=0)
              printf("The receive message thread cannot be created!");
              
              while (1)
              {
              s = pthread_join (send_thr, NULL);
              r = pthread_join (recv_thr, NULL);
              
              if (s && r)
              break;
              }
              
	close(sock);
	printf("closed socket\n");              
}


void *cthr_send(void *arg)
{	      
	      pthread_setcancelstate(PTHREAD_CANCEL_ENABLE, NULL);
	      pthread_setcanceltype(PTHREAD_CANCEL_ASYNCHRONOUS, NULL);
	      

	      char send_data [1024], recv_data[1024]; 
	      while (1)
	      {
		      printf("\n SEND (q or Q to quit) : ");
		      gets(send_data)/*,1024,stdin)*/;
		      
		      if (strcmp(send_data , "q") == 0 || strcmp(send_data , "Q") == 0)
		      {
		        send((int) arg, send_data,strlen(send_data), 0);
		        /*close ((int) arg);*/
		        break;            
		      }
		       
		      else
		         send((int) arg, send_data,strlen(send_data), 0);
              }  
              
              if ( pthread_cancel(recv_thr) == -1 ) 
              {
		      perror("pthread_cancel failed");
		      exit(3);
              }  
//              if (pthread_cancel(recv_thr)!= 0)
//              perror ("Thread cancelation ");              ;              
}

void *cthr_recv(void *arg)
{
         
              pthread_setcancelstate(PTHREAD_CANCEL_ENABLE, NULL);
              pthread_setcanceltype(PTHREAD_CANCEL_ASYNCHRONOUS, NULL);
              
              char send_data [1024] , recv_data[1024]; 
              int bytes_received;
              
              
              while (1)
              {
		      bytes_received = recvfrom((int) arg, recv_data, 1024-1, 0, NULL, NULL);
		      /*recv((int) arg,recv_data,1024,0);*/
		     
		      if (bytes_received == -1)
			{
			  /*
			   * Socket in error state
			   */
			  perror ("Client recv(): ");
			  exit(1);
			}		
	     
		      printf("\nThe number of digit received: %d\n", bytes_received);
		      recv_data[bytes_received] = '\0';

		      if (strcmp(recv_data, "q") == 0 || strcmp(recv_data , "Q") == 0)
		      {
		        send((int) arg, "q", strlen("q"), 0);
//		        close((int) arg);
		        break;
		      }

		      else 
		      printf("\n RECEIVED DATA = %s \n" , recv_data);
		      fflush(stdout);
              }
              
//              if (pthread_cancel (send_thr)!= 0)
//              perror ("Thread cancelation ");              ;              

}
```[/PHP]

When i compile this code with the error shown.

```
shufei@shufei-desktop:~/Desktop$ gcc -lpthread threadclient.c -o threadclient
threadclient.c: In function ‘cthr_send’:
threadclient.c:114: error: ‘recv_thr’ undeclared (first use in this function)
threadclient.c:114: error: (Each undeclared identifier is reported only once
threadclient.c:114: error: for each function it appears in.)

```

is anyone know why it say the recv_thr is undeclare since it was declared in secondary thread. Please forgive my if this is an stupid question.

Regards,
wssoh

---

### Post by escapee on 2008-12-16
For future reference, you should start your own thread (posting thread, not programming thread) if your problem  doesn't have direct relevance to the thread in which you are posting.  Granted, they are both related to the same topic, but two completely separate problems/situations.  Definitely no need to post in a 5 month old thread.

All that aside, you declared recv_thr in the scope of *void *cthr_do();* and did not pass it to or declare it in the scope of *void *cthr_send()*; where you want to use it.


Hope that helps :)

---

### Post by wssoh85 on 2008-12-18
Thanks for your advise, I will open a new thread. :)

---

