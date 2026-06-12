---
title: "Doubts about sockets and timeouts"
date: 2016-02-08
forum: Programming Talk
---

### Post by mfvpcrec on 2016-02-08
Hello everyone I have a question about sockets and connections and all this stuff :) I have a server and a client (that were written in python), 
the client send a message "I still alive" in X time and some messages randomly and, in the other side, in the server, I have a recv, that receive
all that information with a timeout larger than the time that I send the message of " I still alive".
WITHOUT UNDERSTANDABLE reason after send MANY messages  I have in the server a  randomly "time out exception" :confused: . Well I deactivate the
Nagle's Algorithm because the messages are small and I don't wanna wait for anything, but the exceptions still happen.
Ok  if I can't avoid that problem about time outs I decided resend the message that was not received but this produce me a few questions

Where are the messages that were not received?
I can get repeated message because timeouts ? ( I think if but just wondering )
Why timeouts occur if I send correctly and timely message?

Bye!

---

