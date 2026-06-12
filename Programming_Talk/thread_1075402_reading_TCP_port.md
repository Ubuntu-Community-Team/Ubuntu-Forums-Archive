---
title: "reading TCP port"
date: 2009-02-20
forum: Programming Talk
---

### Post by tneva82 on 2009-02-20
Not working at all. I can open the port without errors, I get client connected to it but reading results in -1 as a result.

```
  IPaddress readAddress;
  TCPsocket readSocket;
```

Just the address of server and the socket it's going to use for receiving.

```
int serverNetwork::openPort(int readPort) {
  
  if(SDLNet_ResolveHost(&readAddress, NULL, readPort) !=0) {
    printf("Address resolving failed!");
    exit(1);
  }

  readSocket=SDLNet_TCP_Open(&readAddress);

  if(!readSocket) {
    printf("SDLNet_TCP_Open: %s\n", SDLNet_GetError());
    exit(2);
  }
}
```

Resolve servers address and open socket to it. As far as I can see no real difference to example codes. Just names.

```
int serverNetwork::receiveData(char *answer, int maxLength) {
  return result=SDLNet_TCP_Recv(readSocket, answer, maxLength);
}
```

And here's where issues seems to be. Result is constantly -1. How What's causing that? SDL_Net doc's say just that it's error. Nothing about what sort of error.

And here's the code which uses class of which above are part of.

```
serverNetwork *server=new serverNetwork();
  char *answer=new char[120];
  int count;
  bool running=TRUE;
  server->openPort(4500);
  printf("Server running\n");
  while(running) {
    server->checkForConnections();
    count=server->receiveData(answer, 120);
    printf("%i\n", count); // prints -1 every time.

```

Anybody could point the(probably obvious) error I'm making?

---

### Post by johnl on 2009-02-20
It's hard to say because I can't see some of the relevant code.

I would wager this:
```

    server->checkForConnections();
    count=server->receiveData(answer, 120);

``` 

might be wrong.  what does server->checkForConnections() do?  You need to accept() a connection before you can recv() from it.

I am not familiar with the SDL stuff so I can't really say;  you might find it worthwhile to change your code to include a perror() statement like so, which will display why exactly the receive failed.

```

int serverNetwork::receiveData(char *answer, int maxLength) {
  int result;
  if ((result = SDLNet_TCP_Recv(readSocket, answer, maxLength)) == -1) {
    perror("Error receiving data");
  }

  return result;
}

```

---

### Post by tneva82 on 2009-02-20
[QUOTE=johnlmight be wrong.  what does server->checkForConnections() do?  You need to accept() a connection before you can recv() from it.[/quote]

Right. I forgot to mention that code. checkForConnections precicely calls accept() function. And I added it to return boolean to see wether connection is accepted. So if accept() returns non-NULL value checkForConnections return true(otherwise false) so connection is established as far as I can tell. It doesn't now even try to read data until checkForConnections returns true.

---

### Post by johnl on 2009-02-20
What are you doing with the return value of accept() ?  You need to recv() on the socket returned from accept(), not the original listening socket.

---

### Post by tneva82 on 2009-02-20
> **johnl said:**
> What are you doing with the return value of accept() ?  You need to recv() on the socket returned from accept(), not the original listening socket.

Ah the socket is stored in the class which is then used by the sendData. I use the return value simply to check that there was a connection made.

---

### Post by tneva82 on 2009-02-22
Right. Problem solved. What I messed up was that I didn't think up that I should use the socket given by TCP_Accept to both sending AND listening. I thought I would listen the port I had opened!

Annoying logical error but thankfully solved one!

---

