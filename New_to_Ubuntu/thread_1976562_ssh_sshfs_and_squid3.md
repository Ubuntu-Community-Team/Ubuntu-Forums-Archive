---
title: "ssh sshfs and squid3"
date: 2012-05-08
forum: New to Ubuntu
---

### Post by lance bermudez on 2012-05-08
how do I use squid3 to cash ssh and sshfs to be used over home network. In other words how to i use ssh and sshfs over squid3 proxy at home

---

### Post by Ms. Daisy on 2012-05-10
When you ssh inside of your LAN you're not ever leaving the network,  you're not going out onto the internet and back into the LAN.  So why on earth would you want a proxy for that?

---

### Post by lance bermudez on 2012-05-10
good question let me explain more I need to speed up movie watching have server in other room away form tv. have old labtop connected to tv with linux on it with sshfs to connnect to server with movies. 

I know that for filefox you can creat a ssh tunnel to quid. I know you can ssh'd onto the server with movies to forwarding port 8080.
eg: ssh -L 8080:localhost:3128 user@hostname
this forwards all port 8080, thru my sqid proxy. 
then configured firefox to use localhost:8080 for all its protocols.

this is what i was looking to do with sshfs throw the squid proxy. you kow a better way please tell me.

---

