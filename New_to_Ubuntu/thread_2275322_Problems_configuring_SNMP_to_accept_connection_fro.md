---
title: "Problems configuring SNMP to accept connection from other host in the network"
date: 2015-04-25
forum: New to Ubuntu
---

### Post by roberts123 on 2015-04-25
I want to make SNMP Agent accept connections from other hosts in the network.


the IP address the other hosts are as follows


    192.168.28.139(Solaris 10) -its a virtual machine
    192.168.1.76(Windows 7)- my personal desktop


This is what I done 
In file /etc/snmp/snmpd.conf


    agentAddress udp:161


    rocommunity public localhost 
    rocommunity public 192.168.1.0/24
    rocommunity public 192.168.28.0/24


and in my /etc/default/snmpd


    SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -g snmp -I -smux -p /var/run/snmpd.pid'


It's works when I do
  
     snmpwalk -v 2c -c public localhost


and 


     snmpwalk -v 2c -c public 192.168.28.139


But if I use snmpwalk on my my Windows 7 IP address, It gives Timeout:No response from 192.168.1.76


     snmpwalk -v 2c -c public 192.168.1.76 
     Timeout:No response from 192.168.1.76


Please help.

---

### Post by nerdtron on 2015-04-25
It's really difficult to test when you have a NAT-ted Virtual Machine. Try to use Bridged adapter on the Network settings of your Virtual machine. This way, your local LAN, windows machine, and the the virtual machine will have the same IP block.

---

### Post by roberts123 on 2015-04-25
Thanks. i will give it a try.

---

