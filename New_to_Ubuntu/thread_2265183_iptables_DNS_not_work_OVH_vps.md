---
title: "iptables DNS not work OVH vps"
date: 2015-02-13
forum: New to Ubuntu
---

### Post by unreal2 on 2015-02-13
Hi,

ssh work good;
dns not working why ? Where is my mistake.


```
#!/bin/sh
### BEGIN INIT INFO
# Provides:          ip-fr-rule.sh
# Required-Start:    $local_fs $remote_fs
# Required-Stop:     $local_fs $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start daemon at boot time
# Description:       Enable service provided by daemon.
### END INIT INFOi


iptables -F
iptables -X

iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP

# SPIS PORTOW
#
# 80 www
# 110 POP3
# 9000 PHP
# 21 FTP
# 22 ssh
# 25 smtp
# 53 dns
# 143 imap
# 443 https
# 23 telnet
# 3306 mysql
#
#

#INPUT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -p tcp --dport 53 -m state --state NEW -j ACCEPT
iptables -A INPUT -p udp --dport 53  -m state --state NEW -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -m state --state NEW  -j ACCEPT
iptables -A INPUT -p tcp --dport 80 -m state --state NEW  -j ACCEPT
iptables -A INPUT -p tcp --dport 443 -m state --state NEW -j ACCEPT

iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
#OUTPUT
iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

iptables -A OUTPUT -p tcp --sport 53 -j ACCEPT
iptables -A OUTPUT -p tcp --sport 22 -j ACCEPT
iptables -A OUTPUT -p tcp --sport 80 -j ACCEPT
iptables -A OUTPUT -p tcp --sport 443 -j ACCEPT
iptables -A OUTPUT -p udp --sport 53 -j ACCEPT
iptables -A OUTPUT -p icmp --icmp-type echo-reply -j ACCEPT

```

---

### Post by Doug S on 2015-02-13
If I understand correctly, which is questionable...

I think your external DNS requests that are resolvable by your internal DNS should be working. However, your internal DNS will need to forward requests for your computer to access the outside world, for example to access ubuntu to get updates. For that you would need to allow out with a destination port of 53. However, be careful because I don't think you don't want people to be able to recurse through your DNS.

As separate from your iptables, check that your internal DNS is listening to your external IP address. Example:```
doug@doug-64:~/public_html/linux/ubuntu-docs/help.ubuntu.com/dev$ [COLOR=#ff0000]sudo netstat -utlpn[/COLOR]
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      1712/smbd
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1502/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      1712/smbd
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      23807/apache2
[COLOR=#ff0000]tcp        0      0 173.180.XXX.YYY:53      0.0.0.0:*               LISTEN      1311/named[/COLOR]
tcp        0      0 192.168.111.1:53        0.0.0.0:*               LISTEN      1311/named
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1311/named
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1188/sshd
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1566/master
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      1311/named
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      23807/apache2
[COLOR=#ff0000]udp        0      0 173.180.XXX.YYY:53      0.0.0.0:*                           1311/named[/COLOR]
udp        0      0 192.168.111.1:53        0.0.0.0:*                           1311/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                           1311/named
udp        0      0 0.0.0.0:67              0.0.0.0:*                           1356/dhcpd
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1059/dhclient3
udp        0      0 192.168.111.255:137     0.0.0.0:*                           1257/nmbd
udp        0      0 192.168.111.1:137       0.0.0.0:*                           1257/nmbd
udp        0      0 0.0.0.0:137             0.0.0.0:*                           1257/nmbd
udp        0      0 192.168.111.255:138     0.0.0.0:*                           1257/nmbd
udp        0      0 192.168.111.1:138       0.0.0.0:*                           1257/nmbd
udp        0      0 0.0.0.0:138             0.0.0.0:*                           1257/nmbd
```Note: My internal DNS doesn't actually respond to external inquiries, but I deal with that in my iptables rule set.

---

### Post by unreal2 on 2015-02-14
I have read many configs iptables and I understood .

This is solution 
```
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT
```

and now working.

---

### Post by Doug S on 2015-02-14
> **unreal2 said:**
> I have read many configs iptables and I understood .

This is solution 
```
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT
```

and now working.Yes, of course. Glad you got it working.

---

