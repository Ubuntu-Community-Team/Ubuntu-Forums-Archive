---
title: "SSH Connection Lost / Refused"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by julio8a00 on 2012-05-23
Hello,

I found a tutorial online on setting up Opensshd-server.
everything works fine when I try ssh user@localhost

but when I try to connect though another computer on the network it gives me:

Connection Lost
pool-my-ip-address.plspca.dsl-w.verizon.net/my.ip.address:22 - Connection Refused

i also tried different ports which I have forwarded on my router but it doesn't connect. I would really appreciate some help

thanks in advance

---

### Post by sandyd on 2012-05-23
> **julio8a00 said:**
> Hello,

I found a tutorial online on setting up Opensshd-server.
everything works fine when I try ssh user@localhost

but when I try to connect though another computer on the network it gives me:

Connection Lost
pool-my-ip-address.plspca.dsl-w.verizon.net/my.ip.address:22 - Connection Refused

i also tried different ports which I have forwarded on my router but it doesn't connect. I would really appreciate some help

thanks in advance
Post output of
```
cat /etc/ssh/sshd_config
```

Have you set opensshd to bind on the local LAN ip? Sometimes, opensshd only binds on the local IP, and not the LAN.

See if you can ssh into your LAN ip to test it out.

---

### Post by julio8a00 on 2012-05-23
it connects if I use this IP 192.168.1.35  (local network IP)

but I can't connect using my public IP/DNS address, only Local.

I am attempting to connect from outside the local network.

---

### Post by sandyd on 2012-05-24
Verizon is thought to be blocking and/or sniffing ports. SSH won't work.

---

### Post by julio8a00 on 2012-05-29
I'll contact my ISP thanks!  =D

---

### Post by roton on 2012-05-29
> **julio8a00 said:**
> I'll contact my ISP thanks!  =D

Or you could just run it on a port which is definitely open/allowed.

---

### Post by Cheesemill on 2012-05-29
You also have to set up port forwarding on your router to allow connections from outside your LAN through to the machine you are trying to connect to.

---

### Post by wixi on 2012-06-05
I've got the same problem. In the previous Ubuntu 11.10 I had, there was no problem with the ssh. Now after completly now installation of the 12.04, I can only connect using local network (using). The internet provider and port forwarding on the router did not change and are completly not the cause. Firewall is even disabled in Ubuntu to be sure..

There must be some problem on the Ubuntu OS side. Did anyone have such a problem and resolved it? If yes, please help.

---

### Post by stmiller on 2012-06-06
To check if port 22 is open from the outside, you can run something like shields up:

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by reptilezone2002 on 2012-06-07
> **julio8a00 said:**
> Hello,

I found a tutorial online on setting up Opensshd-server.
everything works fine when I try ssh user@localhost

but when I try to connect though another computer on the network it gives me:

Connection Lost
pool-my-ip-address.plspca.dsl-w.verizon.net/my.ip.address:22 - Connection Refused

i also tried different ports which I have forwarded on my router but it doesn't connect. I would really appreciate some help

thanks in advance

thres to config files

/etc/ssh/ssh_conf & sshd_conf 

edit those files find the line represent the port no & if it the line is commented out with a # symbol remove the # to uncomment the tile do this for both the files & restart the service by sudo service ssh restart

and another thing if u r using ssh from the internet change the port no from default port 22 to another port (that can be done by editing the above mentioned files & changing the line that says port=22 ) coz at the moment u open ssh port 22 to the internet u r vulnerable to attaks . hope this solve ur brob.. plz let us know how it went

---

