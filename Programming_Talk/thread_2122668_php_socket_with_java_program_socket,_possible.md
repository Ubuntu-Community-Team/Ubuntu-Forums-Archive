---
title: "php socket with java program socket, possible?"
date: 2013-03-05
forum: Programming Talk
---

### Post by Xender1 on 2013-03-05
I am trying to connect my php server with a java program....the idea is that when a user hits a button it calls a php script, I would like this php script to in someway send data to a java program that I have running (currently both on localhost but eventually the php server will be hosted and just the java will be on my machine). The reason for this is because when the user pushes the button and the java program receives that, I need to send data over serial (usb) to my arduino. 

I have looked into php/JavaBridge, but it is having me install an apache tomcat server, wanting the java side to be a java servlet (is that what is required? i was thinking just a standard java program).....I feel like a simple socket might work and be easier?

---

### Post by r-senior on 2013-03-06
Sockets are sockets. You should be able to write a socket server program in Java and connect to it from your program. The first link below is pretty much exactly what you need:

[http://www.oracle.com/technetwork/java/socket-140484.html](http://www.oracle.com/technetwork/java/socket-140484.html)
[http://docs.oracle.com/javase/tutorial/networking/sockets/index.html](http://docs.oracle.com/javase/tutorial/networking/sockets/index.html)

You don't need servlets and a servlet container like Tomcat to do this. It might make sense if you had a more extensive web service but I don't think it does in this case.

---

### Post by spjackson on 2013-03-06
> **Xender1 said:**
> eventually the php server will be hosted and just the java will be on my machine
I think that before making your decision you should investigate what is permitted by your intended hosting environment. Otherwise you may end up producing something that works locally where you have full configuration control, but falls foul of a firewall or other configuration that you cannot control. If I was in your situation, I'd be thinking along the following lines.

Can I reasonably expect my hosting solution to permit a call out to a remote web service? Yes. Can I readily test this? Yes. If not, would a redirect of the client browser be just as effective? Can I reasonably expect to connect to an arbitrary socket? Probably not. How easily can I test that? etc.

Technically, as r-senior says, sockets are sockets. However, I think that in a hosted context there's more to consider, as above.

---

