---
title: "Ubuntu Firewall??"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by markbusu on 2008-07-15
Hi guys,

I am running 8.04 Server edition, and been racking my brains on an issue i am having.

I have configured SNMP correctly on UBT01, and able to get SNMP information locally (There is no Host specified in snmpd.conf there it is not an SNMP access list issue).

When running a TCPDUMP on UBT01 i can see the following:

```
00:42:58.677424 IP 192.168.1.101.43511 > 192.168.1.103.snmp:  C=mark GetNextRequest(25)
00:42:58.677492 IP 192.168.1.103 > 192.168.1.101: ICMP 192.168.1.103 udp port snmp unreachable, length 74
```

Is there any firwall installed on Ubuntu or anything that might be denying the connection.

Thanks for any feedback you can give!

Mark

---

### Post by bodhi.zazen on 2008-07-15
The firewall is called iptables ant there are a number of front ends.

By default the firewall is permissive.

You can check your firewall rules with :

```
sudo iptables -L
```

See also :

[uhelp]community/Uncomplicated_Firewall_ufw[/uhelp]

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

---

### Post by jimv on 2008-07-15
[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

---

### Post by bodhi.zazen on 2008-07-15
> **jimv said:**
> [https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

Firestarter will not run without X.

---

### Post by jimv on 2008-07-16
> **bodhi.zazen said:**
> Firestarter will not run without X.

Good point.  I forget that not everyone installs a gui on their server.

---

### Post by davemiles871 on 2008-10-24
Its probably not a firewall issue, as by default the firewall allows everything. Its worth checking the entries in /etc/default/snmpd to see if the snmpd daemon is actually listening on the main IP address of the system, because by default it only listens on 'localhost' 127.0.0.1

I simply added the hostname of the system to the end SNMPDOPTS line and restarted the daemon and lo and behold it works.:)

---

