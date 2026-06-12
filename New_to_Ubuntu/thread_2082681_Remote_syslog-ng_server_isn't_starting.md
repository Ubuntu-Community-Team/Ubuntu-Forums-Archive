---
title: "Remote syslog-ng server isn't starting"
date: 2012-11-10
forum: New to Ubuntu
---

### Post by shtivis on 2012-11-10
Hi,
I installed a syslog-ng on Ubuntu.
I modified the syslog-ng.conf
I added the following lines:
source s_external
{
        udp(ip(192.168.7.237) port(514));
};
when i issue the command:
sudo netstat -tanpu|grep syslog
or
netstat -a | grep 514

I get nothing
When I use Wireshark i see my router sends packets to the Ubuntu but I get an Echo replay that there is no answer from port 514.

I got no firewall
omer@omer-virtual-machine:~$ sudo ufw status
Status: inactive
omer@omer-virtual-machine:~$ 

I need some ideas..
Best regards,
Shtivis

---

### Post by HiImTye on 2012-11-10
from what I've read what you need is
```
source s_syslog { syslog(ip(192.168.7.237) port(514) transport("udp")); };
```
but I don't personally use it

---

### Post by shtivis on 2012-11-10
Thanks,
But where I need to insert it? in the config file or in the ubuntu?

tried both still nothing

---

### Post by HiImTye on 2012-11-10
in syslog-ng.conf

---

### Post by shtivis on 2012-11-10
Tried,
Still not working

---

