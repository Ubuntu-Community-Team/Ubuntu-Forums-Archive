---
title: "cant resolve hostname"
date: 2013-04-19
forum: New to Ubuntu
---

### Post by Maik20 on 2013-04-19
Hi,

i am new to linux/ubuntu. I set up my first linuxserver as virutal host (vmware). I setup the network interface to use dhcp. The ip i got assigned is correct. i can ping all ip-adresse in my private network and i can ips in the internet for example "ping 173.194.69.94" (for one of googles server). But i cant resolve a hostname. "ping www.google.com" results in a time out. 
in /etc/resolve.conf i found this
nameserver 192.168.2.1
search Speedport_W723_V_Typ_A_1_00_096

the ip 192.168.2.1 is my router. this was setup automaticaly.

I have no idea why it wont work.

Thanks

Maik

---

### Post by m4gnus on 2013-04-19
Hello,

So what are you trying to get accomplished? Want to add a different gateway IP? Or are you simply wanting to know why that particular IP was plugged in?

---

### Post by jorok_tupur on 2013-04-20
> **Maik20 said:**
> Hi,

i am new to linux/ubuntu. I set up my first linuxserver as virutal host (vmware). I setup the network interface to use dhcp. The ip i got assigned is correct. i can ping all ip-adresse in my private network and i can ips in the internet for example "ping 173.194.69.94" (for one of googles server). But i cant resolve a hostname. "ping www.google.com" results in a time out. 
in /etc/resolve.conf i found this
nameserver 192.168.2.1
search Speedport_W723_V_Typ_A_1_00_096

the ip 192.168.2.1 is my router. this was setup automaticaly.

I have no idea why it wont work.

Thanks

Maik

You might get better response from the virtualisation forum:

[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

---

