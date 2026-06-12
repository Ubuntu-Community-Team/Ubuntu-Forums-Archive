---
title: "Nagios"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Nxion on 2008-04-28
Any one here have any experence in setting up Nagios2 to monitor hosts ?

I installed it and made a hosts file but I cant get it to work. All it says in the status windows is "PENDING" I cant get it to see my clients. 

Am I missing some thing ?

My machine is running 8.04

---

### Post by Nxion on 2008-04-29
No one ?

---

### Post by juan@forum on 2008-04-29
try to monitor your own machine...

PENDING means that a check has been configured to be performed but it it not yet...

when you click that service it should say Next Check, what does it says?

---

### Post by Nxion on 2008-05-01
I realized what I did. I forgot to define the services nagios looks for. I fixed it. All is good. Thanks.

---

### Post by t8sht3r on 2008-05-13
I was trying to install nagios tonight using the apt-get command, is there not a package for Ubuntu that I can use apt-get for?  All I can find when searching is "download the latest tarball", etc. I want to use the package manager if possible.

---

