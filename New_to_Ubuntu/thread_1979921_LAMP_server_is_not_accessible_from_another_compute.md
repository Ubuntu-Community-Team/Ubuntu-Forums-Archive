---
title: "LAMP server is not accessible from another computer on the same LAN"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by bariamtak on 2012-05-14
Hi I am trying to set up a server to tweak around with my ubuntu 12.04 . I installed LAMP sucessfully and i can access it from the host by typing the hostname.
My problem is that i cannot access the server from another desktop on the same network.
I have searched the forums and googled it for a long time without any success. I found similar thread here [http://ubuntuforums.org/showthread.php?t=1923203&highlight=access+apache+server+network](http://ubuntuforums.org/showthread.php?t=1923203&highlight=access+apache+server+network) but the guy's problem was solved by editing the configuration of file /etc/apache2/sites-enabled/000-default:
While it doesn't solved mine. I tried everything which i know of but now I am at lost. I didn't change the default port which is 80.
Any help will be greatly appreciated. Thank you.

---

### Post by agillator on 2012-05-14
First, is there a firewall involved? There could be on on the server, the client and/or the LAN itself. Run the command 'sudo iptables -L -v' on both the server and the client. If you get anything except chain policies, i.e. you get actual rules, then make sure port 80 is open.

Second, how are you trying to access the server? If there is no DNS server on the LAN and you are trying to use the hostname of the server on the client, it probably can't find it. Assuming the server has a fixed ip there are two ways to fix this problem. First, use the ip address instead of the hostname when accessing it. Second, if you make an entry in the /etc/hosts file for the server and its ip address, then you can reach it through the hostname. The hosts file is the first place your system looks in resolving names.

See if one of these solves your problem.

---

### Post by DingusFett on 2012-05-14
Probably a dumb question, but can you ping to the IP address of the server? And yeah, I would start making sure it has a static IP set and make sure you're trying to access it through the address rather than host name.

---

### Post by d4m1r on 2012-05-14
Do you have a static IP assigned to the server on the network? If you don't, try accessing the server by using its internal IP instead of its hostname.

If you do want to access it by hostname in the future, you need to save its IP and hostname in your /etc/hosts file (sudo gedit /etc/hosts), on every PC on your network. Example:

192.168.1.5    lamp-server

Then every time you enter lamp-server in your browser, it will redirect to that local IP. Hope this helps.

---

### Post by bariamtak on 2012-05-14
> **agillator said:**
> First, is there a firewall involved? There could be on on the server, the client and/or the LAN itself. Run the command 'sudo iptables -L -v' on both the server and the client. If you get anything except chain policies, i.e. you get actual rules, then make sure port 80 is open.

Second, how are you trying to access the server? If there is no DNS server on the LAN and you are trying to use the hostname of the server on the client, it probably can't find it. Assuming the server has a fixed ip there are two ways to fix this problem. First, use the ip address instead of the hostname when accessing it. Second, if you make an entry in the /etc/hosts file for the server and its ip address, then you can reach it through the hostname. The hosts file is the first place your system looks in resolving names.

See if one of these solves your problem.


I think the port 80 is open and here is the output of iptables -L -v.
*************************************************************************
bariamtak@bariamtak-pc:~$ sudo iptables -L -v
[sudo] password for bariamtak: 
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
12216   16M ufw-before-logging-input  all  --  any    any     anywhere             anywhere            
12216   16M ufw-before-input  all  --  any    any     anywhere             anywhere            
   60  4680 ufw-after-input  all  --  any    any     anywhere             anywhere            
    0     0 ufw-after-logging-input  all  --  any    any     anywhere             anywhere            
    0     0 ufw-reject-input  all  --  any    any     anywhere             anywhere            
    0     0 ufw-track-input  all  --  any    any     anywhere             anywhere            

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-before-logging-forward  all  --  any    any     anywhere             anywhere            
    0     0 ufw-before-forward  all  --  any    any     anywhere             anywhere            
    0     0 ufw-after-forward  all  --  any    any     anywhere             anywhere            
    0     0 ufw-after-logging-forward  all  --  any    any     anywhere             anywhere            
    0     0 ufw-reject-forward  all  --  any    any     anywhere             anywhere            

Chain OUTPUT (policy ACCEPT 31 packets, 1972 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 9778  869K ufw-before-logging-output  all  --  any    any     anywhere             anywhere            
 9778  869K ufw-before-output  all  --  any    any     anywhere             anywhere            
  848 65699 ufw-after-output  all  --  any    any     anywhere             anywhere            
  848 65699 ufw-after-logging-output  all  --  any    any     anywhere             anywhere            
  848 65699 ufw-reject-output  all  --  any    any     anywhere             anywhere            
  848 65699 ufw-track-output  all  --  any    any     anywhere             anywhere            

Chain ufw-after-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   60  4680 ufw-skip-to-policy-input  udp  --  any    any     anywhere             anywhere             udp dpt:netbios-ns
    0     0 ufw-skip-to-policy-input  udp  --  any    any     anywhere             anywhere             udp dpt:netbios-dgm
    0     0 ufw-skip-to-policy-input  tcp  --  any    any     anywhere             anywhere             tcp dpt:netbios-ssn
    0     0 ufw-skip-to-policy-input  tcp  --  any    any     anywhere             anywhere             tcp dpt:microsoft-ds
    0     0 ufw-skip-to-policy-input  udp  --  any    any     anywhere             anywhere             udp dpt:bootps
    0     0 ufw-skip-to-policy-input  udp  --  any    any     anywhere             anywhere             udp dpt:bootpc
    0     0 ufw-skip-to-policy-input  all  --  any    any     anywhere             anywhere             ADDRTYPE match dst-type BROADCAST

Chain ufw-after-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  any    any     anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "

Chain ufw-after-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  any    any     anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "

Chain ufw-after-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-user-forward  all  --  any    any     anywhere             anywhere            

Chain ufw-before-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  810 58789 ACCEPT     all  --  lo     any     anywhere             anywhere            
11274   16M ACCEPT     all  --  any    any     anywhere             anywhere             state RELATED,ESTABLISHED
    0     0 ufw-logging-deny  all  --  any    any     anywhere             anywhere             state INVALID
    0     0 DROP       all  --  any    any     anywhere             anywhere             state INVALID
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere             icmp destination-unreachable
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere             icmp source-quench
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere             icmp time-exceeded
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere             icmp parameter-problem
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere             icmp echo-request
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere             udp spt:bootps dpt:bootpc
  132 17158 ufw-not-local  all  --  any    any     anywhere             anywhere            
   72 12478 ACCEPT     udp  --  any    any     anywhere             224.0.0.251          udp dpt:mdns
    0     0 ACCEPT     udp  --  any    any     anywhere             239.255.255.250      udp dpt:1900
   60  4680 ufw-user-input  all  --  any    any     anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  810 58789 ACCEPT     all  --  any    lo      anywhere             anywhere            
 8120  744K ACCEPT     all  --  any    any     anywhere             anywhere             state RELATED,ESTABLISHED
  848 65699 ufw-user-output  all  --  any    any     anywhere             anywhere            

Chain ufw-logging-allow (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  any    any     anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW ALLOW] "

Chain ufw-logging-deny (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     all  --  any    any     anywhere             anywhere             state INVALID limit: avg 3/min burst 10
    0     0 LOG        all  --  any    any     anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "

Chain ufw-not-local (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     all  --  any    any     anywhere             anywhere             ADDRTYPE match dst-type LOCAL
   72 12478 RETURN     all  --  any    any     anywhere             anywhere             ADDRTYPE match dst-type MULTICAST
   60  4680 RETURN     all  --  any    any     anywhere             anywhere             ADDRTYPE match dst-type BROADCAST
    0     0 ufw-logging-deny  all  --  any    any     anywhere             anywhere             limit: avg 3/min burst 10
    0     0 DROP       all  --  any    any     anywhere             anywhere            

Chain ufw-reject-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-skip-to-policy-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  any    any     anywhere             anywhere            

Chain ufw-skip-to-policy-input (7 references)
 pkts bytes target     prot opt in     out     source               destination         
   60  4680 DROP       all  --  any    any     anywhere             anywhere            

Chain ufw-skip-to-policy-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  any    any     anywhere             anywhere            

Chain ufw-track-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-track-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  233 13980 ACCEPT     tcp  --  any    any     anywhere             anywhere             state NEW
  584 49747 ACCEPT     udp  --  any    any     anywhere             anywhere             state NEW

Chain ufw-user-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-limit (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  any    any     anywhere             anywhere             limit: avg 3/min burst 5 LOG level warning prefix "[UFW LIMIT BLOCK] "
    0     0 REJECT     all  --  any    any     anywhere             anywhere             reject-with icmp-port-unreachable

Chain ufw-user-limit-accept (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  any    any     anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
bariamtak@bariamtak-pc:~$
***********************************************************************************************************************************
Its foreign to me. But i 'm guessing its not the problem of this. Maybe i'm wrong.

---

### Post by bariamtak on 2012-05-14
Let me clearify about my network.
The ifconfig gives me this.
**************************************************************
bariamtak@bariamtak-pc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 9c:8e:99:42:3a:5f  
          inet addr:10.0.14.15  Bcast:10.0.14.255  Mask:255.255.255.0
          inet6 addr: fe80::9e8e:99ff:fe42:3a5f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14499 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10632 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17051072 (17.0 MB)  TX bytes:1259095 (1.2 MB)
          Interrupt:41 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:907 errors:0 dropped:0 overruns:0 frame:0
          TX packets:907 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:61684 (61.6 KB)  TX bytes:61684 (61.6 KB)
***********************************************************************************
And about the ip, yes it is a static ip.
I am on a LAN which is connected to the University's network.And there is one switch which is use to connect the computers in my network. Now I am really confused whether i am really on a local network or is it the computer which i am trying to access frm is outside my network. But i think its inside the network because it is linked with only a switch.
Or maybe my whole concept is my network is wrong.

Comming back to my problem, its not accessible either by my ip and hostname.
And about DNS i am a little bit confused.

---

### Post by alphacrucis2 on 2012-05-14
> **bariamtak said:**
> 
And about the ip, yes it is a static ip.
I am on a LAN which is connected to the University's network.And there is one switch which is use to connect the computers in my network. Now I am really confused whether i am really on a local network or is it the computer which i am trying to access frm is outside my network. But i think its inside the network because it is linked with only a switch.
Or maybe my whole concept is my network is wrong.

Comming back to my problem, its not accessible either by my ip and hostname.
And about DNS i am a little bit confused.

What's the ip address of the client? Is it in the same subnet as the server.

---

### Post by bariamtak on 2012-05-14
> **alphacrucis2 said:**
> What's the ip address of the client? Is it in the same subnet as the server.

yes it is with the same subnet with the server.
The client ip is 10.0.14.9.


I was going to post the screen shot of my connection information but dont know how to do it. I am still trying.

---

### Post by bariamtak on 2012-05-15
> **agillator said:**
> First, is there a firewall involved? There could be on on the server, the client and/or the LAN itself. Run the command 'sudo iptables -L -v' on both the server and the client. If you get anything except chain policies, i.e. you get actual rules, then make sure port 80 is open.

Second, how are you trying to access the server? If there is no DNS server on the LAN and you are trying to use the hostname of the server on the client, it probably can't find it. Assuming the server has a fixed ip there are two ways to fix this problem. First, use the ip address instead of the hostname when accessing it. Second, if you make an entry in the /etc/hosts file for the server and its ip address, then you can reach it through the hostname. The hosts file is the first place your system looks in resolving names.

See if one of these solves your problem.

I got it to work with the IP. The problem was with the Firewall. Now it works after adding new rule. 
But it's still not accessible with the localhost_name.
The etc/hosts file contains this.
*********************************************************************************
127.0.0.1    localhost
127.0.1.1    bariamtak-pc

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
**********************************************************************************
Do i need to change anything here ?
Thanks in advance.

---

### Post by roelforg on 2012-05-15
Sorry if it has been said before...

But i'm going to address the elephant in the room.
Did you try to access it by using bariamtak-pc as hostname from the client?
Because i think the problem is that you didn't add that to the clients /etc/hosts with the correct ip, if you don't, the client can't resolve the name to an ip.
Appending this to /etc/hosts on the client and reboot should fix it:
```

10.0.14.15 bariamtak-pc

```

---

### Post by bariamtak on 2012-05-15
> **roelforg said:**
> Sorry if it has been said before...

But i'm going to address the elephant in the room.
Did you try to access it by using bariamtak-pc as hostname from the client?
Because i think the problem is that you didn't add that to the clients /etc/hosts with the correct ip, if you don't, the client can't resolve the name to an ip.
Appending this to /etc/hosts on the client and reboot should fix it:
```

10.0.14.15 bariamtak-pc

```

Thank you Roelforg. I add that and its working but what if i want to access it from windows box ? 
And shall i mark this thread solved ?

---

### Post by roelforg on 2012-05-15
> **bariamtak said:**
> Thank you Roelforg. I add that and its working but what if i want to access it from windows box ? 
And shall i mark this thread solved ?
 
Use the ip directly
 
And, mark it if the problem is solved.

---

### Post by bariamtak on 2012-05-15
> **roelforg said:**
> Use the ip directly
 
And, mark it if the problem is solved.

Thank you very much.

---

### Post by DingusFett on 2012-05-15
From Windows (so long as everything is working connecting by IP), just add the same line to the Windows hosts file. It should (from memory here) be in C:\Windows\system32\drivers\etc

10.0.14.15 bariamtak-pc

---

### Post by bariamtak on 2012-05-16
> **DingusFett said:**
> From Windows (so long as everything is working connecting by IP), just add the same line to the Windows hosts file. It should (from memory here) be in C:\Windows\system32\drivers\etc

10.0.14.15 bariamtak-pc


Thank you DingustFett. Thank you everyone. You all rock !

---

