---
title: "[SOLVED] Apache newb"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Travarious on 2008-11-03
I recently installed Ubuntu 8.04 and I installed apache. I have apache up and going I can go to [http://localhost](http://localhost) and I get the IT WORKS!! page. The problem that I am having however is that when I try and go to my web server on my local network I get no response. I am using a different system on the same router and same subnet. I am able to ping the webserver(Ubuntu) from the client(winXP) system and I get a response. however when I go to the Firefox and type in the IP address of the webserver (192.168.2.4) It just times out. I am using a Belkin router and I have port 80 requests bing forwarded to 192.168.2.4 however there is still no reply. I have been researching this on forums and other Google posts but have had no luck. the closest one I can find to my situation is people not using the correct address then they do and it works. such is not the case for me. 

I apologize if this is already somewhere else I couldn't find it.


<Just because I'm paranoid doesn't mean people aren't really out to get me.>

---

### Post by chrisod on 2008-11-03
Have you tried turning off the forwarding? Forwarding is usually for requests coming in from outside of the network. I wonder if maybe you've created some sort of conflict with the router frying to forward the port 80 request back to itself.

---

### Post by Iowan on 2008-11-03
[This]("https://help.ubuntu.com/community/ApacheMySQLPHP") is a good How-To.  One possible solution is to simply add "127.0.1.1 hostname" to your **hosts** file.

I have another article (somewhere) that "secures" Apache by making it accessible only from "localhost". Replacing "localhost" with the hostname - or IP address "unsecures" it.

---

### Post by Travarious on 2008-11-04
> **Iowan said:**
> [This]("https://help.ubuntu.com/community/ApacheMySQLPHP") is a good How-To.  One possible solution is to simply add "127.0.1.1 hostname" to your **hosts** file.

I have another article (somewhere) that "secures" Apache by making it accessible only from "localhost". Replacing "localhost" with the hostname - or IP address "unsecures" it.

Ok I followed the How-To and when I get to step right after disable and enable then I restart and I get the following error.

 * Restarting web server apache2                                                [Mon Nov 03 23:32:44 2008] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Mon Nov 03 23:32:54 2008] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

Not sure what this is all about line 3 is as follows
Alias /phpmyadmin /usr/share/phpmyadmin 
I commented it out and now I am getting the following.

* Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

I have seen this somewhere but my brain seems fried. wait it's in the walk-through. I created the file now things are restarting properly and when I go to local host I see the index containing the webpage I created but still NOGO when I try to connect from the windows box.

I have tried to connect at every step of the process each attempt made to connect was made with forwarding on and off on the router.

I appreciate the help and advise given so far any other advise would be greatly appreciated a copy of my hosts file is below 

127.0.0.1	localhost
127.0.1.1	Game-laptop


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


Thanks again.

---

### Post by conjur3r on 2008-11-04
Do you have the firewall enabled?  It might be blocking port 80 (default www port) in.  What is the output of this (prints firewall rules):

# sudo iptables -L

---

### Post by cariboo on 2008-11-04
This error:

> * Restarting web server apache2 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

is nothing to worry about it just means that you haven't set up a nme for your server in /etc/hosts eg:

```
127.0.0.1 localhost
127.0.1.1 Game-laptop
192.168.2.4 webserver
```

If you still have your web server forwarded to the router turn of the port forwarding as that might be your problem as sime routers don't allow you to loop around the router and access the external ip address.

Jim

---

### Post by Travarious on 2008-11-04
Ok first off thanks for the all the help.

I have tried to connect with port forwarding on and off. I did update my hosts file it now look like:

127.0.0.1	localhost
127.0.1.1	Game-laptop
192.168.2.4     webserver


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


I went to the terminal and ran the sudo iptables -L comand and the output is:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
RH-Lokkit-0-50-INPUT  all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
RH-Lokkit-0-50-INPUT  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain RH-Lokkit-0-50-INPUT (2 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh flags:FIN,SYN,RST,ACK/SYN 
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     udp  --  192.168.2.1          anywhere            udp spt:domain 
ACCEPT     udp  --  home.domain.actdsltmp  anywhere            udp spt:domain 
ACCEPT     udp  --  resolver.qwest.net   anywhere            udp spt:domain 
REJECT     tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp reject-with icmp-port-unreachable 

I notice that it states Rejecting tcp traffic anywhere I will be looking into this further. if I come up with a solution to get it change I will post back. If I have not posted back I would greatly appreciate any advise that could be given about what this is how it will affect me trying to connect and what would be a secure method of setting it up to allow incoming traffic.

---

### Post by Travarious on 2008-11-04
I have installed firestarter and configured it to allow traffic from the system I am testing and bingo everything is up and going thanks for all the help!!

---

