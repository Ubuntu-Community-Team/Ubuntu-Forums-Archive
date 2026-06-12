---
title: "socket.error errno.EWOULDBLOCK [PYTHON]"
date: 2010-09-05
forum: Programming Talk
---

### Post by mo.reina on 2010-09-05
can anyone tell me what the conditions have to be to raise this exception?

---

### Post by dwhitney67 on 2010-09-05
You setup your socket to be non-blocking.  When you attempted to read from this socket, the EWOULDBLOCK is the most likely response you would get unless you knew for certain that there was actual data to be read.

You should avoid reading a non-blocking socket unless you know for fact there is data to be read.  Use "select" to determine when there is data.

Try adapting this method to your code:
```

        def isSocketReadable(self, timeout = None):
                if timeout is None:
                        ready_to_read, ready_to_write, in_error = select.select([self.sock], [], [])
                else:
                        ready_to_read, ready_to_write, in_error = select.select([self.sock], [], [], timeout)
                return len(ready_to_read) > 0

```
If the method returns a value of true, then it is safe to read from the socket.

P.S.  It is also possible to receive an EINTR exception; this denotes that the operation (eg. read) has been interrupted by a signal.

---

### Post by mo.reina on 2010-09-05
actually it came from code that i was reading, but thanks for the function.

yeah from the docs it seems that if no data is being received, either because the stream is empty or it's not being sent for some reason the exception comes up.

by the way, aren't non-blocking sockets the key to asynchronous clients?  if you use blocking sockets then if you were reading from multiple sockets you'd have to wait for each socket to finish before reading from the next one.

---

### Post by mo.reina on 2010-09-05
actually, i just looked at the docs again and this is what it says

> In non-blocking mode, if a recv() call doesn&#8217;t find any data, or if a send() call can&#8217;t immediately dispose of the data, a error exception is raised;

so if i have
```
bytes = ''
bytes = socket.recv(1024)
```
and there is no more data to be received, what happens to the variable bytes?  does the code proceed or is an exception raised?

snippet:
```
while True:
                try:
                    bytes += sock.recv(1024)
                    if not bytes:
                        break
                except socket.error, e:
                    if e.args[0] == errno.EWOULDBLOCK:
                        break
                    raise

```

---

### Post by mo.reina on 2010-09-05
ok so...

no more data but socket on the server side is still open = exception
no more data due to socket on server side being closed = empty variable and so if clause

---

### Post by dwhitney67 on 2010-09-05
> **mo.reina said:**
> 
by the way, aren't non-blocking sockets the key to asynchronous clients?  if you use blocking sockets then if you were reading from multiple sockets you'd have to wait for each socket to finish before reading from the next one.

Not necessarily; it all depends on how one designs their application.

For instance, one could dedicate a separate thread for handling each client, thus mitigating the need to read from each socket in a "round-robin" fashion.  With separate threads handling a unique client, there's no need for a non-blocking socket.

If the server is only expecting small requests, and needs to forward back small amounts of data, then a single-thread would work.  But then again, if you are developing a web-server where 1000's (if not millions) of clients connect, this approach would be impractical.  In such a case, one would consider using a multi-threaded architecture, perhaps also with multiple systems to share in the load.

---

### Post by dwhitney67 on 2010-09-05
> **mo.reina said:**
> 
snippet:
```
while True:
                try:
                    bytes += sock.recv(1024)
                    if not bytes:
                        break
                except socket.error, e:
                    if e.args[0] == errno.EWOULDBLOCK:
                        break
                    raise

```

The code above neglects one issue; when the client disconnects from the server (for whatever reason), the recv() call will return, and indicate, that zero bytes have been read.  The code fails to handle this case.  It merely adds zero to the number of bytes read thus far, then attempts to read more!

Of course, with a non-blocking socket, the exception would be thrown almost immediately on the subsequent recv() call.  But bear in mind, that an EWOULDBLOCK exception is no reason to exit the while-loop, unless you are utilizing a select() somewhere along the line indicating that recv() should be called again.

In summary, the code above does not handle a client disconnect.

---

### Post by mo.reina on 2010-09-07
yep there is a select command, that's just a code snippet.  someone else on the irc channel made that very comment about the .recv() call receiving 0 bytes, i've tried the code with the socket in nonblocking mode and in fact it does end up in an infinite loop

---

### Post by dwhitney67 on 2010-09-07
> **mo.reina said:**
> yep there is a select command, that's just a code snippet.  someone else on the irc channel made that very comment about the .recv() call receiving 0 bytes, i've tried the code with the socket in nonblocking mode and in fact it does end up in an infinite loop

Something to the effect of this should resolve the issue, whether using blocking or non-blocking:
```

...

r, w, e = select.select(...)

if len(r) > 0 :
   while true :
      try :
         data = sock.recv(1024)

         if len(data) == 0 :
            break        # client disconnected

         bytes += data

      catch socket.error e :
         if e.args[0] == errno.EWOULDBLOCK :
            break
         raise

```

---

