---
title: "[C] send() with timeout"
date: 2010-09-01
forum: Programming Talk
---

### Post by dawwin on 2010-09-01
Is this enough to use select() before send() to make it blocking only for given time?
I wrote something like this
```

int send_all(int s, char *buffer, int msg_len)
{
        int sent;
        int not_sent;
        int n;
        struct timeval tv;
        fd_set sset;
        int maxfdp1;
        
        sent = 0;
        not_sent = msg_len;
        FD_ZERO(&sset);
        FD_SET(s, &sset);
        maxfdp1 = s + 1;
        tv.tv_usec = 0;
        tv.tv_sec = SEND_TIMEOUT;
        
        while (sent < msg_len) {
                switch (select(maxfdp1, NULL, &sset, NULL, &tv)) {
                        case -1: 
                            return -1;
                        case 0: 
                            return -1;
                        default:
                            if (FD_ISSET(s, &sset) != 0) {
                                    n = send(s, buffer+sent, not_sent, MSG_NOSIGNAL);
                                    if (n <= 0) {
                                            return -1;
                                    }
                            } else {
                                    return -1;
                            }    
                            
                            break;
                }
                
                sent += n;
                not_sent -= n;
        }
        
        return 0;
}

```

---

### Post by dwhitney67 on 2010-09-01
I've never used select() to determine when it is appropriate to write (ie send), but I suppose it is reasonable.

Important:  You will need to reset the value within 'sset' every iteration of the while loop; ditto for the 'tv' value.  Both of these value are manipulated with each call to select().

Btw, why would you need a timeout for sending data?  Are you concerned that the recipient will not read their end of the socket quick enough?

P.S.  A return value of less than zero from send() does not necessarily indicate a "fatal" error; there are cases, such as when errno is equal to EWOULDBLOCK (EAGAIN) or EINTR, that you may want to consider looping back again to attempt the send().

---

### Post by dawwin on 2010-09-01
I need timeout for send() because it can be blocked for example when I disconnect my ethernet cable. send() can block and child process that handle connection will never exit.

---

### Post by Zugzwang on 2010-09-01
> **dawwin said:**
> I need timeout for send() because it can be blocked for example when I disconnect my ethernet cable. send() can block and child process that handle connection will never exit.

Actually, does this really happen and did you try it? I would suspect that all reasonable TCP implementation will consider the connection to be lost after some period of time (which may however well have a magnitude in the order of minutes). Then, the "send" call should return "-1" and "errno" should be set to something like "ECONNRESET".

---

### Post by dawwin on 2010-09-01
Yes, I tested it and it can happend

EDIT:
I found this in linux kernel manual
```

       When the message does not fit into the send buffer of the socket, **send**()
       normally blocks, unless the socket has been placed in nonblocking I/O mode.

```

EDIT2:
There is timeout, but it is about 20 minutes

---

### Post by MadCow108 on 2010-09-01
man setsockopt
man 7 socket
```

struct timeval tv;
tv.tv_sec = 20;
tv.tv_usec = 0;
setsockopt(sock, SOL_SOCKET, SO_SNDTIMEO, &tv, sizeof(struct timeval))
// SO_RCVTIMEO for recv timeout

```
but it may not be supported by your plattform

---

