---
title: "Design for connection of GUI - Application with sockets"
date: 2013-07-09
forum: Programming Talk
---

### Post by Pithikos on 2013-07-09
I have an application in python which is supposed to use a webpage as its GUI.

The application is working continuously and outputting its data to the webpage via sockets(websockets). Data from the GUI to the application is seldom, but once it happens I want everything to get blocked in the application to examine what it received(it could have received a pause message).

What is a good design for this?
Should I use a queue for outgoing messages and a queue for incoming? Do I need to use threads? Does blocking - unblocking connection calls matter?

---

