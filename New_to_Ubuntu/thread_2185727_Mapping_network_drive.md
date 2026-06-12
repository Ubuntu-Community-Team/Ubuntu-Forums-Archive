---
title: "Mapping network drive"
date: 2013-11-04
forum: New to Ubuntu
---

### Post by quarkhirad on 2013-11-04
At my work place i need to connect to a windows share folder. In windows i just opened my computer then map network drive and then typed \\ccgg1\cag1 and clicked finish. It then prompted me for a username password and tadda i was connected to the network drive. How do i connect to this network drive in ubuntu. I am running 13.10.

Thanks 

khirad

---

### Post by TheFu on 2013-11-06
Open Nautilus, type  smb://ccgg1/cag1  into the address bar. 
As long as your DNS is working to find ccgg1 (the server), that should be it.

There is also a "Network Drives" option in my file manager - browse to the share and mount it.

Of course, if your MS-Windows is running an AD domain, with kerberos, then things are more complex.  Try the above first.

---

### Post by quarkhirad on 2013-11-07
> **TheFu said:**
> Open Nautilus, type  smb://ccgg1/cag1  into the address bar. 
As long as your DNS is working to find ccgg1 (the server), that should be it. 

Thats it. You hit the nail on the head. Thanks

---

### Post by TheFu on 2013-11-07
> **quarkhirad said:**
> Thats it. You hit the nail on the head. Thanks

This works for 1 user.  "smb" is the protocol, others are supported too.
If you want the remote file system available without logging in ... ask.

---

### Post by quarkhirad on 2013-11-07
> **TheFu said:**
> This works for 1 user.  "smb" is the protocol, others are supported too.
If you want the remote file system available without logging in ... ask.

Yeah please tell me

---

