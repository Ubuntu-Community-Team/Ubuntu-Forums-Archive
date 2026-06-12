---
title: "start localhost ubuntu"
date: 2013-05-14
forum: New to Ubuntu
---

### Post by sdmubun on 2013-05-14
I am using a VM with ubuntu on it and I need to connect with my browser to 127.0.0.1/server. I suppose it to be the localhost. Should I start any service to make it work? Now my browser cant establish a connection. Please help

---

### Post by TheFu on 2013-05-14
> **sdmubun said:**
> I am using a VM with ubuntu on it and I need to connect with my browser to 127.0.0.1/server. I suppose it to be the localhost. Should I start any service to make it work? Now my browser cant establish a connection. Please help

What is the "server"?   File, print, web, email, ssh, something else - there are thousands of choices, each would have a different client and a different server to start.  Samba, NFS, CUPS, apache, nginx, litehttp, postfix, exim, sendmail, openssh, .... you get the idea? Also, did you actually run a server and listen on 127.0.0.1 or one some other interface?  Some servers will listen on all interfaces by default, which can be useful so that other computers can access the service, but some only listen on the localhost interface. You need to know the port that whatever server you are using listens on. This can almost always be configured to any port you like, but there are default ports that are commonly used too.

The type of networking that you used for your VM matters too if you want a different computer (that means a different OS running either on physical hardware or inside a different VM) to access the "server."  Did you setup NAT or bridged or private networking?  Perhaps something else?

Lastly, if you are running a desktop inside the VM, did you try to run whatever browser is included and point the URL at localhost:80? Did that work?

---

### Post by sdmubun on 2013-05-15
webserver

---

### Post by TheFu on 2013-05-15
> **sdmubun said:**
> webserver

Which webserver?
What port?
Did you start it?  Usually something like **sudo service apache start** is needed.
Then you can point any web browser on your LAN directly at the non-127/8 IP for the server and see web pages.  **ifconfig** will show you the IP addresses on the box.

However, if you are running this for a web development purpose, like Django or Rails, many of those have specific web servers built-in that are used for development and may not listen on any IP other than 127.0.0.1 as part of their security setup.

---

### Post by sdmubun on 2013-05-16
I already solved it installing Apache but thank you anyway

---

