---
title: "TCP problem send large messages"
date: 2015-02-04
forum: Programming Talk
---

### Post by mfvpcrec on 2015-02-04
Hi guys , i write this message for a doubt, a time ago i wrote a client/server program with TCP/IP in Linux. When i tested the program flooding the server with messages of 1024 bytes (Or 1025 bytes i dont remember exactly the number but was more that 1000 bytes) in certain point a message was received truncated blocking the program because the while(recv) never completed the 1024 characters count. I avoided this problem making  the messages more shorter (i don't remember  200 bytes i guess) but i know that is not ok. Now i must develop a very strong connection (avoiding so much as posible the lost of messages) and i need understand why this happened and how avoid this problem. Maybe the net was oversaturated in that moment when i tested my program and a part of the message was lost but this is not a excuse. My question is ¿There is some protocol that avoid the lost packages (i know that tcp does the best effort for send the message but  i saw how a message or part of it came truncated more than once) or either very strong  or I must develop a protocol for this?

I read about Reno TCP and TCP Vega but really i dont know how use it.

Thank you very much

---

### Post by dwhitney67 on 2015-02-05
When dealing with TCP, the message delivery is guaranteed.  However if you are developing s/w to receive messages, you need to be aware of the fact that the message(s) that are sent are not always delivered 'whole'... it is quite possible that large messages are packetized into smaller chunks.

Your s/w will need to account for this packetization, either by reading in a fixed-number of bytes, or by employing some other strategy such as prefacing your message with a header that includes the length of the data portion of the message.

Good s/w will employ a strategy of ensuring that large messages are both sent and received in their entirety.  Don't assume the a single call to send() will transmit the entire message, and do not assume than a single call to recv() will receive the entire message.

Here's a link to [Beej's Guide to Network Programming]("http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html") that you should reference in your s/w development endeavor.

---

