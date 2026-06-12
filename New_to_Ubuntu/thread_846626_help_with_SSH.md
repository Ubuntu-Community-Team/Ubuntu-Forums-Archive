---
title: "help with SSH"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by DFord425 on 2008-07-01
I move my computer running ubuntu to another room on a different router, same network. Now when i try to ssh into it and i keep getting connection timed out. Any ideas why i might not be able to connect to the computer.

---

### Post by Nxion on 2008-07-01
When you say same network, different router can you elaborate on that? 


Can you ping it at all? 

Are you sure it is pulling an IP address?

Thanks :)

---

### Post by whitethorn on 2008-07-01
Have you forwarded the port from the router to your computers ip?  Unless you changed the default port in the sshd_config file, then it's port 22.

---

### Post by DFord425 on 2008-07-01
Yes i can ping it, and i ran ifconfig on the computer to get the ipaddress. And the sshd daemon is running and listening on the port i specified.

---

### Post by DFord425 on 2008-07-01
> **whitethorn said:**
> Have you forwarded the port from the router to your computers ip?  Unless you changed the default port in the sshd_config file, then it's port 22.
I have my computer wired to a wireless bridge which is getting its signal from the router connected to the internet. The router connected to the internet is where the computer im trying to ssh into. Where do i set up the port fowarding, the bridge, the router, or both.

---

