---
title: "C# client server chat UDP protocol ,,, how to specify port number ??"
date: 2011-12-17
forum: Programming Talk
---

### Post by Qutaibah on 2011-12-17
hi I built on C# visual studio client / server chat program using UDP ,and run on server by using mono platform , 


[B]-I want to determine port number for client
[/B]how can I open port as example (port 4000) between server and client

I am using ubuntu server 11:10 64 bit

and the clients ubuntu desktop and windows xp

---

### Post by Qutaibah on 2011-12-17
between client and server

---

### Post by directhex on 2011-12-17
Er... depends on your code, surely? If you're using System.Net.Sockets.UdpClient, it takes the port number as an argument

---

### Post by lisati on 2011-12-18
*Thread moved to **Programming Talk**.*
Not exactly a task for absolute beginners, more a programming question.

---

