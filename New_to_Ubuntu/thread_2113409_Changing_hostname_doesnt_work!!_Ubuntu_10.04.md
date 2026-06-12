---
title: "Changing hostname doesnt work!! Ubuntu 10.04"
date: 2013-02-07
forum: New to Ubuntu
---

### Post by Drigo on 2013-02-07
So I have two machines in the network. Lets say one called ubuntu and the other is suppose to be called ubuntu2.
I reformatted the second machine and accidentally gave it ubuntu as the hostname during installation.

After following some threads I changed the values in /etc/hosts and /etc/hostnames.

After reboot, I checked the hostname and it output ubuntu2, which is the correct hostname . 

!!However, when I try to ssh from a different computer I can't connect to ubuntu2. Though, I can connect to it using ubuntu as the hostname, which eliminated the original ubuntu computer.

Any other place where I need to change it?

---

### Post by TheFu on 2013-02-07
Reboot shouldn't be necessary.
* change the name in all /etc/hosts - other machines too.
* change the name in /etc/hostname  (not plural)
* run **sudo  hostname ubuntu2** on the machine
That should be it unless you are running a DNS server or using Windows as a client which tends to cache hostnames and IPs longer.

Network connections do not care what the name of the host is to itself unless you have specific ssh_config  and sshd_config settings which mandate it.  Another machine can call any remote machine ANYTHING THEY WANT.  I use this all the time.  Any machine can have thousands of network aliases.

---

### Post by Warren Hill on 2013-02-07
There is a video here

[http://www.youtube.com/watch?v=Mlfao1yigw8](http://www.youtube.com/watch?v=Mlfao1yigw8)

Have you done all these steps?

If yes then maybe the problem is the dns server on the other machine.  You may need to clear the DNS cache

---

### Post by Drigo on 2013-02-08
Well...I am just reinstalling the OS. Now the previous ubuntu machine hostname doesnt work. When i do nslookup (in any computer or itself I get)....

$nslookup ubuntu
Server:		127.0.0.1
Address:	127.0.0.1#53

** server can't find ubuntu: SERVFAIL
'
How can I fix this? It looks like somehow the mistaken installation of ubuntu2 with ubuntu, overwrote the dns and now the older ubuntu doesn't work unless I connect through the ip. How can I fix this?

---

### Post by Drigo on 2013-02-08
I guess this will be more helpful...

$drigo@ubuntu:~$ nslookup 10.50.4.5

Server:		127.0.0.1
Address:	127.0.0.1#53

5.4.50.10.in-addr.arpa	name = ubuntu.<somedomain>





$drigo@ubuntu:~$ nslookup ubuntu.<somedomain>

Server:		127.0.0.1
Address:	127.0.0.1#53

** server can't find ubuntu: SERVFAIL

---

