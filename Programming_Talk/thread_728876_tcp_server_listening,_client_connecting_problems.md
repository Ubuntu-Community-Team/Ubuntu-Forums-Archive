---
title: "tcp server listening, client connecting problems"
date: 2008-03-19
forum: Programming Talk
---

### Post by pjwhite on 2008-03-19
hello everyone. I tried searching for something related to this, but I figured it was time to ask my own question. I am experiencing these problems using Ubuntu 7.04

I am starting up a TCP listener/server and once connected, will act as a communication/control link with a program on another computer. In the final iteration I want it to run it like a daemon, disconnected from a controlling process so I am going to do:

```
result = fork()
if (result == 0){
    //close stdio handles and reopen to /dev/null
    setsig()
    umask(0)

    socket()
    bind()
    listen()
    accept()

    while(keep_reading)
        read()
        do_my_stuff()
}
else
    _exit(0)
```

This is simplified as i am using functions and setting socket options, particularily the SO_REUSEADDR option.

If I do NOT run the fork and just run the socket->bind->listen->accept I get the same problems.

I do check for all errors for all calls and receive none. Using lsof and netstat, it shows my socket in LISTEN mode. If the connection is made, then the program works exactly as planned.

**The problem is:**

The client connecting, whether it is my client, or even netcat will connect properly, but then the server immediately sends a disconnect. The server does not get out of accept() during this, and even stranger it is random, and sometimes it works (60%), and sometimes it doesn't (40%).

I could tell it connected and disconnected right away by using wireshark, I got a SYN -> SYN/ACK -> ACK and then right away FIN/ACK -> FIN/ACK -> FIN. Using netstat -ta also shows the ports getting gummed up in TIME_WAIT as though it did connect and disconnect.
[B]
What i think could be the problem[/B]

Two things I have done:

one is to not set the SO_REUSEADDR parameter, and it then works as expected, although I have not done as much testing because it requires you to wait for a minute after each test for the TIME_WAIT to clean up.

two, before I set up the socket, I read some parameters from a config file, by opening and closing it. If I comment this out and hard-code the port to listen on, etc, the occurance of it is MUCH less, although can still happen.



I am at my wits end with this. Is there anything I can do to figure this out or help debug it. I am pretty sure it has to do with file handles getting gummed up or something like that. But i have no Idea!

Thanks for reading!

---

### Post by ruy_lopez on 2008-03-19
You are exiting the parent on fork(). Is that what you want?

Try making the parent wait for the child to exit.
```

waitpid(result, &status, 0);
if (WIFEXITED(status))
        printf("child %d exit status: %d\n", result, WEXITSTATUS(status));

```

---

### Post by pjwhite on 2008-03-19
> **ruy_lopez said:**
> You are exiting the parent on fork(). Is that what you want?

Try making the parent wait for the child to exit.
```

waitpid(result, &status, 0);
if (WIFEXITED(status))
        printf("child %d exit status: %d\n", result, WEXITSTATUS(status));

```


But I want the process to be able to disconnect from the controlling process, such as a terminal window. So i can now start my program and it immediately disconnects from the parent to become owned by init.

However, the problem exists if i DON"T do the fork(), I still get into this state...

---

### Post by themusicwave on 2008-03-19
Bugs like this always remind me that you can take nothing for garnted in client server applications, especially on the server end.  The server needs to have lots of error checking and handle lots of scenarios.

For instance, what happens if the client disconnects in the middle of a read?  Can they reconnect?  Is the corrupt data thrown out?

You have to think about all of this when writing a server.  Imagine the client is on it's worst behavior at all times and things will go much easier.

---

