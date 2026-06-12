---
title: "Opening port 80 on Ubuntu 14 Server and making it visible on the internet"
date: 2014-10-12
forum: New to Ubuntu
---

### Post by Adam_Togni on 2014-10-12
Hello, im very new to Ubuntu and dedicated servers but unfortunately cost dedicated that I purchase an unmanaged dedicated server :-(

Anywho, heres my problem, im trying to access my server from the internte but when i type in the IP address in the address bar i just get an error page Server not Responding, Im pretty sure its down to the port 80 not being open, however ive been faffing around with it all weekend and am getting nowhere, below is the readout for nmap and port 80 is showing as open:

Starting Nmap 6.40 ( [http://nmap.org](http://nmap.org) ) at 2014-10-12 20:39 BST
Nmap scan report for footwear2userver (127.0.1.1)
Host is up (0.000019s latency).
Not shown: 991 closed ports
PORT      STATE SERVICE
21/tcp    open  ftp
22/tcp    open  ssh
25/tcp    open  smtp
80/tcp    open  http
110/tcp   open  pop3
143/tcp   open  imap
993/tcp   open  imaps
995/tcp   open  pop3s
10000/tcp open  snet-sensor-mgmt

And below is my iptables readout:

Chain INPUT (policy DROP)
target     prot opt source               destination         
fail2ban-ssh  tcp  --  anywhere             anywhere             multiport dports ssh
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh
DROP       all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http

I'm a little worried about the fact that DROP all is before the http line.

If you need anything else please let me know.

Any help is grateful, however please bear in mind I'm an absolute newbie but I am eager to learn and pick things up pretty quick.

---

### Post by nerdtron on 2014-10-12
This can be achieved easily using UFW. (be sure no iptable rules is currently active)

```
sudo ufw allow port 80
sudo ufw allow from IP.x.x.x to any port 22
sudo ufw enable
sudo ufw status

```

First line opens the port 80 to anyone. Second line opens port 22 from the specific IP address you like.

More info here: [https://www.digitalocean.com/community/tutorials/how-to-setup-a-firewall-with-ufw-on-an-ubuntu-and-debian-cloud-server](https://www.digitalocean.com/community/tutorials/how-to-setup-a-firewall-with-ufw-on-an-ubuntu-and-debian-cloud-server)

---

### Post by Adam_Togni on 2014-10-12
Hi nerdtron, many thanks for the swift response, i had been to that website among others over the weekend and have done what it said, wfw status as below, although I havent set the sudo ufw allow from IP.x.x.x to any port 22, as the shh is working fine!

How do i make sure iptable rules are currently active?Status: active

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW       Anywhere
22                         ALLOW       Anywhere
80                         ALLOW       Anywhere
22/tcp (v6)                ALLOW       Anywhere (v6)
22 (v6)                    ALLOW       Anywhere (v6)
80 (v6)                    ALLOW       Anywhere (v6)

Any other ideas?

---

### Post by SeijiSensei on 2014-10-13
> Nmap scan report for footwear2userver (127.0.1.1)

That IP is local to the machine and not the one visible to networks.  Most firewalls do not block traffic on these IPs even if they have rules to control access on public-facing interfaces.  You need to use the public IP with nmap to see what ports are visible to the outside.

---

### Post by Adam_Togni on 2014-10-13
Thanks SeijiSensei

Heres the nmap for the public address

Host is up (0.000022s latency).
Not shown: 990 closed ports
PORT      STATE SERVICE
21/tcp    open  ftp
22/tcp    open  ssh
25/tcp    open  smtp
53/tcp    open  domain
80/tcp    open  http
110/tcp   open  pop3
143/tcp   open  imap
993/tcp   open  imaps
995/tcp   open  pop3s
10000/tcp open  snet-sensor-mgmt

Nmap done: 1 IP address (1 host up) scanned in 2.47 seconds

---

### Post by Adam_Togni on 2014-10-13
SeijiSensei mentioning the local IP made me think maybe its my hosts file thats wrong, here it is for reference, should one of the IP addresses here be the public address?

127.0.0.1       localhost
127.0.1.1       footwear2userver

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

---

### Post by nerdtron on 2014-10-13
> **Adam_Togni said:**
> Hi nerdtron, many thanks for the swift response, i had been to that website among others over the weekend and have done what it said, wfw status as below, although I havent set the sudo ufw allow from IP.x.x.x to any port 22, as the shh is working fine!

How do i make sure iptable rules are currently active?Status: active

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW       Anywhere
22                         ALLOW       Anywhere
80                         ALLOW       Anywhere
22/tcp (v6)                ALLOW       Anywhere (v6)
22 (v6)                    ALLOW       Anywhere (v6)
80 (v6)                    ALLOW       Anywhere (v6)

Any other ideas?


Sorry I have a typo on my earlier post. Before you enable the ufw, you should not have any iptables rules. Just the UFW do the management of the firewall. Flush/reset everything on the iptables (or reboot the server) and enable/disable ufw again.

Also, does the public IP assigned to the server or on a router with port forwarding? There are other ports that are open.

---

