---
title: "Server vs. Desktop"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by john.hall on 2008-06-25
I have chosen Ubuntu to be the distribution for a class project in which I have to set up a client-server environment with NFS, CUPS, etc.  

Is it necessary to install the server edition for the server machine, or can I just install the desktop edition for both machines and just install the necessary packages from apt?

---

### Post by John.Klockenkemper on 2008-06-25
You can just install the desktop edition for both and pull the packages using apt.

The server edition is stripped of a desktop and many other packages at the installation phase as it is intended for server use and servers typically do not have a gui. 

The desktop and server versions are relatively the same at the core.

---

### Post by sam_delta on 2008-06-25
ubuntu desktop = ubuntu server + GUI w/ some default applications

sam

---

### Post by bluepowder7 on 2008-06-25
to help you out, check out the "ubuntu server guide"

[http://doc.ubuntu.com/ubuntu/serverguide/C/](http://doc.ubuntu.com/ubuntu/serverguide/C/)

---

### Post by john.hall on 2008-06-26
Ok.  Thank you!

---

### Post by dominiquec on 2008-06-26
Primary difference is the kernel.  Server uses a kernel optimized for server workloads.  See [https://help.ubuntu.com/community/ServerFaq](https://help.ubuntu.com/community/ServerFaq)

My own experience, server kernel wouldn't boot on a Thinkpad as it required PAE.  Your mileage may vary.

---

