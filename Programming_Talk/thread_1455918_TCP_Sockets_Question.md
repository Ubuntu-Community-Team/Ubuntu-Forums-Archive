---
title: "TCP Sockets Question"
date: 2010-04-16
forum: Programming Talk
---

### Post by rchan0021 on 2010-04-16
What is a TCP control connection, and TCP data connection? I thought that sockets could send and receive data on a single connection.


Thanks in advance.

---

### Post by soltanis on 2010-04-16
There isn't any distinction that is formally defined between the two, so I'll have to ask what context you're using this in. All TCP connections are stream-type, stateful connections between two endpoints over Internet Protocol packets. All TCP streams carry "data", in the sense that they carry information.

Some protocols, like RTSP, use multiple connections to differentiate certain commands (such as play, rewind, stop, to control a media stream) from data (the media stream) which is transmitted separately. So for example, RTSP can use a TCP connection to control the media stream while RTP, a UDP-based protocol, transmits the stream itself.

And you're correct, almost all sockets you would create with the socket(2) call can both send and receive, unless you use shutdown(2) to close one part of the connection.

---

### Post by The Cog on 2010-04-16
Spot on.

I think that FTP was the first protocol that had separate control and data connections. The control connections carry the commands to transfer files, and the data connections then carry the file contents (one connection per file).

---

### Post by soltanis on 2010-04-16
This property is also what makes FTP an insecure protocol (ever heard of the nmap FTP bounce scan?).

---

