---
title: "Socket Programming with PHP"
date: 2011-09-28
forum: Programming Talk
---

### Post by dazman19 on 2011-09-28
Hi,

I have written a program with PHP which opens a socket, writes data to it, then reads the response from the socket, then ends. The program works great , except in some instances the application running on the socket needs a few questions answered by the user.

This is running on an apache webserver, and when the request finishes processing I need to close the socket. 

But I actually need to return a few things to the user to ask them questions and send their response back to the same socket.

I am thinking about writing a CGI application in either C++ or Java (since they are the other languages I know how to use) and posting it an opensocket command with an identifer, then posting it data, reading the responses from the CGI app and sending them back to the user. Then when i am done I will post it a closesocket and ID. 

1) do you think this is a good solution? or shall i stick to php since the entire app is already in php, if so how am i easily going to do this?

2) I am thinking about using java because this would be nice to compile on both windows and linux machines. If i use java are there librarys for it so i can easily read HTTP REQUEST headers?

---

