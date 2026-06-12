---
title: "select() and pthread"
date: 2010-07-05
forum: Programming Talk
---

### Post by dawwin on 2010-07-05
I am writing a simple server program and I've got a question about select() and threads. I wrote following function:
```

int recv_timeout(int s, char *buffer, int msg_len, int seconds)
{
        struct timeval tv;
        fd_set rset;
        int maxfdp1;
        int result;
        
        FD_ZERO(&rset);
        FD_SET(s, &rset);
        maxfdp1 = s + 1;
        tv.tv_usec = 0;
        tv.tv_sec = seconds;
        
        switch (select(maxfdp1, &rset, NULL, NULL, &tv)) {
            case -1: 
                return -1;
            case 0: 
                return 0;
            default:
                if (FD_ISSET(s, &rset) != 0) {
                        result = recv(s, buffer, msg_len, MSG_NOSIGNAL);
                        if (result == 0) {
                                result = -1;
                        }
                        
                        return result;
                } else {
                        return -1;
                }    
                
                break;
        }
        
        return -1;
}

```It's recv() with timeout. I used select() for timeout. 
Ii my program I create thread for each user. 
It this save to use select() in posix threads?

---

### Post by dwhitney67 on 2010-07-05
AFAIK, select() is thread-safe.

---

