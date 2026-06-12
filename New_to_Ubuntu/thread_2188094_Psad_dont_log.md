---
title: "Psad dont log"
date: 2013-11-15
forum: New to Ubuntu
---

### Post by ido555333 on 2013-11-15
hi 
i install psad and i follow this instruction [http://krystianekb.blogspot.co.uk/2013/01/ubuntu-port-scan-detection-tools-psad.html](http://krystianekb.blogspot.co.uk/2013/01/ubuntu-port-scan-detection-tools-psad.html)


i use[B][SIZE=3] gufw firewall gui[/SIZE]

[SIZE=2][SIZE=3]and setting : [/SIZE]incoming :deny
[SIZE=3]
the psad dont log alerts
i made some test with this linux machine and my windows laptop both use zenmap
i have loggs and alerts in my firewall in : /var/log/kern.log

and i see the ports scan that i made but
when i check the psad there is no logs

[/SIZE][/SIZE][/B]root@gfr:~# psad --Status
[+] psadwatchd (pid: 21236) %CPU: 0.0 %MEM: 0.0
Running since: Fri Nov 15 17:30:04 2013


[+] psad (pid: 21234) %CPU: 0.0 %MEM: 0.1
Running since: Fri Nov 15 17:30:04 2013
Command line arguments: [none specified]
Alert email address(es): root@localhost


[+] Version: psad v2.2.1


[+] Top 50 signature matches:
[NONE]


[+] Top 25 attackers:
[NONE]


[+] Top 20 scanned ports:
[NONE]


[+] iptables log prefix counters:
[NONE]


Total protocol packet counters:


[+] IP Status Detail:
[NONE]


Total scan sources: 0
Total scan destinations: 0


[+] These results are available in: /var/log/psad/status.out



[SIZE=3][B]in file conf of psad i did make change to
[/B][/SIZE]HOME_NET 192.168.1.6
[SIZE=3][B]i try 192.168.1.1/20
and 192.168.1.6

none of them work[/B][/SIZE]

---

