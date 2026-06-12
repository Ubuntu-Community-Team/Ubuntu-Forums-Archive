---
title: "Multiplayer Game"
date: 2009-07-05
forum: Programming Talk
---

### Post by nebu on 2009-07-05
I am trying to write a multi-player tictactoe game in c++....

I have managed to get around the ui with gtk but the networking is turning out to be a bit of a worry.....

I am kind of new to socket programming and id like to know how one go about the problem of multi-player gaming..... 

one of the things that i cant understand how to do is.... how do i know which computers on the local network are running my game client given that the software is using a certain port..... something like one searches for online servers in a game like counter strike or cube etc...

any help will be really appreciated...

---

### Post by nebu on 2009-07-06
bump...

---

### Post by dwhitney67 on 2009-07-06
You did not indicate in your post of you were using UDP or TCP, thus I will assume the latter.

When using TCP the server application needs to bind it's socket, set up a listen backlog, and then accept client connections.

The server will bind its socket using a combination of either the interface's IP address and port number, or just the port number across all interfaces (INADDR_ANY).  It would seem to me that you want to use the IP address of the system on which the server is running (of course, along with the port number too).

The client that connects to this server will need to know the interface IP address and port number.  If you are running the server on multiple machines, then it makes sense that the client will have a list of IP address from which to try to make this connection.  If one fails, then it will move on to the next (to try it).

Based on the simplicity of Tic-Tac-Toe, I would recommend that you use UDP.  Once again, though, the client that initiates contact with the server will need to know the server's IP address and port number.

If you have any specific questions, just let me know.

P.S.  In lieu of using hard-coded IP addresses, the majority of server sites have IP addresses that are registered through a Domain Name Registrar; thus the need to know the IP becomes moot... all one needs to know is the HTTP web-address.

---

