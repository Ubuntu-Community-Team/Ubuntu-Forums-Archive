---
title: "Questions with the read() function"
date: 2009-08-10
forum: Programming Talk
---

### Post by darthshak on 2009-08-10
I am learning the Sockets API and I decided to try out the first example in Richard Stevens' book "Unix Network Programming Volume 1 : The Sockets Networking API"

The first program is a simple echo program where the client app types in text that is sent to the server. The server sends the text back to the client and is displayed on the client's screen.

The following a quote from the book on directly using the read() function to read from a socket : 
> 
Stream sockets (e.g., TCP sockets) exhibit a behavior with the read and write functions that differs from normal file I/O. A read or write on a stream socket might input or output fewer bytes than requested, but this is not an error condition. The reason is that buffer limits might be reached for the socket in the kernel. All that is required to input or output the remaining bytes is for the caller to invoke the read or write function again.

Now, I never really faced this problem in my program. Could someone give me an example of how using the read() function creates the problem above?

---

### Post by jamescox84 on 2009-08-10
Maybe something like this.

```

char  buffer[1024];
char *p          = buffer;
int   bytes_read = 0;
do {
        bytes_read = read(p, sizeof(char), 1024, socket_descriptor);
        p += bytes_read;
} while ((bytes_read != 0) && (p < (buffer + 1024)));

```

Just keep reading until your buffer gets full, or you `read' returns no new data.

---

### Post by dwhitney67 on 2009-08-10
> **jamescox84 said:**
> Maybe something like this.

```

char  buffer[1024];
char *p          = buffer;
int   bytes_read = 0;
do {
        bytes_read = read(p, sizeof(char), 1024, socket_descriptor);
        p += bytes_read;
} while ((bytes_read != 0) && (p < (buffer + 1024)));

```

Just keep reading until your buffer gets full, or you `read' returns no new data.
This code is _almost_ correct, however you neglected to check if the read() returns an error.  In such case, the bytes_read would have a value less than zero... and then, well, the rest is obvious.

Consider this code, which uses the more familiar recv() versus read(), for reading from a socket:
```

char buffer[1024] = {0};
int  bytes_read   = 0;

while (bytes_read < sizeof(buffer))
{
   int rtn = recv(sd, buffer + bytes_read, sizeof(buffer) - bytes_read, 0);

   if (rtn <= 0) break;

   bytes_read += rtn;
}

```

P.S.  I should add that neither recv() nor read() should be called without first verifying that there is indeed something to be read.  Otherwise, they will block... unless of course, one has setup a non-blocking socket.

---

