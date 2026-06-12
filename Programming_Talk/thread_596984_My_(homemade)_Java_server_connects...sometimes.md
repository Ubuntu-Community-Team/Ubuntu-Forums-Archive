---
title: "My (homemade) Java server connects...sometimes"
date: 2007-10-30
forum: Programming Talk
---

### Post by r0b0h0b0 on 2007-10-30
Hi all

I posted this question in the general section but have had no replies as yet, so I'm trying here. Sorry for the cross-post.

New to Linux.

I've written a simple HTTP server in Java, which is called to life with a script at startup (not boot). It's listening on port 12999 for requests. It will serve up a requested page sometimes, but not always.

When I connect to my Java server from another machine, the browser will neither connect nor timeout...just sit there and think. When I check netstat on the linux box it tells me a the connection is ESTABLISHED on port 12999, but my micro server does not report a connection. This will happen about 8 times out of 10.???

If, however, I restart my server (close and re-open the Java application), it will work without fail - and not only can I connect to it from another box on the LAN, but also from the internet (I've set it up to do so).

I've not installed any firewalls, nor is the port being used by another process (as far as I can tell).

What gives? Why can I sometimes connect to it first time round, but sometimes not? Why does netstat report that the connection is established but my server doesn't report the connection? If the server isn't connected, but my browser doesn't complain (or timeout), what the heck is my browser connecting to?


**PS: Sorry for the re-post...I don't know what happened there!**

---

### Post by r0b0h0b0 on 2007-10-30
help? anyone?

---

### Post by tenmillionmilesaway on 2007-10-30
Does it work when you connect from localhost, if so you can probably assume that it is a network issue.  If it doesn't then you can probably assume that there is a bug in your code.

Richard

---

### Post by hecato on 2007-10-30
Thought I havent used java from some time, and cat see really the code, I will suguest a sniffer (wireshark for example, but I have installed it, and apparently doesn't work with wlan0, have pass some time that I have used it, but yu can search another one, and filer what is going in that port IIRC).

Also you only specify that you have wrote an http server, than mean from sockets?? or have you used a class that has already some http things?, also from "it run ok first time, later no" is most about your code, like perhaps you are not freeing a var, or you don't have enough thread for handle the request or some like that... or other thing related to the code.

Also the following is a contradiction from my point of view

[LIST]
[*]If, however, I restart my server ... it will work without fail ...
[*]Why can I sometimes connect to it first time round, but sometimes not?[/LIST]You have say that always first time connect, but later you reject it ;), or the "sometimes not" means after first connection I can't? and doesnt include the first successful connect.

---

### Post by AlexThomson_NZ on 2007-10-30
Some things I would probably try in your position are:
 * Adding some debugging code, so that is logs when a request is recieved, and when a send is sent
 * Simulating a browser on the client using telnet

Also, like Hecato asked- are you using existing libs, or your own using sockets?  I suspect there might be a logic bug in your code, where it may not be returning to a listening state (bit of a guess though without knowing more info).

---

### Post by dumbsnake on 2007-10-31
I'm actually developing my own HTTP server as well.  This will be the second time I've done it.  Both times I used C++, but I still have some perspective on the issue.  First, writing a webserver that is not buggy is not a trivial task.  Understanding threads and sockets really well is a must.  I'll assume you are in this category.

In order to debug your code, you really need to output information to the console or a log file.  Personally, I would output every time a new thread was made and every time a new socket was created or destroyed.  And every time an HTTP request was received or a response sent.

Honestly, no one here can help debug your code when you don't provide it.  If you want something a little less tricky (as evidenced by your choice of java as a language) you might try writing a CGI, SCGI or FastCGI program instead of a full blown HTTP server.   Goodluck.

---

### Post by r0b0h0b0 on 2007-10-31
@tenmillion:
yes, when I connect from localhost it connects every time without fail.

@hecato:
when I say I can "sometimes connect to it first time round, sometimes not" I imply that of all the times i try to connect to it for the first time (i.e., when my machine has booted up and the application has started), only a part of those attempts will have been successful. There seems not to be a pattern.

@dumbsnake:
My server is not referred to as a "micro" server for nuttin. The .jar file is 17.7kB in size, and that includes the code for the GUI as well as    the code for generating the default response and the code for fetching the requested .html page from disk - over and above the code required for handling socket connections and threading. It is nowhere near a full-fledged HTTP server! 

essentially, this is what I do:
```

//some code snippets

import java.net.ServerSocket;
import java.net.Socket;

...

ServerSocket serverSocket = new ServerSocket(12999);

...

while(someCondition) {
  try {
    Socket socket = serverSocket.accept();
    System.out.println("connected to " + socket.getInetAddress());
    //pass socket to handler and serve up stuff via
    //InputStream and OutputStream
  } catch (Exception someEx) {
    //handle someEx
  }
}

...

```

As you can see, simpler than that it cannot get. Whenever a connection on port 12999 is accepted, the first thing the app does is it reports that the connection is established, and it provides me with the (remote) IP address.

OK, here's another fly in the ointment:
When I run the application from NetBeans, it works **every time**. But when I run the application from a shell script, I get the weird results as described in my original post.

I am using Java 1.6, btw, and I'm not new to Java. I'm new to Linux ;)

---

### Post by dumbsnake on 2007-10-31
Well, it would seem that it is a network problem not related to your programming if it works correctly from localhost everytime, but this is really odd to me and actually somewhat inconsistent with your other statements.  The fact that you say that it always works with netbeans would imply that your program is the problem since that is all that varies there, but the fact that it always works with localhost indicates without a doubt that the network is the problem.

But, I have a pretty good guess what is wrong anyway....

So when a server binds to a port, it must also free the port later.  A program closing should in theory close the port, but frequently it doesn't always work this way.  I don't know the java code to solve this problem, but you ought to check that your server socker is binding correctly.  Likely, the browswer is connecting to the onclosed server socket that belongs to the process of your program that was already running.

I'm sorry I don't know the correct java to do that stuff and I might be wrong, but it is worth checking maybe?

The 2 solutions using POSIX sockets are to close the socket instead of just exiting the program and to tell the serversocket that it can reuse a socket when you bind it.

---

### Post by r0b0h0b0 on 2007-10-31
urgh. The silly thing is that the same application on my windoze server does not give me problems at all - it works as expected. I can assure you that the problem does not lie with the code (I've written many similar apps - and this one is particularly simple). I'm not saying Linux is at fault, I'm happy to assume that there is something (read: lots of things) I don't understand about Linux networking, and that there is what I want to solve.

My app does release the port when it is destroyed. It also binds correctly when it starts (hence the fact that I can connect locally), the problem arises when I connect from the LAN. Could it possibly (shot in the dark) be because the Linux box is a lone ranger on the Windows (TCP) network, and that the problem is somehow a result of a windows machine trying to connect to a linux box on a windows network? The fact that the problems seems somewhat erratic indicates to me that it is due to some ethereal fudge element.

---

