---
title: "forking for multiple clients"
date: 2011-06-18
forum: Programming Talk
---

### Post by kapil1503 on 2011-06-18
hello,
i am making a chat server for multiple clients in c using linux. i have made the following client and server programs. but i cannot understand how to apply forking for multiple clients. please help. thank you.

---

### Post by BkkBonanza on 2011-06-18
You probably want to use threads not forking. You would define the process function suitable for being a seperate thread and then create a new thread to handle each incoming connection. It's not too hard but you do need to become familiar with how it works before jumping in. 

There's many threading tutorials on the web and google is going to be your best help with this. Maybe this one will get you started...

[https://computing.llnl.gov/tutorials/pthreads/](https://computing.llnl.gov/tutorials/pthreads/)

---

### Post by kapil1503 on 2011-06-18
hello,
actually i already have used threads in the past. this time i want to try with forks. could you please help me out with this?

---

### Post by dwhitney67 on 2011-06-18
> **kapil1503 said:**
> hello,
i am making a chat server for multiple clients in c using linux. i have made the following client and server programs. but i cannot understand how to apply forking for multiple clients. please help. thank you.

I tested your programs, and they seem to be working fine.  The client and server apps could use some more output; in other words, you should consider printing a prompt so that the user knows to input data.  On the server side, you should use a prompt that includes the client information (e.g. IP address and/or port number) so that you know which client is being responded to.

Now for some code commentary...

1.  Why is the following in your server code?
```

unlink("server_socket");

```
This applies to servers that use AF_UNIX style sockets; you're using AF_INET.


2.  Do you wish for clients to connect to your server from other systems?  If so, the following line of code will not permit that:
```

server_address.sin_addr.s_addr = inet_addr("127.0.0.1");

```
Change it to:
```

server_address.sin_addr.s_addr = htonl(INADDR_ANY);

```


3.  Never use gets(); use fgets() instead.
```

gets(buffer2);

```
```

fgets(buffer2, sizeof(buffer2) - 1, stdin);

```


4.  Be cautious about reading/receiving an amount of data that is equivalent to your buffer size.  You may fail to obtain a terminating null character at the end of the buffer, or as your applications seem to expect, a newline character.

Thus after gathering user input, I would recommend that you send only the number of bytes contained within the input message; use strlen() to determine that.

---

