---
title: "UDP DatagramPacket DatagramSocket send() receive() drop or buffer?"
date: 2010-05-05
forum: Programming Talk
---

### Post by raequin on 2010-05-05
I am working on an application that communicates with a piece of software (image processing) that only provides UDP. Hence I am using Datagrams. Here's my simple question. For

DatagramSocket.send(DatagramPacket),

what happens to the information if the application on the other end of this message is not calling

DatagramSocket.receive(DatagramPacket)?

I ask because I do not want to use every packet sent by the image processing software. For example, I trigger the processing, causing it to send a DatagramPacket, but I am not interested in that information so I do not call receive(). Then, I trigger it once more, and this time I want the info in the sent DatagramPacket, so I do call receive(). I am wondering if there is a buffer or something holding the first DatagramPacket, because I want to be sure that receive() gets the second set of information and not the first. Hopefully that's a clear enough description. Thanks for reading, please let me know any info you have on this.

---

### Post by psusi on 2010-05-05
Datagram sockets do not know or care if someone is on the other end to receive the packet.

---

### Post by soltanis on 2010-05-05
If your application has bound a UDP listener on the other end to that port (using the bind() call) then the OS will queue the packet up for the application, so that the next time the application calls recv(), it will be popped from the OS buffer. So you don't technically have to be reading while sending (just have the program set up for receiving, if you see the difference).

UDP packets are of course not guaranteed to arrive in order or at all. Over local networks, they tend to work though (unless network conditions are REALLY bad). Over the Internet, you're taking more chances although packet loss is a much smaller problem nowadays than most guides suggest. Don't be cavalier and assume your stuff will be well-ordered and guaranteed to arrive; just don't assume that 50% of your data is going down the drain and the other 50% is going to arrive in reverse order.

---

