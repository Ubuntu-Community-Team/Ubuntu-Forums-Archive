---
title: "&quot;Unbinding&quot; sockets in c"
date: 2009-12-10
forum: Programming Talk
---

### Post by bamsanks on 2009-12-10
I'm learning how to use sockets in c, which is going reasonably well.
My issue is that after I have successfully compiled and run my program, the ports/sockets are apparently still in use the next time I run the program, causing it to fail.
It seems that as soon as I close the terminal in which I ran the first instance of the program, I can run another instance.
Any ideas as to whether this is a programming issue or whether the terminal is supposed to keep the ports open?
It can get annoying having to close and open a new terminal every time I want to run the program.

---

### Post by dwhitney67 on 2009-12-10
After you have opened the socket, and have obtained a valid socket descriptor, issue the following configuration for the socket:
```

const int       optVal = 1;
const socklen_t optLen = sizeof(optVal);

int rtn = setsockopt(sd, SOL_SOCKET, SO_REUSEADDR, (void*) &optVal, optLen);

assert(rtn == 0);   /* this is optional */

```
As for your current conundrum with the sockets still appearing as if they are binded, just give your system a few moments (maybe minutes) to clean up.

---

### Post by bamsanks on 2009-12-10
Excellent. Thankyou very much.

---

### Post by slavik on 2009-12-11
have you tried closing the socket on exit?

---

### Post by bamsanks on 2009-12-11
Yep. I was doing that. The problem seemed to be that the address was still in use while the terminal was open, which was solved by changing the SO_REUSEADDR option.

---

