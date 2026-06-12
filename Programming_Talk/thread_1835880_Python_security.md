---
title: "Python security"
date: 2011-08-30
forum: Programming Talk
---

### Post by newelfik on 2011-08-30
Hi everyone,

I'm developing a screensaver under ubuntu.
This is an dynamic screensaver which done some actions on the system in background.

So i would like to restrict right to some users, so done an access politic to the screensaver.

I have a server and some client in Python, communication in TCP/Socket. the client listen gnome-screensaver dbus. 

So I would like to secure the communication and authentication.
As it is a screensaver, there is no way to login/password authentication.

Have you got any idea ? 

For the moment, I get back username in client module and send it to server with a config file for the rights, but python is not a compiled language, so... users can modify source code.

---

### Post by Smart Viking on 2011-08-30
I don't really understand your problem, but if you store the file under /usr/bin with the right permissions, then normal users cannot change the source code.

Maybe you could create a group for your program to fix some other security issues, but I don't know so much about that.

---

### Post by newelfik on 2011-08-30
hmm, you right. But is it enough for a security ?

I think there is a better way to secure communication. For the moment i am only send the result of 'whoami' in a socket. 

I'm looking for a folder, one file by user getting right access. And set up some config access.

---

### Post by Smart Viking on 2011-08-30
There's different kinds of security.

If something secret travels over the network, then it would be smart to encrypt it. But I know very little about network programming.

---

### Post by newelfik on 2011-08-30
I need only send START/STOP for screensaver status , and the username. So if there is no way to a user to pretending to be someone else. it's seems to be good.

I am looking for that.

---

### Post by StephenF on 2011-08-30
[http://atlee.ca/software/pam/](http://atlee.ca/software/pam/)

---

