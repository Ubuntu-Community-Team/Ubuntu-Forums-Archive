---
title: "Blocking threads in C"
date: 2014-07-27
forum: Programming Talk
---

### Post by brick2 on 2014-07-27
```
#include <sys/socket.h>
#include <sys/types.h>
#include <arpa/inet.h>
#include <pthread.h>

struct arguments
		{
			int *new_sock;
			int port;
			char *IP;
		};
pthread_t cli[1000];

int connection();
int *cli_handler(void *arg);

int main( int argv, char* const argc[] )
{
	connection();
	return 0;
}

int connection()
{
	int sock_fd,
		cli_sock,
		len,
		PORT = 4444;
	struct sockaddr_in server;

	server.sin_family = AF_INET;
	server.sin_port = htons(PORT);
	server.sin_addr.s_addr = INADDR_ANY;

	/* bind
	 * listen
	 * accept
	 */

	sock_fd = socket( AF_INET, SOCK_STREAM, 0);

	if( sock_fd == -1 )
	{
		perror("SOCKET FAILED!!!");
		return 1;
	}
	puts("SOCKET CREATED");

	if( bind( sock_fd, (struct sockaddr*)&server, sizeof(server) ) == -1 )
	{
		perror("BIND FAILED!!!");
		return 1;
	}
	puts("BIND DONE");

	listen(sock_fd, 1000);
	//why does printf not output text here? but no errors are given
	puts("LISTENING ON PORT 4444....");

	len = sizeof(struct sockaddr_in);
	int index00;

	struct arguments *ptr_arg;

point00:while( cli_sock = accept (sock_fd, (struct sockaddr  *) &server, (socklen_t *)&len) )
		{
			if(cli_sock == -1)
			{
				perror("ACCEPT FAILED!!!");
				return 1;
			}
			ptr_arg = (struct arguments *)malloc(sizeof(*ptr_arg));
			ptr_arg->new_sock = cli_sock;
			printf( "Connection received from: %s %d\n", inet_ntoa(server.sin_addr), ntohs(server.sin_port) );

			ptr_arg->IP = inet_ntoa(server.sin_addr);
			ptr_arg->port = ntohs(server.sin_port);

			//why would someone put < 0 here

			for( index00=0; index00<1000; index00++ )
			{
				if( cli[index00] == NULL )
				{
					if( pthread_create( &cli[index00], NULL, cli_handler, (void *)ptr_arg ) < 0 )
					{
						perror("THREAD FAILED");
						return 1;
					}
					pthread_join(cli[index00], NULL);
					goto point00;
				}
				index00++;
			}
		}
}

int *cli_handler(void *arg)
{
	int new_sock,// = *(int *)sock,
		write_fd,
		recv_fd,
			i;

	char buff[256];

	struct arguments *ptr_arg;
	ptr_arg = (struct arguments *)arg;

	new_sock = ptr_arg->new_sock;
	int port_f = ptr_arg->port;

	int len = strlen(ptr_arg->IP);
	char test[len];
	for( i=0; i<len; i++ )
		test[i] = ptr_arg->IP[i];

	while(1)
	{
		write_fd = write( new_sock, "TEST: ", 6 );
		if( write_fd == 0 )
		{
			puts("NOTHING WRITTEN");
		}
		else if( write_fd == -1 )
		{
			perror("\nFAILED TO WRITE");
			return 1;
		}

		if ( ( recv_fd = recv( new_sock, buff, 256, 0 ) ) == -1 )
		{
			perror("\nRECV FAILED");
			return 1;
		}

		printf("FROM %s %d: %s", test, port_f, buff);

		for( i=0; i<256; i++ )
			buff[i] = '\0';
	}
	free(arg);
}


//CLINET IP IDENTIFIER DONE

//server input to send to specific client
//TThread index managing
```


Code is above, the problem is following.
Multiple clients may connect, but only one at a time may send messages  to the server, when one discconects next one may send and so on.
Can anyone tell me as to why is this happening, how to fix it.
I think that threads are somehow blocking one another but I am not sure.

Thank you all for your time.

---

### Post by dwhitney67 on 2014-07-27
Why are you calling pthread_join() after you create the new thread?  That call will block your server (thus denying any other client from connecting) until the thread completes.

If you want to support multiple simultaneous clients, then in lieu of using a pthread, just fork a new process to handle the client.  For example:

```

while (true)
{
    int client = accept(sock_fd, NULL, NULL);

    if (fork() == 0)
    {
        handleClient(client);
    }
}

```
Of course, there are other approaches, but the one above is the easiest I could think of.

---

### Post by ofnuts on 2014-07-27
Because your code explicitly waits for the thread to end (pthread_join) after it created it... so you aren't going to create another thread until that one is done.

printf() doesn't output anything until 1) there is a \n in the output (line-buffered mode it stdout is a TTY device) or 2) some buffer is full (4K IIRC) in all other cases. This can be changed (setvbuf)

Ninja'ed :) Using threads for this is OK if done properly. A process is a little heavier on the system.

---

### Post by brick2 on 2014-07-29
Ok so here is what I did.
Insted of joining a thread I did pthread_detach, it appears to work ok but I am a litle worried about the resources of the system.

---

### Post by dwhitney67 on 2014-07-29
> **brick2 said:**
> Ok so here is what I did.
Insted of joining a thread I did pthread_detach, it appears to work ok but I am a litle worried about the resources of the system.

Just limit how many clients may connect at any given time.  Or procure more RAM.

---

### Post by brick2 on 2014-07-29
Well 
pthread_t cli[1000];

so I guess 1000, but that is jsut in case I am not expecting more than 50

---

### Post by dwhitney67 on 2014-07-29
> **brick2 said:**
> Well 
pthread_t cli[1000];

so I guess 1000, but that is jsut in case I am not expecting more than 50

Then set your array size to 50, use a counter that is incremented when the client connects, and is decremented when they disconnect.  If max clients have connected, then reject any new connections.

```

int client = accept(sock_fd, NULL, NULL);

if (numClients < MAX_CLIENTS)
{
    // handle client
}
else
{
    close(client);
}

```

---

### Post by ofnuts on 2014-07-29
One question is the purpose of this array... all it holds are threads ids that are never used. And since I don't see where the contents of the array are reset when a thread ends, it looks like this array size is the number of threads that will be run created before the app hangs forever.

I'll go with DW for a counter, but it should be counting threads, no clients. Increament when starting the thread, decrement when it ends. You'll have to handle simultaneous updates (because at least the decrement part can only be done at the end of a thread).

When a threads is detached, its system resources are recovered when it ends. The other possible leak is the argument parameter to the thread startup but you have already covered that.

---

### Post by dwhitney67 on 2014-07-29
> **ofnuts said:**
> One question is the purpose of this array... all it holds are threads ids that are never used. And since I don't see where the contents of the array are reset when a thread ends, it looks like this array size is the number of threads that will be run created before the app hangs forever.

I'll go with DW for a counter, but it should be counting threads, no clients. Increament when starting the thread, decrement when it ends. You'll have to handle simultaneous updates (because at least the decrement part can only be done at the end of a thread).

When a threads is detached, its system resources are recovered when it ends. The other possible leak is the argument parameter to the thread startup but you have already covered that.

Yep; a thread pool would be helpful in managing the number of clients that can be handled.

---

