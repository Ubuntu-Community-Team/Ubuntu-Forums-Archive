---
title: "[SOLVED] Allowing TCP/IP connections"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by fredscripts on 2008-11-28
I just want to access a database I have on my machine from a java program on the same machine,

I've posted the question in Programming talk:

[http://ubuntuforums.org/showthread.php?t=995256](http://ubuntuforums.org/showthread.php?t=995256)


And the problem seems that isn't in the java code nor in postgresql.

It seems that I need to configure something of network stuff (where I am absolutely newbie) in order to get rid of this message when trying to connect to the database:


```
Connection Attempt failed
Connection refused. Check that the hostname and port are correct and that the
postmaster is accepting TCP/IP connections. 
```

How could I do it? (please I need it as I need to keep working on the java code, so I need to access the database for checking if I am doing it well).

Thanks!

---

### Post by taseedorf on 2008-11-28
Since this is the newbie forum, I will give you the easiest answer.

Install firestarter, which is a gui to iptables (ubuntu's built in firewall)

there are commands to use in shell, but i dont know them off hand

try either one of two things

disabling the firewall through firestarter while working on the code (not recommended)
OR
allowing connections to yourself from yourself
so, allow, 127.0.0.1 and whatever.your.local.ip to access your box........
see if that works.

---

### Post by skymera on 2008-11-28
I agree, Firestarter is an easy to use GUI for IPTables.

It will allow you to open ports to specific IP addresses and also view what's being blocked and when. 

Although UFW is installed by default which is a simplified CLI for IPTables.

---

### Post by fredscripts on 2008-11-28
> **taseedorf said:**
> Since this is the newbie forum, I will give you the easiest answer.

Install firestarter, which is a gui to iptables (ubuntu's built in firewall)

there are commands to use in shell, but i dont know them off hand

try either one of two things

disabling the firewall through firestarter while working on the code (not recommended)
OR
allowing connections to yourself from yourself
so, allow, 127.0.0.1 and whatever.your.local.ip to access your box........
see if that works.


Thanks so much for answering.

Sorry but I'm completely newbie on network stuff (firewalls, ports etc).

So could you please tell me the steps I must do in firestarter ?

I've installed it, select eth0 (cable connection), then after the wizard, I stopped the firewall. I got my database running, then tried to access to it by my java code, and still:

```
Connection Attempt failed
Connection refused. Check that the hostname and port are correct and that the postmaster is accepting TCP/IP connections.

```

Mainly what I need is to access to my localhost, with this adress on the java code:
```

String url = "jdbc:postgresql://localhost/postgres"; 
String user = "postgres";
String pwd = ""; //not sure what to put here, because i don't type any password to get the database running.
```


So how could I achieve this? Where's the option to "allow TCP/IP connections within this computuer? I mean I'm trying to access to a database of my own computer.

Thanks!

---

### Post by fredscripts on 2008-11-28
I had to edit the file postgresql.conf and set the tcpip_socket = true :)

---

