---
title: "accept ans select"
date: 2009-08-02
forum: Programming Talk
---

### Post by vralfy on 2009-08-02
Hi,
i'm trying to code a TCP server/client program in C++. I intitialize the hole socket, an finaly i come to this:
```

void Server::acceptNewPlayer() {
    struct sockaddr_in cad;
    socklen_t alen = sizeof(cad);
    int cid;
    if ((cid = accept(this->sd,(struct sockaddr *)&cad, &alen)) < 0) {
        fprintf(stderr,"accept failed\n");
    } else {
        /* at this point i habe an socket to communicate with the client */
        printf("New player connected\n");
    }
}
```everything works fine while i call this function in an infinity loop. But the problem is, that *accept* blocks the whole program until a client connects. So i tryed to use *select* as follows:
```

int sd;
fd_set fds;

``````

void Server::run() {
    FD_ZERO(&this->fds);
    FD_SET(this->sd+1,&this->fds);
    struct timeval tv;
    tv.tv_sec=1; tv.tv_usec=100;
    int retval = select(this->sd+1,&this->fds, NULL, NULL, &tv);
    if (FD_ISSET(this->sd,&this->fds)) {
        if (retval<0) printf("retval<0\n");
        else if (retval)  this->acceptNewPlayer();
    } else printf("FD not set\n");
}

```This routine also runs in an infinity loop. All i  can see on my screen is "FD not set". Why?

Bye
vralfy

---

### Post by dwhitney67 on 2009-08-02
Your code appears to have some "holes" in it.

The accept() will block indefinitely unless you have setup the socket to be non-blocking.  For socket that is blocking, the use of select() is preferred.  So in this respect, you are on the correct path.

I do not have your complete code, but this is how I would approach setting things up:
```

int sd = socket(...);
bind(sd, ...);
listen(sd, 5);

// main loop
fd_set savefds;
FD_ZERO(&savefds);
FD_SET(sd, &savefds);

while (true)
{
   fd_set readfds = savefds;  // this must be set before each call to select()
   timeval timeout = {1, 0};  // this must be set before each call to select()

   int sel = select(sd + 1, &readfds, 0, 0, &timeout);

   if (sel > 0 && FD_ISSET(sd, &readfds))
   {
      // client connected
   }
   else if (sel == 0)
   {
      // timeout occurred
   }
}

```
You did not indicate if you plan to monitor more than one client, and if so, if you planned to utilize the same select() used for monitoring your server's listen socket.  Doing so adds a little more detail to the code than shown above.

Btw, if you want to use my [Socket Library]("http://www.softhouseproductions.com"), you more than free to do so.  The code above would boil down to:
```

TCPServerSocket sock;

while (true)
{
   timeval timeout = {1, 0};

   if (sock.activityDetected(&timeout))
   {
      TCPSocketPtr client = sock.accept();

      // do something with the client
   }
   else
   {
      // timeout occurred
   }
}

```

P.S.  In the code you originally posted, the client's socket descriptor is declared as a local variable in your acceptNewPlayer() method.  You probably want to add that socket descriptor to a container (eg. an STL set or list) before the method returns.

---

### Post by vralfy on 2009-08-03
Thanx!!!
i didn't know the fd_set has to be set everytime before i call the select. I did socket programming a long time ago and i didn't had to set it everytime.

i changed the following:

```

fd_set readfds = this->fds; /* so that's it */
struct timeval tv = {1, 0};
int retval = select(this->sd+1,&readfds, NULL, NULL, &tv);

```

Thanx again!

vralfy

---

