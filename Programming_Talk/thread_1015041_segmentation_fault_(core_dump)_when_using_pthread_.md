---
title: "segmentation fault (core dump) when using pthread_cancel()"
date: 2008-12-18
forum: Programming Talk
---

### Post by wssoh85 on 2008-12-18
Hi, everyone. I'm learning thread now and I face the problem of segmentation fault. I know that the segmentation fault is most probably occur when pthread_cancel() function was called. But I can't fix it. Please help me.
Here is my code. Sorry for such a long code
[PHP]/* threadclient.c */

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
struct package {pthread_t send_thr, recv_thr;
		int sock;} ;
	
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
	
	pthread_t send_thr, recv_thr;
        int sock, bytes_received, connected, s, r;  
        char send_data[1024],recv_data[1024];
        struct hostent *host;
        struct sockaddr_in6 server_addr;  
	struct package pack, *p_pack;
	
        host = gethostbyname("::1");
      	if ((sock = socket(AF_INET6, SOCK_STREAM, 0)) == -1) 
		{
		    perror("Socket");
		    exit(1);
		}
        
        p_pack=&pack;
        
	pack.sock=sock;
	        
        server_addr.sin6_family = AF_INET6;     
        server_addr.sin6_port = htons(5000);   
        server_addr.sin6_addr= in6addr_any;
        
        connected = connect(sock, (struct sockaddr *)&server_addr, sizeof(server_addr));
         
	if (connected== -1) 
		{
		    perror("Connect");
		    exit(1);
		}

	printf("The connection is established.\n");	
	
	

	int chk_send = pthread_create(&send_thr, NULL, cthr_send, (void *)p_pack);
        if(chk_send!=0)
        printf("The send message thread cannot be created!");
      
        int chk_recv = pthread_create(&recv_thr, NULL, cthr_recv, p_pack);              
        if(chk_recv!=0)
        printf("The receive message thread cannot be created!");
      
        pack.send_thr = send_thr;
	pack.recv_thr = recv_thr;
	
        while (1)
	        {
	        s = pthread_join (pack.send_thr, NULL);
	        r = pthread_join (pack.recv_thr, NULL);
	      
	        if (s && r)
	        break;
	        }
              
	close(sock);
	printf("closed socket\n");              
}


void *cthr_send(void *arg)
{	      
	      int sock, test;
	      char send_data [1024], recv_data[1024]; 
	      struct package *point;
	      
	      point = arg;
	   	      
	   	      pthread_t recv_thr = (*point).recv_thr;
	   	      
	      while (1)
	      {		
		      printf("\n SEND (q or Q to quit) : ");
		      gets(send_data)/*,1024,stdin)*/;
		      
		      if (strcmp(send_data , "q") == 0 || strcmp(send_data , "Q") == 0)
		      {
		        send((*point).sock, send_data,strlen(send_data), 0);
		        /*close ((*point).sock);*//**/
		        break;            
		      }
		       
		      else
		         send((*point).sock, send_data,strlen(send_data), 0);
              }  
              
              puts("position of segmentation fault");
              if ( pthread_cancel(/*(*point).*//**/recv_thr != 0) ) 
                            {
              		      perror("pthread_cancel failed");
              		      exit(3);
                            }            
}

void *cthr_recv(void *arg)
{                    
              char send_data [1024] , recv_data[1024]; 
              int bytes_received, sock;
              struct package *point;
	      
	      point = arg;
	      
              if ((sock = socket(AF_INET6, SOCK_STREAM, 0)) == -1) 
		{
		    perror("Socket");
		    exit(1);
		}
		
              while (1)
              {
		      bytes_received = recvfrom((*point).sock, recv_data, 1024-1, 0, NULL, NULL);
		      /*recv((int) arg,recv_data,1024,0);*/
		     
		      if (bytes_received == -1)			//Check the received message error status
			{
			  perror ("Client recv()");
			  exit(1);
			}		

		      printf("\nThe number of digit received: %d\n", bytes_received);
		      recv_data[bytes_received] = '\0';

		      if (strcmp(recv_data, "q") == 0 || strcmp(recv_data , "Q") == 0)
		      {
		        send(sock, "q", strlen("q"), 0);
//		        close((int) arg);
		        break;
		      }

		      else 
		      printf("\n RECEIVED DATA = %s \n" , recv_data);
		      fflush(stdout);
              }
              
	      if ( pthread_cancel((*point).send_thr != 0) ) 
		      {
			      perror("pthread_cancel failed");
			      exit(1);
		      }             

}[/PHP]

The purpose of this program is simple TCP client to have continuous conversation with server. Therefore, I create 2 thread which is to send message and receive message from server.

compile had no problem, but when run and this client type a "q" to quit the program, the error occur.

error is shown here
```
vince@vince-laptop:~/Desktop$ ./tethreadclient
thread run sucessful
The connection is established.

 SEND (q or Q to quit) : q
position of segmentation fault
Segmentation fault (core dumped)
vince@vince-laptop:~/Desktop$ 

```

