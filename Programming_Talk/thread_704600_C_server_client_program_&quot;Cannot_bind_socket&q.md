---
title: "C server client program &quot;Cannot bind socket&quot; after being run 10 times"
date: 2008-02-22
forum: Programming Talk
---

### Post by earobinson on 2008-02-22
If I run the error.sh shell script 10 times or more I eventually get the "Cannot bind socket" anyone know why this is? All the program is trying to do is to make a socket connection and then terminate.

It should just keep connecting no?

Thanks

---

### Post by rodo-&gt;dave on 2008-02-22
Hi!
I've been goofing around with it a bit, but have not solved the problem....

I get "Cannot bind socket: [98]:[Address already in use]" for the error.

```

    // Bind listen socket to listen port.
    server_address.sin_family = AF_INET;
    server_address.sin_addr.s_addr = htonl(INADDR_ANY);
    server_address.sin_port = htons(listen_port);

    if (bind(*listen_socket, (struct sockaddr *) &server_address, sizeof(server_address)) < 0) {
        printf("Cannot bind socket: [%d]:[%s]\n", errno, strerror(errno));
        return(1);
    }

    // Wait for connections from clients.
    listen(*listen_socket, 5);
    return(0);

```

---

### Post by rodo-&gt;dave on 2008-02-22
Ok. I was thinking there must be some data still lingering in the queue so I added a recv() and it appears to be working ok now...

In Server.c - 
```

int main(int argc, char** argv) {
    char data[1024];

    if (init_listen_socket(&listen_socket, PORT) == 1) {
        return(1);
    }

    connect_to_client();

    recv(socket_fd, data, sizeof(data), 0);

    //close(listen_socket);
    //close(socket_fd);

    return(0);
}

```

---

### Post by supirman on 2008-02-23
From [Beej's guide to networking]("http://www.beej.us/guide/bgnet/output/html/singlepage/bgnet.html"):

Sometimes, you might notice, you try to rerun a server and bind() fails, claiming "Address already in use." What does that mean? Well, a little bit of a socket that was connected is still hanging around in the kernel, and it's hogging the port. You can either wait for it to clear (a minute or so), or add code to your program allowing it to reuse the port, like this:

[PHP]int yes=1;

// lose the pesky "Address already in use" error message
if (setsockopt(listener,SOL_SOCKET,SO_REUSEADDR,&yes,sizeof(int)) == -1) {
    perror("setsockopt");
    exit(1);
} 
[/PHP]

So the sequence should be 
socket()
setsockopt()
bind()

---

### Post by earobinson on 2008-02-23
Thanks this seems to work perfectly

---

### Post by earobinson on 2008-02-23
Question is there something similiar I should be doing on the client side?

---

### Post by supirman on 2008-02-23
You shouldn't need to do that on the client side, as it only comes into play when you try to bind().

---

### Post by ruy_lopez on 2008-02-23
There shouldn't be any problem with clients. The client port is chosen automatically, typically from 49152-65535, so called *ephemeral* ports. The client won't reuse the same port in quick succession.

Since a socket is an address/port pair, you only get reuse errors with servers. With clients the ephemeral port makes the socket different each time.

---

