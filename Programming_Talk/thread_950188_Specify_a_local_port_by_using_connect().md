---
title: "Specify a local port by using connect()"
date: 2008-10-16
forum: Programming Talk
---

### Post by f.ben.isaac@gmail.com on 2008-10-16
```


struct addrinfo hints, *res;
int sockfd;

// first, load up address structs with getaddrinfo():
memset(&hints, 0, sizeof hints);
hints.ai_family = AF_UNSPEC;
hints.ai_socktype = SOCK_STREAM;

getaddrinfo("www.example.com", "3490", &hints, &res);

// make a socket:
sockfd = socket(res->ai_family, res->ai_socktype, res->ai_protocol);

// connect!
connect(sockfd, res->ai_addr, res->ai_addrlen);

```

This is an example where we make a socket connection to “[www.example.com”](www.example.com”), port 3490....
[U]
we didn't call bind(). Basically, we don't care about our local port number; we only care where we're going (the remote port). The kernel will choose a local port for us, and the site we connect to will automatically get this information from us. [/U]


Isn't port 3490 getaddrinfo("www.example.com", "3490", &hints, &res);
refers to the local port? -  The underlined part confuses me, because we already specified the local port which is 3490....

I'm confused

---

### Post by dwhitney67 on 2008-10-16
A server, web or otherwise, will perform the following steps:

1.  create a socket
2.  bind the socket (to a port)
3.  listen on the socket
4.  accept connections (from clients)

The client (which it seems you are trying to create) needs to do the following:

1.  create a socket
2.  connect to the server (at whatever port/hostname the server is using)

I recently posted a TCP/UDP Socket library here on the forums recently.  Perhaps you could use it in lieu of going through all of the tedious steps of setting up your client's socket?  But based on how you are setting up your socket, it may not meet your needs.

The Socket library can be found here:
[http://ubuntuforums.org/showpost.php?p=5987396&postcount=8](http://ubuntuforums.org/showpost.php?p=5987396&postcount=8)

And, perhaps to further assist you, here's an example of setting up a client (the hard way!):
[php]
  // create socket
  int sd = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP);

  assert(sd > 0);

  // connect to the server
  const char*          serverHost = "localhost";
  const unsigned short port       = 9100;

  hostent* host = gethostbyname(serverHost);

  assert(host != 0);

  sockaddr_in destAddr;
  memset(&destAddr, 0, sizeof(destAddr));

  destAddr.sin_family      = AF_INET;
  destAddr.sin_addr.s_addr = *((unsigned long*) host->h_addr_list[0]);
  destAddr.sin_port        = htons(port);

  if (connect(sd, (sockaddr*) &destAddr, sizeof(destAddr)) == -1)
  {
    std::cout << "connect failed; reason = " << strerror(errno) << std::endl;
    return 1;
  }

[/php]

---

### Post by f.ben.isaac@gmail.com on 2008-10-24
Remember, i'm trying to connect to remote host...

Your advice helped me alot though.

---

### Post by dwhitney67 on 2008-10-24
> **f.ben.isaac@gmail.com said:**
> Remember, i'm trying to connect to remote host...

Yes, I see... [www.example.com](www.example.com), at a particular port number (3490?).  I will try the same when I get back home (please remind me).  Right now my Ubuntu system is not networked.  I'm posting via WinXP.  I will be able to test on 29/10/08.

---

### Post by f.ben.isaac@gmail.com on 2008-10-26
I SOLVED IT. Your answer helped me too...

Thats how i did it:

```

struct sockaddr_in *specifyPort = (struct sockaddr_in *)results->ai_addr;

		specifyPort->sin_port = htons(startingPort);

		int connectStatus;
		connectStatus = connect(socketfd, results->ai_addr, results->ai_addrlen);


```

---

