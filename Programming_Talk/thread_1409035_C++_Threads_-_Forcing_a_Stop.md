---
title: "C++ Threads - Forcing a Stop"
date: 2010-02-17
forum: Programming Talk
---

### Post by PaulM1985 on 2010-02-17
Hi

I am trying to setup a Server-Client connection between some programs I am writing and I want to be able to deal with all close connection cases.

My plan was to have a two threads on the Server (the normal main() thread and an additional thread for receiving information) and one thread on the Client which deals with sending an receiving.  I thought only one thread is needed on the client because this drives the system, it is not waiting for requests, it makes them.

My threaded receive method on the server would be something like:

```


void
Server::Receive(int length) const {

	char *pString = new char[length];
	int numbytes;

	// Waits here for client to ask for something
	if ((numbytes = recv(m_ClientId, pString, length, 0)) == -1) {
		perror("recv");
	}

	pString[numbytes] = '\0';

	std::string aString(pString, numbytes);

//
// Process aString and send back the required information
//
}

```

The problem I have got is the case when the Server tries to stop when the client is running.  The Receive thread waits on the recv() line for the client to send something.  Is there a way I can force this thread to abort this?  Or can anyone think of a different way I can wait for client information and stop this thread safely or any other advice in general?

I was thinking of using boost for threading.  I have done some threading stuff in Java before but nothing in C++.

Any advice would be great.

Paul

---

### Post by dwhitney67 on 2010-02-17
You need to realize that recv() is a *blocking* call.  If you want it to be non-blocking, then you must set up the socket to be non-blocking.

The better alternative, is to not call recv() unless there is indeed information to receive from the client.  Use select() to determine if there is indeed information to receive from the client.

In a multi-threaded application where you will be supporting the connection of multiple clients, and using a single thread to receive data, the simplest approach is to maintain an STL *set* that contains each socket descriptor; each descriptor is unique.  The STL set will need to be managed by a thread-safe object that can be accessed by the listen-thread and the receive-thread.

The listen-thread will accept() connections, and for each, it will insert the socket (descriptor), via the thread-safe object, into the STL set.

The receive-thread will obtain an FD_SET from this same thread-safe object that it can use within the select() call.  When activity is reported by select(), an updated FD_SET is provided indicating which client(s) are sending data.

If you receive zero-bytes (or an error occurs) when attempting to recv() from a client, this is indicative that the client disconnected or that there was some other error with the socket.  In such an event, just close() the socket and remove it from the STL set.

This is easy programming that will push your knowledge a little further.  Please let me know if you have further questions.

P.S.  A thread-safe object will undoubtedly utilize some sort of access locking "mechanism", such as a semaphore or a mutex, to prevent concurrent access between competing threads.  If you are not familiar with the subject of thread-safe, then become fluent in it because this is an important topic to understand for multi-threaded programming.

---

### Post by zippaplick on 2010-02-17
@dwhitney67: great post dude. Very informative.

@PaulM1985: personally I've always found pthread's api to be a bit obtuse. I'd suggest you go with boost threads. the API is straight forward and it includes locking mechanisms.

---

### Post by VertexPusher on 2010-02-17
> **PaulM1985 said:**
> Is there a way I can force this thread to abort this?
If you use the pthreads API, call pthread_kill() to send a signal to the blocked thread. If you use Boost or GNU Common C++, call the equivalent methods of the Thread class to interrupt/terminate the thread, just as you would do in Java.

---

### Post by PaulM1985 on 2010-02-17
Thanks for the info. Is select a non blocking function? I am only ever going to have one client connected at one time.

Paul

---

### Post by dwhitney67 on 2010-02-17
select() is a blocking function; however you can call it with a timeout period (struct timeval), thus enabling the thread to regain control should there not be any socket activity within the prescribed timeout period.

For one client, typical usage of select() is something like this:
```

fd_set save_fds;

FD_CLR(&save_fds);
FD_SET(sockdesc, &save_fds);

bool clientConnected = true;

while (clientConnected)
{
   fd_set  read_fds = save_fds;
   timeval timeout  = {1, 0};      // timeout of 1 second

   int sel = select(sockdesc+1, &read_fds, 0, 0, &timeout);

   if (sel > 0)
   {
      // activity detected from client socket
      int bytesRead = recv(...);

      if (bytesRead > 0)
      {
         // got data
      }
      else if (bytesRead == 0)
      {
         clientConnected = false;
      }
      else
      {
         // socket error... give the client the boot
         clientConnected = false;
      }
   }
   else if (sel == 0)
   {
      // timeout occurred.
   }
   else
   {
      // grave error (this is rare)
   }
}

// if here, close client's socket
close(sockdesc);

```

---

### Post by VertexPusher on 2010-02-18
select() was designed to enable handling of multiple file descriptors/connections in a single threaded process without CPU-intensive polling. In a multithreaded environment, and especially if you have prior experience with Java, I think it's easier to just spawn one thread per connection and use blocking I/O calls, because that's exactly what you would do in a Java program. A blocked thread takes 0% CPU cycles, and the parent thread can always terminate blocked child threads if necessary.

Of course timeouts still make sense to track down and clean up broken/dead connections.

---

