---
title: "Having a problem with sockets"
date: 2011-09-01
forum: Programming Talk
---

### Post by jmknsd on 2011-09-01
I've spent the summer working on a gsoc project and I have encountered a problem that I have been unable to solve. 

I'm using the event loop tools that come with the wayland demo compositor, and I create a remote socket and add it to the event loop/epoll. Once the socket is written to, the handling function calls accept. I have put printfs above and below this statement, printing out the epoll fd, and the accept call changes it somehow. I am allocating a new fd for this accept call, and the epoll fd is stored in a different struct. Here is the function that makes the accept call:

[https://github.com/kempj/remote-wayland/blob/master/rwl_client.c#L569](https://github.com/kempj/remote-wayland/blob/master/rwl_client.c#L569)

Debugging this requires the accompanying psuedo compositor to be running, as well as a normal wayland client and compositor, so debugging takes a bit of set up, but I can run anything needed.

Thanks for your help,
    Jeremy

---

### Post by dwhitney67 on 2011-09-02
In the future, please post your code on this forum, not on some third-party site that may be unavailable in the future.  Some day someone may find this thread looking for answers to a similar question that you have, but they may not have the privilege of seeing your original code and any errors it may contain.

And speaking of errors... how are you compiling your code?  This little error should have been caught by the compiler:
```

if((remote_fd = accept(fd,(struct sockaddr *) &incoming_addr, **size**)) == -1){

```
You need to pass the address of the "size" variable so that accept() can tell you the size of the sockaddr structure that it returns.

Also, what were you thinking with this?
```

port = (char *)&"35000\0";

```
This would have sufficed (and it not the same as what you attempted!):
```

port = "35000";

```

Undoubtedly there are other issues with the code, but since I do not have the Wayland development package on my system, it will be hard to deduce these without having the privilege of compiling the code.

My suggestion to you is that you learn socket programming separately from learning to develop with Wayland.  Trying to learn both at the same time seems unwise.

Here is a good link to a guide/tutorial that you can use for socket programming: [http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html](http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html)


P.S.  When compiling with gcc, use the -Wall and -pedantic options; fix any/all code that generates warnings!

---

