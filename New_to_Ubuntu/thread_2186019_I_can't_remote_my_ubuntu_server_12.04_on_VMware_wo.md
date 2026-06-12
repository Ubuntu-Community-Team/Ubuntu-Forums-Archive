---
title: "I can't remote my ubuntu server 12.04 on VMware workstation 7 from putty"
date: 2013-11-05
forum: New to Ubuntu
---

### Post by samuel.siahaanq on 2013-11-05
I can't remote my ubuntu server 12.04 on VMware workstation 7 from putty.

I've just install Ubuntu Server 12.04 on VMware Workstation 7, when i ping to my host 192.168.10.103 is conected, 
ping to 8.8.8.8 => conected 
sudo apt-get update or sudo apt-get upgrade -> it's work 
apt-get install ssh openssh-server -> it's work

_FYI :_
***Ubuntu Server on VMware Workstation 7:***
IP Addres : 192.168.10.5
Netmask : 255.255.255.0
Gateway : 192.168.10.1
Network : 192.168.10.0
Broadcast : 192.168.10.255
dns-nameserver : 192.168.10.1

My PC (Win XP SP3)
IP Addres : 192.168.10.103
Netmask : 255.255.255.0
Gateway : 192.168.10.1

On My VMware network i choose **Bridged**

the problem is : I can't remote my ubuntu server 12.04 on VMware workstation 7 from putty (no respond in screen).
i send too the printscreen for adding your infomations.

[http://www.mediafire.com/view/myfiles/#rr5z9intszsyztz](http://www.mediafire.com/view/myfiles/#rr5z9intszsyztz)

[http://www.mediafire.com/view/myfiles/#v51jj38q8xzkdql](http://www.mediafire.com/view/myfiles/#v51jj38q8xzkdql)

[http://www.mediafire.com/view/myfiles/#74c4jnlv03zihze](http://www.mediafire.com/view/myfiles/#74c4jnlv03zihze)

[http://www.mediafire.com/view/myfiles/#7dvy4atynnm6mih](http://www.mediafire.com/view/myfiles/#7dvy4atynnm6mih)


[IMG]http://www.mediafire.com/?7dvy4atynnm6mih[/IMG]

[IMG]http://www.mediafire.com/?74c4jnlv03zihze[/IMG]

[IMG]http://www.mediafire.com/?v51jj38q8xzkdql[/IMG]

[IMG]http://www.mediafire.com/?7dvy4atynnm6mih,74c4jnlv03zihze,v51jj38q8xzkdql,rr5z9intszsyztz[/IMG]

---

### Post by Doug S on 2013-11-05
Hi and welcome to Ubuntu forums,

Your first posting is very thorough and complete and you have covered most things I can think of to check. Are you sure sshd is listening?```
doug@doug-64:~$ [COLOR=#ff0000]sudo netstat -tpln[/COLOR]
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1225/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      1581/smbd
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1176/apache2
tcp        0      0 173.180.45.4:53         0.0.0.0:*               LISTEN      1181/named
tcp        0      0 192.168.111.1:53        0.0.0.0:*               LISTEN      1181/named
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1181/named
[COLOR=#ff0000]tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1064/sshd[/COLOR]
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1436/master
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      1181/named
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      1581/smbd
```

---

