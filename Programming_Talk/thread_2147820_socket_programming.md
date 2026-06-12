---
title: "socket programming"
date: 2013-05-23
forum: Programming Talk
---

### Post by ferizhandi on 2013-05-23
hi all

i wrote a sever with c. i put a non-terminate loop, but not work correctly.while loop not perform permanently.
in this code, i want to if there were no person to connect, recieve message from other clients that conected already.
For example: the last statement work a time.
what is wrong?!
what  should i do?!

```

    while(1)
    {
        int newSocket = accept(tcp_socket,(struct sockaddr*)&server_addr,&s);               

        if(newSocket<0)
        {
           // recv msg from client that conected beforhand
        }

        else
        {
            // if one client connect

        }
        write(1,"what\n",5);
    }
```

---

### Post by dwhitney67 on 2013-05-23
You should take a look at this [tutorial ]("http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html")to guide you along the journey of learning socket programming.

After doing a quick check of your "pseudo-code", I think you are misunderstanding as to how the accept() call behaves.  If you are using a blocking socket (this is typical) to receive client connections, then the accept() will block indefinitely until a client connects.  The accept() call will only return a value of less than 0 when an error occurs, and return a value greater than zero to indicate the socket descriptor of a client that has successfully connected.

If you want to determine when a client is sending data, you should consider using select() or poll() to manage the various sockets you have.  Always remember to manage the server's listen socket (ie. the one that accepts connections) and the sockets for any clients that are connected.

---

### Post by ferizhandi on 2013-05-23
Tanks a lot.

---

