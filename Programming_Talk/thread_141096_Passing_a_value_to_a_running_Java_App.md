---
title: "Passing a value to a running Java App"
date: 2006-03-07
forum: Programming Talk
---

### Post by hagen00 on 2006-03-07
Hi there

I want to access a java application but also pass it a parameter.

example. I've started the java app with

```
/usr/lib/j2sdk/bin/java myApp
```
but now want to call that same application and tell it to do something else based on the value i pass it. 

eg. 
```
/usr/lib/j2sdk/bin/java myApp parameter1
```

So based on what parameter1 is it needs to do something. Now obviously the above example **won't** work, since then i'll be starting a new instance of the java application. What i want to do is pass a value to the already running application. So basically, that application needs to listen for any parameters coming its way. 

Can this be done?

Many thanks

PS I've posted on the java forums, but the guys so far have given me the advice of using sockets, which i don't think is correct. I'll be passing the variables from the command line (a bash script) and don't think i can bind that to a socket. Even if i can...sounds like overkill. So i'm hoping the programming gurus here can help me out.

---

### Post by knalle on 2006-03-07
the jvm sandboxes the code so you cannot reach your app again without using one of the following;

1: static variable trick where class a1 and a2 communicates trough static variable(s) won't work on all jvms

2: socket listening, you can connect to a socket and listen to a port for arguments

3: Java RMI, see java.sun.com about RMI

---

### Post by sphinx on 2006-03-07
There is no real easier way of getting information in and out of an already running process than using some sort of networking. 

Except if you use the filesystem to communicate, but then your going to be polling a directory at some point and that just feels icky to me so I'll ignore this option. Also I have no idea what knalle is talking about with static variables communicating between jvms, If you could point me in the direction of more infomation on the subject knalle that would be good.

The simplest to understand conceptually is to use sockets as you have already been advised. RMI is a framework that uses sockets underneath. It takes care of some boilerplate code, however hagen00 you may want to look at sockets alone first to gain an understanding of them before tacking RMI unless, of course, you already do.

To me it sounds like you want a client-server application, one option would be to write a client java application that takes the parameter from the commandline like you example and just sends it to the running server in  a seperate jvm using sockets (or the RMI layer above that if you so choose) that does whatever it needs to do and returns whatever data it needs to back to the client jvm.

Personally (if you thought sockets were overkill... :) ) I'd write the server application as a Servlet and run it in an Servlet Container like Tomcat or Jetty, that way all the networking stuff is handled for you and you dont have to write the client. Use wget or some other commandline http client and script it to get the url of your servlet with the paramater in the url. Thats seems like less work for me but requires the learning curve for setting up a Servlet container, Servlet programming and some bash scripting to use wget.

All this is based on the assumption that you need a single server and can't have many run once processes as needed. It would be a hell of a lot simpler if you created an application that you started like your second example, did its thing and exited. That way you'd have none of the networking complexity that your looking to avoid.

---

### Post by LordHunter317 on 2006-03-07
[QUOTE=knalle]1: static variable trick where class a1 and a2 communicates trough static variable(s) won't work on all jvms[/quote]That won't work on any JVM.  I don't even know what trick you're talking about.

[quote=sphinx]Except if you use the filesystem to communicate, but then your going to be polling a directory at some point and that just feels icky to me so I'll ignore this option.[/quote]No, you could write the wrappers to use a FIFO socket or a pipe.  They may even already exist.

> RMI is a framework that uses sockets underneath.It's also useless for this.  I'm not sure why it was brought up.

RMI is a generic RPC mechanism, and a tool wrapped around it would likely be more complicated than the OP is dreaming of.

> To me it sounds like you want a client-server application,That's possible.  The other is an admin interface to a server or long running process, or other control mechanism.

Sockets are the eaisest solution.  Not saying they're the best, just the eaisest, in Java.

---

### Post by hagen00 on 2006-03-08
Thanks for the detailed replies guys. This really is a great forum!
> that you started like your second example, did its thing and exited.
Sure, that would definitely be easiest. The problem is that the server application running connects to an IRC server. I'm not sure i want to each time make a new connection to the IRC server. 

But if i understand the advice that was given to me correctly, maybe the best option is to 
1. Have my bash script start up the client java app, passing a parameter
2. client java app then communicates with server java app, passing the parameter via sockets. 
3. server java app does processing and client java app shuts down.

Right?

---

### Post by thumper on 2006-03-08
I'm not sure if it is something that you want to investigate, but JMX (Java Management Extensions) handles this type of thing.

However to get your mbean (managed bean - a JMX object) to run you need a JMX container.  I know that JBoss does, and I'm sure there are many more, but I haven't really touched Java for a couple of years so investigation might be in order.

---

### Post by knalle on 2006-03-08
[QUOTE=LordHunter317]That won't work on any JVM.  I don't even know what trick you're talking about.
[/QUOTE]

well you haven't been working with older pre jdk1.0.1 vms then

---

### Post by sphinx on 2006-03-08
[QUOTE=hagen00]Right?[/QUOTE]

Right.

---

### Post by mlind on 2006-03-08
what about JNDI?

awhile ago I was doing development using Joram JMS server and configuration
was done remotedly using admin module or JNDI binding. I'm not sure if it was
running as MBean, but it wasn't in servlet or j2ee container.

---

### Post by LordHunter317 on 2006-03-09
[QUOTE=knalle]well you haven't been working with older pre jdk1.0.1 vms then[/QUOTE]I have and it still won't work.  When you can explain to me how IPC can occur without the code explictly asking for it, or show a JVM that is intentionally running all the Java code in the same process space somehow, be my guest.

---

