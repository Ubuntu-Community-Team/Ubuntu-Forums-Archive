---
title: "unable to ping the same interface after configuring an IPv6 address ubuntu 12.04"
date: 2013-02-22
forum: New to Ubuntu
---

### Post by sumitkamboj on 2013-02-22
I setup IPv6 in my Ubuntu 12.04 on eth0 using command

  ifconfig eth0 inet6 add 2001:db8:fedc:cdef::1/64   but when i try to ping eth0 itself using 
  
ping6 2001:db8:fedc:cdef::1   

it always gives 
  
PING 2001:db8:fedc:cdef:0:0:0:1(2001:db8:fedc:cdef::1)  56 data bytes  
From ::1 icmp_seq=1 Destination unreachable: Address unreachable  
From ::1 icmp_seq=2 Destination unreachable: Address unreachable  
From ::1 icmp_seq=3 Destination unreachable: Address unreachable   

I think that it automatically is pinging from ::1 to `2001:db8:fedc:cdef::1
  
Command 
  
ip addr show dev eth0   it gives
  
2: eth0:<NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN qlen 1000 link/ether 00:1b:38:a1:a2:50 brd ff:ff:ff:ff:ff:ff inet6 2001:db8:fedc:cdef::1/64 scope global tentative     valid_lft forever preferred_lft forever   

Command 
  
ip -6 route   it gives
  
2001:db8:fedc:cdef::/64 dev eth0  proto kernel  metric 256  fe80::/64 dev eth0  proto kernel  metric 256    

Command 
  
ip6tables -L   

it gives
  
Chain INPUT (policy ACCEPT) target     prot opt source               destination           
Chain FORWARD (policy ACCEPT) target     prot opt source               destination           
Chain OUTPUT (policy ACCEPT) target     prot opt source               destination      

Command 
  
ip6tables -F 
it gives nothing.   

Please help how to solve this.

---

### Post by fdrake on 2013-02-22
man ping
> 

       -I interface address

Set  source address to specified interface address. Argument may be numeric IP address or name of device. When pinging IPv6 link-local address this option is required.


try this :
```


ping -I eth0 2001:db8:fedc:cdef::1
 
```

check my post I edited my code

---

### Post by sumitkamboj on 2013-02-22
thanks for reply

it still not working.
please help i stuck here from last 15 days.
i would let you know that i have dual boot ubuntu 12.04. another ubuntu(that is upgraded from ubuntu 11.10) doing the same for me very well.

---

### Post by prodigy_ on 2013-02-22
> **sumitkamboj said:**
> state DOWN
What are you trying to ping? ;)

> **sumitkamboj said:**
> NO-CARRIER
I'd start with connecting a network cable. (If it's already connected, more info is needed. For starters, what's on the other side and has this connection ever worked before). Then try:
```
sudo ifconfig eth0 up
```

---

### Post by sumitkamboj on 2013-02-28
I am trying to set IPv6 address to a Ethernet interface(eth0) so that i can ping the eth0 interface. There is no role of cable because i am trying to ping the same interface in my PC. For example when i try to ping lo(localhost) using command

ping6 -I lo ::1 

it reply with ICMP request.
i want to do the same for my eth0 interface so that i get reply from eth0.

---

### Post by sumitkamboj on 2013-03-02
this may have clue for someone    command
  
     ip -6 route get 2001:db8:fedc:cdef::1   gives
  
    2001:db8:fedc:cdef::1 from :: via 2001:db8:fedc:cdef::1 dev eth0  src ::1  metric 0  cache    

why it has src ::1 ?

---

