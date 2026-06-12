---
title: "C - Running a server program on the same box as a client?"
date: 2008-06-25
forum: Programming Talk
---

### Post by sshuber on 2008-06-25
Hi there!

I'm new to linux development, but I recently got a job that requires me to know network programming in C. I'm working my way through Unix Network Programming: Volume 1 by Stevens et all. In the book, they have many examples of code for both clients and servers. The server code uses infinite loops to listen on ports for  requests from the client programs. 

I currently only have one box with Linux installed (this one) and I don't have an extra box I can install it on to implement one running as a server and this one running as a client. I'm curious if it's possible in this situation to run both the server program and be able to run the client program at the same time, i.e. have the server executable running in the background and allowing me to run the other executable as well. I'm thinking it might be possible with threading or running some sort of virtual machine, but I'm clueless. I am currently running 8.04 Desktop x86.

I'm very green when it comes to Linux since all of my development up to this point has been in the Windows environment. If anyone can shed some light on this or point me in the right direction, I would appreciate it immensely.

Thanks!
-Scott

---

### Post by LaRoza on 2008-06-25
You can run the server and client on the same machine. You have to use the IP address 127.0.0.1

---

### Post by NormR2 on 2008-06-25
There might be security problems using port 80 (HTTP default) in which case parametize your code so you can use another port > 4096(??) while testing. 8080 is often used for testing servers.

---

### Post by sshuber on 2008-06-26
Great, thanks folks. After work today I'll give it a shot and see what happens. :)

---

