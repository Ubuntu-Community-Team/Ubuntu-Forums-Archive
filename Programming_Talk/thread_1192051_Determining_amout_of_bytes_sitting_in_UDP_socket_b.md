---
title: "Determining amout of bytes sitting in UDP socket buffer"
date: 2009-06-19
forum: Programming Talk
---

### Post by ittiam on 2009-06-19
I would like to know how many bytes is my udp socket having so that i can allocte my buffer to receive it? In UDP it is not possible to read like TCP, for example read the header first, then determine the length anda allocate.

---

### Post by dwhitney67 on 2009-06-19
I do not know of any way to determine the amount of bytes awaiting in the receive queue of the UDP socket.

If you have established a protocol between the client and the server in which perhaps the first byte or two of the message contain the message length, then you can peek at the message without retrieving it.

Something like:
```

char len[2] = {0};

recv(sd, len, sizeof(len), MSG_PEEK);  // get the 1st two bytes that contain the msg length

// convert the information to a usable number (the ntohs() may be overkill)
const unsigned short* lenptr = (const unsigned short*)len;
const unsigned short  msglen = ntohs(*lenptr);

char* msg = malloc(msglen);   // allocate a buffer of the proper size

recv(sd, msg, msglen, 0);   // now receive the entire message

...

free(msg);

```

---

### Post by asbuntu on 2009-06-21
If I recall correctly, no UDP packet can contain more than the MTU (Maximum Transmit Buffer) number of bytes.  That is typically a rather small value.  There are several articles I found in Google, but I did not go deep enough to get a hard answer.  I think a normal maximum is 1500, so my thinking would be to allocate 4096.

---

