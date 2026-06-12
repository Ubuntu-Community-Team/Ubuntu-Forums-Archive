---
title: "recv behaving strangely in Ubuntu"
date: 2009-09-24
forum: Programming Talk
---

### Post by mitch_feaster on 2009-09-24
So I'm getting some weird behavior with the recv function in C (berkeley sockets). It isn't blocking like it "should" be. It's behaving as though I had OR'd MSG_DONTWAIT into the flags on the call to recv, or set up the socket as non-blocking -- but I haven't done either of those two things.

Now, the reason this is "weird" to me is that **it seems to be Ubuntu-specific.** The same code behaves as expected in Red Hat and even Debian.



Here's how I'm calling recv:

```

    if ( (nbytes = recv(sock, buf, MAX_MSG, 0) == -1) ) { /*recv error*/
        perror("recv error");
        exit(EXIT_FAILURE);
    }
    //we successfully returned from recv
    printw("Received %d bytes of data...Such as %s\n", nbytes, buf->code);
    /*In Ubuntu recv returns immediately, setting nbytes to 0!*/

```

And here's how I'm creating the socket:

```

    //open socket:
    if ( (sock = socket(PF_INET, SOCK_STREAM, 0)) == -1 ) {
        perror("Error creating socket");
        exit(EXIT_FAILURE);
    }

```

Any ideas on why this is happening (only in Ubuntu)?

---

### Post by mitch_feaster on 2009-09-25
It never fails that whenever I post to the forums after struggling with something for hours upon hours, I solve my own problem within a few minutes of my posting. :-)

If you ask me, this is really "weird". All I changed was how I was setting up the IP address and now it works under Ubuntu...

Old code:
```

        char *ip;
        ip="127.0.0.1";

```

New code:

```

        char ip[MAX_IP];
        printw("Enter IP address of server (enter nothing for localhost): ");
        getstr(ip);
        if (strcmp(ip,"") == 0)
            strcpy(ip, "127.0.0.1");

```


I have no idea how that would be related to the recv function (and only in Ubuntu) but oh well... Even though I'm no longer having the issue I was having I would be interested in any light anyone has to shed on the topic.

---

