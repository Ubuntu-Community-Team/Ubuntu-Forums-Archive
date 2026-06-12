---
title: "how can I check if  a port is available locally?"
date: 2007-08-29
forum: Programming Talk
---

### Post by yinglcs2 on 2007-08-29
Hi,

I am trying to write a function to check if a port is available locally.

Here is my code:  In most case, it works.   In one case, it still returns true (i.e. avaiable) and when i do a 'netstat -na | grep <port>', it is being used.

Can you please tell me if the following code that I have is sufficient to check if a port is available locally?

Thank you.


isPortAvailable(int port)
{

  int sock;

  if ( (sock = socket(AF_INET, SOCK_STREAM, 0)) == -1)     
    return false;
  
  struct sockaddr_in server;
  
  server.sin_family = AF_INET;
  server.sin_addr.s_addr = htonl(INADDR_ANY);
  server.sin_port = htons( port);

  if (bind (sock, (struct sockaddr *) &server, sizeof (server)) == -1)  {
    close (sock);
    return false;
  } else {  
    close (sock);  
    return true;
  }
}

---

### Post by dwhitney67 on 2007-09-06
I would remove the code that obtains a socket and implement this elsewhere.  Otherwise you unnecessarily create a socket for each port, which may not be available.

Consider this (pseudo code):

```

static const int MIN_PORT = 1000;
static const int MAX_PORT = 2000;
int sock = socket( ... );

for (int port = MIN_PORT; port <= MAX_PORT; ++port)
{
  if ( isPortAvailable( sock ,port ) )
  {
    // do something with the socket/port
  }
}
```

I hope this helps.  Btw, there is a range of port numbers that are restricted to root-privileged applications.  I want to say these are from 0 to 900, but I cannot remember exactly the upper limit.

P.S.
I would also recommend that you consider implementing your application in C++ so that you can define different types of Socket classes:  one for TCP and another for UDP.  There is also the minute differences between how a server and a client operate with respect to sockets.

---

