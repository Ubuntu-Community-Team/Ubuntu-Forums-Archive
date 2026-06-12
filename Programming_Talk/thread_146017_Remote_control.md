---
title: "Remote control"
date: 2006-03-17
forum: Programming Talk
---

### Post by Jaristr on 2006-03-17
Hi, 
I'm interested in learning how to code a program that can be remotely controlled by first logging in to it and then typing commands. I actualy know how to program something like this but I want to learn how to program it right, so that it's secure and all. I assume ssh server-client is a good example of a working solution. 
So I would appreciate if some one could point me to right direction on this and talk about this topic. 

Thanks.

Jari.

---

### Post by Burke on 2006-03-19
Hi, I know if you're running a telnet server, you can change something in inetd.conf so that you have a custom login program. You have to specify an option (-l or something) for telnet with a path to the program. I had something like this for a while, it was a chuck nirris fact generator over telnet. What happened was the client init'ed a connection to my computer (telnet server)m, then telnetd started the login program for the remote connection. My program simply printed a 'fact', then called exit(255) to terminate the connection.

This would be the way to go for a remote connection deal, except that telnet isn't secure. I'm not sure whether you can do the same thing with ssh, but it's worth a look. Try Googling for "ssh login program inetd" or something.

Best of luck!

---

