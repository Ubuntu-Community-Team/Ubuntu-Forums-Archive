---
title: "[C] How to detect if a socket is closed?"
date: 2010-12-01
forum: Programming Talk
---

### Post by Royk14 on 2010-12-01
Hi, it's me again.
I'm still working on that server-client project and I have another doubt.

I have something like this (server) :

listen(sockfd, 250);

while(1){

newsockfd = accept(sockfd, ...);

...
}

so I'm accepting connections from, at most, 250 clients at the same time.
So, in each loop, the server will stay blocked on 'accept' until a client connects.
What I want is to break the loop whenever I (user) want. I was thinking about to close 'sockfd'.

Is that effective?
What happens if i close 'sockfd'?
How can I know, just before making the 'accept', if 'sockfd' is closed or not?
What will 'accept' return?

Thanks in advance.

---

### Post by Some Penguin on 2010-12-02
*shrug*  Does it matter whether you check before?  After all, there is no guarantee that the connection won't close while you're blocked waiting for a connection...

...in which case "-1 is returned and errno is set appropriately", to quote the man page.

---

### Post by dwhitney67 on 2010-12-02
If you close sockfd (ie your listener socket), then any connected client will still remain connected.  The accept() returns a new socket when the client connects; if you want to disconnect the client, then the socket descriptor returned by accept() is the one you want to close.

Please note that if after you break from your listener while-loop, and your next action is to exit the application, that each of your clients will be disconnected, unless of course you initiated a separate process (ie. fork) to handle each client.

---

