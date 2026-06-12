---
title: "UDP and Zero bytes packets"
date: 2010-05-07
forum: Programming Talk
---

### Post by FaresH on 2010-05-07
Hi,

I have a server and client, they are connected by non-blocking sockets. And I am using the connect() method. 

The server sends the content of a file to the client and the client sends it to the stdout file. Immediatly after the transfer is done, both sides start to receive zero bytes packets. I mean it never stops. And none of the sides crashes. I am out of ideas, the communication works fine.

The switch between the user input, the recv function and the send function is made by a select and FD_ISSET.

Any ideas as to what might be the problem ? Any idea is welcomed.

---

### Post by dwhitney67 on 2010-05-07
> **FaresH said:**
> 
Any ideas as to what might be the problem ? Any idea is welcomed.

Without seeing your code, I would have to guess that the code has a bug in it.  :-)

From the description you provided, I would guess that the following is meant to transpire:

1.  The client sends the server a request containing the name of a file to upload.

2.  The server receives the request, and then proceeds to send the entire contents of the file via individual packets that contain chunks of the data from the file, and possibly also information about where the chunk originated from within the file, and the chunk size (optional).

3.  The client receives each packet, and writes them to a file (or stdout) on it's end.

4.  After the server has sent the entire file, it then proceeds to send a packet to the client that the data transfer is complete.

5.  The client receives the final packet and then realizes it is done with it's task of receiving data, and then exits.

Now, as for using UDP, this will probably work on a small local area network, but for larger networks, this is probably not the best protocol to be using for transferring file data.  Your packets could be dropped (ie lost), or arrive in a different order in which they were sent, or even arrive two or more times (ie packet duplication).

To mitigate any errors, I would suggest that the server send additional information with each packet, for example the data location and it's size.  Something like:
```

#pragma pack(1)

struct Packet
{
   int            seqNum;
   size_t         dataOffset;
   size_t         dataSize;
   unsigned char* data;
};

#pragma pack(0)

```
As for dealing with missing packets, I don't know how to counter this issue other than having the client request that a specific packet, if it deems one is missing, be sent again by the server.


A final note... When using UDP, a client typically does not connect to the server unless it plans to send lots of data.  From the description you provided in the OP, it seems that the client is the one that is receiving lots of data, not sending it.  Thus a connection is probably not necessary.  Note that the client will not be aware of the server's socket status until it attempts to send data.

Anyhow, consider using TCP for your needs.

---

### Post by The Cog on 2010-05-07
I agree with dwhitney67 that without extra checking, UDP is not suitable for file transfer, and for the reasons he states. If you really want to use UDP, look at the specs for TFTP protocol - this might help understand what's needed.

As for your immediate bug, I guess you have a problem reading the input stream in that you don't recognise when the input stream is finished/closed, and you are constantly reading 0 bytes from the closed input stream. I can't remember how you detect end of stream - maybe you have to check the error status if you ever get a 0-length read result?

---

### Post by FaresH on 2010-05-08
I have a library that tracks down missing packets. 
But my question is why is both udp sockets sending zero bytes messages to the other side. I checked my code, the program after sending the entire file never reaches the function that uses send(). So if this part is never reached, who is sending the zero bytes messages ?

---

### Post by dwhitney67 on 2010-05-08
For all I know, it could be your next door neighbour who is sending the "funny" packets.

Without the privilege of seeing your code, there is nothing for me to comment on.

I could show you how to transfer a file from A to B, but then that would take away my time from enjoying a beautiful sunny Saturday.

---

