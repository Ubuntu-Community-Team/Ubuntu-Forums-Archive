---
title: "Java udp multicast socket"
date: 2012-05-18
forum: Programming Talk
---

### Post by zobayer1 on 2012-05-18
I have been trying to write a simple program using udp and multicast socket. The problem I am approaching is, given say, for example, 4 nodes, all of them will broadcast some message (not same) and at the same time, all of them will be able to capture them (coming from the other 3). Is it solvable using only one port? I have tried it, but the problem is, I am able to send the message (broadcast) to other nodes, but can't get two or more nodes to send message to another client.

Any help is welcome, just give me some idea how these type of things are done. What I did is, each of the nodes are identical, and the program consists of two parts, the main thread is sending messages, and another thread is listening to messages. I am sending messages with IP xxx.xxx.xxx.255 with a specific port address.

Another question is, is it possible to test broadcasting into my localhost, right now I don't have a LAN to use.

---

