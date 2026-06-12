---
title: "Edit linux configuration in c++"
date: 2010-09-20
forum: Programming Talk
---

### Post by kacper on 2010-09-20
I'm thinking of building a web front-end for my linux firewall with a c++ backend. Is there a library or something that will let me write to linux configuration files without messing with user defined config?

---

### Post by nvteighen on 2010-09-21
> **kacper said:**
> I'm thinking of building a web front-end for my linux firewall with a c++ backend. Is there a library or something that will let me write to linux configuration files without messing with user defined config?

In GNU/Linux each program has its own configuration scheme. Anyway, in general, user configuration is stored in the user's home directory while system-wide configuration is stored under /etc, so keeping with that convention would do it.

But... if you're writing a front-end for iptables/netfilter, then you'll only have system-wide configuration, as only root is able to modify the firewall's behaivor (unless you tweaked permissions on your system...). See iptables's man page for information on the relevant configuration files.

---

### Post by kacper on 2010-09-21
> **nvteighen said:**
> But... if you're writing a front-end for iptables/netfilter, then you'll only have system-wide configuration, as only root is able to modify the firewall's behaivor (unless you tweaked permissions on your system...). See iptables's man page for information on the relevant configuration files.

This is way I choose c++ as a backend that will have root access and let the web front-end talk to the c++ backend.

---

### Post by dwhitney67 on 2010-09-21
Any application, regardless of the programming language it is written in, can be invoked using root-privileges.

Is C++ really the best choice for the application you want to develop?  The answer is probably "no".  But don't let this deter you.

As for your application, I would suggest that you get the back-end working first before you spend too much time on the front-end.

---

### Post by kacper on 2010-09-22
> **dwhitney67 said:**
> Any application, regardless of the programming language it is written in, can be invoked using root-privileges.
I was referring more to the option of letting say PHP have root, which is not such a good idea.

> Is C++ really the best choice for the application you want to develop? The answer is probably "no". But don't let this deter you.
If c++ is not the best option what you you recommend?

---

### Post by kacper on 2010-09-26
The easiest way would be to run say lighttpd with php as root, but from a security standpoint it's not that good. How do other firewalls expose their web interface?

Either way I look at it I need a web server for the backend exposed as root. :(

---

