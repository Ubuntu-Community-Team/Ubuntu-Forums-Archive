---
title: "Need help on client-server over FIFOs"
date: 2010-03-07
forum: Programming Talk
---

### Post by mordorblue on 2010-03-07
Hi guys, i just started to learn C programming. Recently i tried to create a program for which client and server that using FIFO to be able communicated with each other. But somehow i think they both failed to run or detect a pipe from each other. Any help is really appreciated. :-k

[ATTACH]149281[/ATTACH]

[ATTACH]149282[/ATTACH]

---

### Post by dwhitney67 on 2010-03-07
Comments for server.c:

You are missing function declarations; if you had these, then the compiler would have told you that both the child() and the parent() functions are being called incorrectly.  Look at the parameters!

The main() function should be explicitly declared to return an int.

Remove unnecessary global variables.  These should be declared at the closest point to where they are used.

I would suggest that you re-evaluate the declaration of msgbuf; keep it simple and declare it as follows:
```

const unsigned int MSGSIZ = 10;
char msgbuf[MSGSIZ];

```
Later, do not use MSGSIZ in your code when it is just as convenient to use sizeof(msgbuf), or strlen(msgbuf) if using null-terminated data.  Note that fgets() will read one-less than the size specified so that a null-termination character can be placed at the end of the buffer.  With a MSGSIZ of 10, you will have space for nine characters and then the tenth will be for the null.

Using a "+ 1" everywhere when referring to the size msgbuf can lead to confusion, and perhaps errors (eg. buffer overrrun).

-------------------------

Comments for client.c:

Read comments above for the server.

--------------------------

P.S.  Step 1 is t fix your code so that it compiles!  Try:
```

gcc -Wall -std=gnu99 server.c -o server
gcc -Wall -std=gnu99 client.c -o client 

```

---

