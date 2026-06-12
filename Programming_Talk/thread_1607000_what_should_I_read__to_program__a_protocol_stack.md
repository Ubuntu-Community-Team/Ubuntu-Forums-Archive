---
title: "what should I read  to program  a protocol stack"
date: 2010-10-27
forum: Programming Talk
---

### Post by jamesbon on 2010-10-27
Hi,
in past 2 weeks I have been putting efforts to learn network programming which I have learned at least making basic client server programs.(You can see my posts on this forum) I was searching on internet as for network programming what is the thing which is needed in companies or from a job if I want to take in network programming related areas then what should I learn more.
I came across a link
[http://www.netdiox.com/NetdioxSyllabus.html](http://www.netdiox.com/NetdioxSyllabus.html)
and a heading on this link Networking,TCP/IP internals Protocol stacks drew my attention.I do not have expensive hardware with me only thing I have is a laptop and I can create virtual machines on my laptop.
So please tell me what should I be able to develop and handle.I am a total newbie in this area.Some one suggested me to get myself involved in a project and start doing things that way I will be able to learn what I want to.If some one can suggest me some thing even on that part that will do.
[B][COLOR=#000000]
[/COLOR][COLOR=#000000][/COLOR][/B]

---

### Post by dwhitney67 on 2010-10-27
Here's a brief description of [Protocol Stack]("http://en.wikipedia.org/wiki/Protocol_stack").

Most of the companies I have worked with in which TCP or UDP was employed to transfer data, did not spend too much (if any) time worrying about the details of how things work wrt the protocol stack.

For most jobs that require knowledge of how to implement client/server applications, knowledge of the details of the Protocol stack are unnecessary.  This is not to say that one should avoid learning about the protocol layers, but intimate knowledge is not necessary.


Here are some (silly) questions that one may be asked during a job interview...

What steps are necessary to set up a TCP server (socket) so that client applications can connect?

Does one need to open two sockets to perform bi-directional communication between a server and a client?

What is the difference between TCP and UDP?

When attempting to connect to a server, a "connection refused" response is received; what does this mean?

UDP is known as a connectionless protocol; yet some applications call connect() for their socket.  Why?

What is the range of ports that can be opened by a regular user? By the super-user?

What is an ephemeris port?

I have a structure that is chock full of data that I want to send via a socket; what is the first thing I need to do before I can send this data?  Once the data is received by the recipient, what then?

What is the difference between Big and Little Endian?


If you can answer these questions, then IMHO, you know enough.

---

### Post by jamesbon on 2010-10-27
Hmm  Ok thanks for your reply.Most of the job interviews I appeared I failed worst part is I did not got much interview calls.I recently graduated.
I came across some one by chance never met him again they told they work for protocol stack on Xen(with Citrix R&D) now that was some thing that fascinated me I wish if I could do some similar things.I want to put some thing **solid** in my resume which is hard for any one to ignore.
I will go to any extent to develop if you suggest some thing to do.

---

