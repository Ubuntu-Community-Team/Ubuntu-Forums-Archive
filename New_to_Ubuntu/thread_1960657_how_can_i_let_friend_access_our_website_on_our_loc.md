---
title: "how can i let friend access our website on our localhost (lampp)?"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by hanzj on 2012-04-17
Hello,
We're currently designing a simple Wordpress.org website on our home computer. We have installed Lampp. How can we let our friend  remotely view what we have done so far.
Sharing our IP address didn't help, friend said.

---

### Post by abyrne on 2012-04-17
Your router probably isn't set up to forward ports. The instructions are different for all routers, so a quick Google search with your router's name and "port forwarding" should do the trick.

The important info is the port you want to forward (port 80) and your private IP (can be found by running "ifconfig". Probably looks something like "192.168.1.x"). After you set it all up just goto your [public IP]("http://www.whatismyip.com/") in any web browser

---

### Post by hanzj on 2012-04-17
Is there a quick (lazy) way to discover our router's identity without having to walk over to the living room, where the router is? Can we discover our router's identity on our Ubuntu comp?

---

### Post by abyrne on 2012-04-18
You could try running
```
netstat -nr
```
which should reveal your gateway address. You can just navigate to that address in your web browser. It might ask for a password, usually the username is "admin" "username" or just blank, and the password is usually "password" "admin" or just blank. Once you login, you should be able see some branding.

---

