---
title: "C/C++ Socket Programming Question"
date: 2010-04-27
forum: Programming Talk
---

### Post by Ner0suM on 2010-04-27
I am trying to create a program that simulates Distance Vector Routing. I spawn about 5 different children and I need each child to be able to talk between each other using sockets. There is no need for ports because this is a connectionless implementation.

Does anyone know how to set up BSD sockets so that I can get child processes to communicate with one another?

---

### Post by dwhitney67 on 2010-04-27
What protocol do you want to use, TCP or UDP?

You can bind a socket to a file, typically a temporary one, say in /tmp.

For example, for TCP:

```

const char* mySocketName = "/tmp/mySocket";

int sd = socket(AF_UNIX, SOCK_STREAM, IPPROTO_TCP);

sockaddr_un addr;
addr.sun_family = AF_UNIX;
strncpy(addr.sun_path, mySocketName, strlen(mySocketName));

bind(sd, (sockaddr*), &addr, SUN_LEN(&addr));
listen(sd, 5);

int client_sd = accept(sd, 0, 0);

if (client_sd > 0)
{
   // deal with client
}

```

---

### Post by Ner0suM on 2010-04-27
> **dwhitney67 said:**
> What protocol do you want to use, TCP or UDP?

You can bind a socket to a file, typically a temporary one, say in /tmp.

For example, for TCP:

```

const char* mySocketName = "/tmp/mySocket";

int sd = socket(AF_UNIX, SOCK_STREAM, IPPROTO_TCP);

sockaddr_un addr;
addr.sun_family = AF_UNIX;
strncpy(addr.sun_path, mySocketName, strlen(mySocketName));

bind(sd, (sockaddr*), &addr, SUN_LEN(&addr));
listen(sd, 5);

int client_sd = accept(sd, 0, 0);

if (client_sd > 0)
{
   // deal with client
}

```

Yeah I was using several temporary files earlier. I didnt find the idea appealing and gave up on it. If it works for me ill give it a shot though.

As for my protocol field my socket looked something like this

socket(AF_UNIX, SOCK_DGRAM, 0);

and i was getting connection refused errors. I will have to switch to linux to actually view my code.

---

### Post by dwhitney67 on 2010-04-27
> **Ner0suM said:**
> Yeah I was using several temporary files earlier. I didnt find the idea appealing and gave up on it. If it works for me ill give it a shot though.

As for my protocol field my socket looked something like this

socket(AF_UNIX, SOCK_DGRAM, 0);

and i was getting connection refused errors. I will have to switch to linux to actually view my code.

SOCK_DGRAM is synonymous with UDP.  UDP supports connectionless sockets, but also permits one to setup a connection.

To setup a connection to a server's AF_UNIX socket, something like this is done by the client:
```

sockaddr_un serverAddr;

memset(&serverAddr, 0, sizeof serverAddr);

serverAddr.sun_family = AF_UNIX;
strncpy(serverAddr.sun_path, socketName, strlen(socketName));

if (connect(sd, (sockaddr*) &serverAddr, SUN_LEN(&serverAddr)) == -1)
{
   // error
}

```

---

### Post by Ner0suM on 2010-04-27
Thanks for your reply's Ill see if I cant get something working out of these examples.

---

