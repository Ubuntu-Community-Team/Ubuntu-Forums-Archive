---
title: "send: Bad file descriptor"
date: 2009-09-12
forum: Programming Talk
---

### Post by akm3 on 2009-09-12
I have written a simple client/server code in C using sockets.
The server simply sends a string to every connected client.
In a first version I use fork(), and here is what the child does:

```

		if(!fork()){
			close(listening_socket);
			Send(new_socket, "Hello World!", 13 , 0);
			printf("sent over socket number: %d", new_socket);
			close(new_socket);
			exit(0);
		}

```
This works perfectly fine.


Then I use a threadpool, instead of forking, and assign the child responsibility to a worker thread(i.e I put this code section in the routine of a thread). I pass the socket number for the newly "accept()"ed client as an argument to the thread, but this time I get "send: Bad file descriptor", and client gets nothing.

As far as I see, in this case the client and the server are connected like the first case and they have each others' IPs. Also I see the socket number is passed to the worker thread correctly (i.e. the same number that "accept()" returns is passed), but for some reason the send in the worker thread fails.

Dose any body has an idea why is that?

---

### Post by dwhitney67 on 2009-09-12
> **akm3 said:**
> I have written a simple client/server code in C using sockets.
The server simply sends a string to every connected client.
In a first version I use fork(), and here is what the child does:

```

		if(!fork()){
			close(listening_socket);
			Send(new_socket, "Hello World!", 13 , 0);
			printf("sent over socket number: %d", new_socket);
			close(new_socket);
			exit(0);
		}

```
This works perfectly fine.


Then I use a threadpool, instead of forking, and assign the child responsibility to a worker thread(i.e I put this code section in the routine of a thread). I pass the socket number for the newly "accept()"ed client as an argument to the thread, but this time I get "send: Bad file descriptor", and client gets nothing.

As far as I see, in this case the client and the server are connected like the first case and they have each others' IPs. Also I see the socket number is passed to the worker thread correctly (i.e. the same number that "accept()" returns is passed), but for some reason the send in the worker thread fails.

Dose any body has an idea why is that?

Not unless I see more of your code.  It could be that you are closing the client socket before the thread gets a chance to run, or it could be that your thread is improperly setup.

Here's an example of how one could setup their server:
```

#include <Socket/TCPServerSocket.h>
#include <pthread.h>
#include <stdbool.h>
#include <stdio.h>

void* clientHandler(void* arg);


int main(int argc, char** argv)
{
   SocketInfo sinfo = { AF_INET, SOCK_STREAM, 0 };

   CreateSocket(&sinfo);                  // create the socket
   Bind(&sinfo, 12345, 0);                // bind to port 12345 for all interfaces
   EnableReusePort(&sinfo);               // SO_REUSEADDR
   Listen(&sinfo, 5);                     // max number of clients that can have a pending connection

   while (1) {
      if (ActivityDetected(&sinfo, 0)) {  // will block until activity detected on listen socket
         SocketInfo* client_sinfo = Accept(&sinfo);

         pthread_t tid;
         pthread_create(&tid, 0, clientHandler, client_sinfo);
      }
   }

   return 0;
}

void* clientHandler(void* arg)
{
   SocketInfo* sinfo = (SocketInfo*) arg;

   bool done = false;

   while (!done) {
      if (ActivityDetected(sinfo, 0)) {                // block until activity detected
         char msg[1024] = {0};

         int bytes = Recv(sinfo, msg, sizeof(msg));    // receive from the client; if msg is zero-bytes in
                                                       // length, assume the client disconnected.
         if (bytes > 0) {
            printf("Client Sent: %s\n", msg);
         }
         else {
            printf("Client Disconnected.\n");
            done = true;
         }
      }
   }

   CloseSocket(sinfo);
   free(sinfo);

   pthread_exit(0);
}

```
The code above does not use a threadpool, but that should not be too difficult to implement.

---

### Post by akm3 on 2009-09-12
Thanks for the reply.

I think what I do is pretty the same.
I'm pretty sure the "threadpool" is fine as I have adopted that from another library with minimal changes.

You can see the server code here:
```
http://pastebin.com/m536f2f84
```

The threadpool functions are in another library, but I have only used a "struct tpool_t", and two functions "tpool_init(&MyTpool, 10, 20, 0)" to create 10 threads in a queue of size 20 for works, and "tpool_add_work(MyTpool, worker_routine ,(void *)new_socket);"
to add the routine "worker_routine()" with arguemtn "new_socket" to a thread in the pool.

---

### Post by dwhitney67 on 2009-09-12
I looked at your code; as I suspected, you are closing the client socket before your thread has an opportunity to use it.  Refer to line 88 of your code.

Btw, your code at line 15 is correct.

---

### Post by akm3 on 2009-09-12
Thanks a lot, that was exactly the problem.
Actually, it was my misunderstanding of threads that caused it, as I didn't realize the difference between a thread, and a child process:)), and just replace some piece of code

---

