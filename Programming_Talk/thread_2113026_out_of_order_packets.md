---
title: "out of order packets"
date: 2013-02-06
forum: Programming Talk
---

### Post by bryanevil on 2013-02-06
How to ensure my udp sockets receive all packets in order? Assuming the packets are guarantee arrive in order at the receiver machine, and no packet drop. 

I am asking this because I ran my program many times in window, and redhat. It always receive in-order packets under windows, on the other hand, out-of-order packet always happen under redhat as well as ubuntu.

  I am using boost asio library to create 50 udp sockets, receive rate set to 100 packet/sec.  I also have tried without boost asio, and use a boost thread to listen to an epoll, and call recv to fd immediately, but yielded the same result. In addition, If I only open 8 sockets in linux, i receive no out-of-order packets.

---

### Post by dwhitney67 on 2013-02-06
You are lucky to receive the packets!  UDP does not guarantee the delivery of packets, and you can almost bet that there's no guarantee that they are delivered in any particular order.

You may want to read the information on this page:  [http://en.wikipedia.org/wiki/User_Datagram_Protocol](http://en.wikipedia.org/wiki/User_Datagram_Protocol)

Pay careful attention to the 2nd paragraph.

---

### Post by bryanevil on 2013-02-06
> **dwhitney67 said:**
> You are lucky to receive the packets!  UDP does not guarantee the delivery of packets, and you can almost bet that there's no guarantee that they are delivered in any particular order.

You may want to read the information on this page:  [http://en.wikipedia.org/wiki/User_Datagram_Protocol](http://en.wikipedia.org/wiki/User_Datagram_Protocol)

Pay careful attention to the 2nd paragraph.

But how would you explain, under the same network setup in windows environment, it did not had a single drop, or out-of-order packet?

---

### Post by dwhitney67 on 2013-02-06
> **bryanevil said:**
> But how would you explain, under the same network setup in windows environment, it did not had a single drop, or out-of-order packet?

It could be luck, or perhaps the depth of the queues employed by the socket, or perhaps the LAN, or perhaps because today is Wednesday.  I really don't know.

If you want guaranteed delivery and ordering, use TCP... not UDP.

---

### Post by The Cog on 2013-02-06
Also the 3rd paragraph.

With UDP, packets might be re-ordered, lost or duplicated. If you want guarantees on any of these, you are probably better off using TCP instead. 

However, if you insist on using UDP, you could arrange to give every sent packet a sequence number. You should arrange for the reciever to be able to request retransmissions of lost packets, to be able to ignore duplicate packets, and to re-order out-of-order packets. TCP does all this and more for you though.

---

