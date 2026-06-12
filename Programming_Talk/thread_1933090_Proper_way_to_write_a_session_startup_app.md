---
title: "Proper way to write a session startup app"
date: 2012-02-28
forum: Programming Talk
---

### Post by PeterTaps on 2012-02-28
Folks,

I am developing a Java based application that acts as a server and, based on client requests, it can spawn GUI applications such as VLC. The idea is to control some features of VLC and other GUI applications remotely.

The way it works today is that the user starts the application manually from a terminal window:

$ java -jar /home/peter/MyServer.jar

The application starts listening on a socket. It also waits for terminal input. If the user enters "quit" from the terminal, the application quits.

This works as expected. From a remote client application, I am able to spawn VLC and other GUI applications as needed.

Now, I would like to run this application automatically when the user session starts.  I tried adding the following command from "Startup Applications" GUI

java -jar /home/peter/MyServer.jar > /home/peter/myout.txt 2>&1

However, this does not fire up at all. 

Is there any log file that I can look at to see why this doesn't work?


I would appreciate it if you could share your thoughts on what is the right way to write such application. I am guessing waiting for "quit" from console is probably not a good idea.

Regards,
Peter

---

### Post by PeterTaps on 2012-02-28
Ok. After doing some research, here is what I found out.

1. You need to close all the standard I/O descriptors:

System.out.close();
System.err.close();
System.in.close();

2. In the "Startup Applications GUI," add "&" at the end of the command.

java -jar /home/peter/MyServer.jar &

3. You also need to implement some logic to keep the main thread alive until the user requests to quit. In my case, I was accepting input on the socket so that the user can send various requests. The main thread just does a wait() for the socket to notify().

Hope others find this useful.

Regards,
Peter

---