Anyone please give me some direction how to solve this.

---

### Post by dribeas on 2008-12-18
I don't really have time now to go into code details, but the one thing you can surely do is allowing the shell to dump core files and check with gdb where the program really died:

```

$ ulimit -c unlimited       # Enable core with unlimited size
$ run_program
...
core created
$ gdb -c core run_program
...
(gdb) bt                    - display function call backtrace

```

The output of the backtrace will tell you where the program died (function that was being executed)

---

### Post by wssoh85 on 2008-12-18
Thanks for you reply. The result is shown here
```

warning: Can't read pathname for load map: Input/output error.
Reading symbols from /lib/tls/i686/cmov/libpthread.so.0...done.
Loaded symbols for /lib/tls/i686/cmov/libpthread.so.0
Reading symbols from /lib/tls/i686/cmov/libc.so.6...done.
Loaded symbols for /lib/tls/i686/cmov/libc.so.6
Reading symbols from /lib/ld-linux.so.2...done.
Loaded symbols for /lib/ld-linux.so.2
Core was generated by `./tethreadclient'.
Program terminated with signal 11, Segmentation fault.
#0  0xb7ee54cd in pthread_cancel () from /lib/tls/i686/cmov/libpthread.so.0
(gdb) bt
#0  0xb7ee54cd in pthread_cancel () from /lib/tls/i686/cmov/libpthread.so.0
#1  0x08048c08 in cthr_send ()
#2  0xb7ee046b in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#3  0xb7e6473e in clone () from /lib/tls/i686/cmov/libc.so.6
(gdb) 


```

However, I don't really understand what it mean here. how can a thread die in 4 places? and where is start_thread() and clone()?

---

### Post by monkeyking on 2008-12-19
without having looked into your code...

debugging pthread programs can be a hell.

I havn't looked into your code but remeber when you debug to enable debug symbols. This means

[PHP]gcc -ggdb[/PHP]
or 
[PHP]g++ -ggdb[/PHP]

Then the debugger will tell you which line the error occured in.

Futhermore I would recommend -Wall -pedantic -ansi.

I would also use valgrind to check for dyn mem allocation.

good look

edit:
your program doesn't crash for me,
but it doesn't connect the client.

[PHP]
gcc -ggdb  th.c -lpthread ;./a.out
/tmp/cc0jKPWl.o: In function `cthr_send':
/home/***/th.c:111: warning: the `gets' function is dangerous and should not be used.
thread run sucessful
Connect: Connection refused
[/PHP]

with -Wall

[PHP]
gcc -ggdb -Wall th.c -lpthread ;./a.out
th.c: In function &#8216;main&#8217;:
th.c:22: warning: unused variable &#8216;k&#8217;
th.c: In function &#8216;cthr_do&#8217;:
th.c:41: warning: unused variable &#8216;recv_data&#8217;
th.c:41: warning: unused variable &#8216;send_data&#8217;
th.c:40: warning: unused variable &#8216;bytes_received&#8217;
th.c:95: warning: control reaches end of non-void function
th.c: In function &#8216;cthr_send&#8217;:
th.c:101: warning: unused variable &#8216;recv_data&#8217;
th.c:100: warning: unused variable &#8216;test&#8217;
th.c:100: warning: unused variable &#8216;sock&#8217;
th.c:130: warning: control reaches end of non-void function
th.c: In function &#8216;cthr_recv&#8217;:
th.c:134: warning: unused variable &#8216;send_data&#8217;
th.c:178: warning: control reaches end of non-void function
/tmp/ccEzSgIN.o: In function `cthr_send':
/home/***/th.c:111: warning: the `gets' function is dangerous and should not be used.
thread run sucessful
Connect: Connection refused

[/PHP]

---

### Post by dwhitney67 on 2008-12-19
I would bet that your assumption here is what is causing the problem:
[php]
                 pthread_t recv_thr = (*point).recv_thr; 
[/php]

You are assuming that by the time the send-thread obtains the recv_thr ID, that it has been set.  It probably isn't, because you do not set it until after both the send AND the receive threads are started.

Re-examine your design, and I believe you will be able to solve the problem.

P.S.  Always start the receive-thread before the send-thread; similarly when dealing with consumer/producer threads, the consumer should always be started first.

P.S.S.  Use the following flags when compiling so that you see the tons of warnings in your code:  -Wall -pedantic

---

### Post by wssoh85 on 2008-12-24
Thanks for all your help :)

But I still cannot get the things right from the error message. And due to time limitation, I change the way of implementation of my program. I set up a flag instead of cancel out the other thread. So the main thrread will always check for the flag and then exit the whole program. 

Anyway, what you all tell me is a very good way of debugging. It is useful for me in future. Thank you. :)

Sincerely,
wssoh

---

