---
title: "set up iptables on Ubuntu Server Breezy Badger"
date: 2006-04-23
forum: Outdated Tutorials &amp; Tips
---

### Post by gymsmoke on 2006-04-23
Since I've gotten so much from the community, I thought I would post this here, since I had so much trouble with setting up my Ubuntu Breezy Badger server...
Also, since this is a topic that alot of people really get nervous about, I thought that this would make it easier for people to get started with it.  I make no real claims to the information, except for the few places where I adjusted the commands for Ubuntu specifically.  The real credit for this belongs to iptablesrocks.org, a great bunch of people who are trying to make linux somewhat less painful for all of us!

So, if you need a basic running (tested!) firewall in 10 steps?  Here we go...

**NOTE:** if you start by typing sudo bash and entering the password, this is a bit easier than typing sudo <cmd> and having to re-enter the password every time.  Otherwise, <sudo> is implied before every command here!
When you're finished, just type exit at the commandline and you'll be returned to your regular user status...

(1) make sure iptables is already installed
[COLOR="Magenta"]dpkg -s iptables[/COLOR]
    if you don't get output like this:
Package: iptables
Status: install ok installed
Priority: important
Section: net
Installed-Size: 976
Maintainer: Laurence J. Lane <ljlane@debian.org>
Architecture: i386
Version: 1.3.1-2ubuntu1.1
Depends: libc6 (>= 2.3.4-1)
Suggests: ipmasq, iproute
Description: Linux kernel 2.4+ iptables administration tools
 netfilter and iptables provide a Linux kernel framework for
 stateful and stateless packet filtering, network and port addresss
 translation, and other IP packet manipulation. The framework is the
 successor to ipchains.
 .
 netfilter and iptables are used in applications such as Internet
 connection sharing, firewalls, IP accounting, transparent proxying,
 advanced routing and traffic control.
 .
 iptables web site: [http://www.iptables.org/](http://www.iptables.org/)

then do [COLOR="Magenta"]apt-get install iptables[/COLOR]

(2) open /etc/syslog.conf in your favorite editor and 
      add this to the bottom of the file
#IPTables logging
kern.debug;kern.info /var/log/firewall

(3) restart the logging daemon
[COLOR="Magenta"]/etc/init.d/sysklogd restart[/COLOR]

(4) install the module ip_conntrack_ftp into the current kernel (if you have ftp server running)
[COLOR="Magenta"]modprobe ip_conntrack_ftp[/COLOR]

(5) install a safety net until your sure that this really works the way you want it to!
    create a new file called firewall_reset in /root (in whatever editor you use)
    and type the following
*filter
:INPUT ACCEPT [164:15203]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [147:63028]
COMMIT

*mangle
:PREROUTING ACCEPT [164:15203]
:INPUT ACCEPT [164:15203]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [147:63028]
:POSTROUTING ACCEPT [147:63028]
COMMIT

*nat
:PREROUTING ACCEPT [14:672]
:POSTROUTING ACCEPT [9:684]
:OUTPUT ACCEPT [9:684]
COMMIT

save this file and exit the editor

(6) install the safety net into cron temporarily
    edit /etc/crontab (in whatever editor you use)
    add the following line at the bottom
0,15,30,45 * * * *  root /sbin/iptables-restore < /root/firewall_reset

(7) create the main firewall rules (this is a little sloppy by iptables developers standards, but I'm also
    learning how to do this alot more efficiently, so if I really get a tight firewall ruleset, I'll update this)
    - however, i tested this on my own servers, and it _does_ work)
    create a new file called primary_firewall in /root (in whatever editor you use)
    add all of the following
# Network Address Translation
*nat
:PREROUTING ACCEPT [127173:7033011]
:POSTROUTING ACCEPT [31583:2332178]
:OUTPUT ACCEPT [32021:2375633]
COMMIT

# Mangle (drop unwanted packets, and make the portscanners work for it)
*mangle
:PREROUTING ACCEPT [444:43563]
:INPUT ACCEPT [444:43563]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [402: 44198]
:POSTROUTING ACCEPT [402:144198]
-A PREROUTING -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,PSH,URG -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG NONE -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags SYN,RST SYN,RST -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags FIN,SYN FIN,SYN -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,PSH,URG -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG NONE -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags SYN,RST SYN,RST -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags FIN,SYN FIN,SYN -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,PSH,URG -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG NONE -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags SYN,RST SYN,RST -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags FIN,SYN FIN,SYN -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,PSH,URG -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG NONE -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags SYN,RST SYN,RST -j DROP
-A PREROUTING -p tcp -m tcp --tcp-flags FIN,SYN FIN,SYN -j DROP
COMMIT

# Filter (intially drop all packets, then selectively open ports and enable logging of dropped requests)
*filter
:INPUT DROP [1:242]
:FORWARD DROP [0:0]
:OUTPUT DROP [0:0]
:LOG_DROP - [0:0]
:LOG_ACCEPT - [0:0]
:icmp_packets - [0:0]

# INPUT rules (incoming requests)
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -p tcp -m tcp --dport 20 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 21 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 25 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 43 -j ACCEPT
-A INPUT -p udp -m udp --dport 53 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 110 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 143 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 443 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 783 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 993 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 3306 -j ACCEPT
-A INPUT -s 127.0.0.1 -j ACCEPT
-A INPUT -p icmp -j icmp_packets
-A INPUT -j LOG_DROP

# OUTPUT rules (outgoing traffic)
-A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 20 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 21 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 22 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 25 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 43 -j ACCEPT
-A OUTPUT -p udp -m udp --dport 53 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 80 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 110 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 143 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 443 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 783 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 993 -j ACCEPT
-A OUTPUT -p tcp -m tcp --dport 3306 -j ACCEPT
-A OUTPUT -s 127.0.0.1 -j ACCEPT
-A OUTPUT -p icmp -j icmp_packets
-A OUTPUT -j LOG_DROP

# Log dropped requests and accepted requests
-A LOG_DROP -j LOG --log-prefix "[IPTABLES DROP]: " --log-tcp-options --log-ip-options
-A LOG_DROP -j DROP
-A LOG_ACCEPT -j LOG --log-prefix "[IPTABLES ACCEPT]: " --log-tcp-options --log-ip-options
-A LOG_ACCEPT -j ACCEPT

# ICMP requests (drop them all except ourselves)
-A icmp_packets -p icmp -m icmp --icmp-type 0 -j ACCEPT
# MAKE SURE THE FOLLOWING LINE HAS YOUR IP ADDRESS, PLEASE!!!!! (DON'T USE 1.2.3.4)
-A icmp_packets -s 1.2.3.4 -p icmp -m icmp --icmp-type 8 -j ACCEPT
-A icmp_packets -p icmp -m icmp --icmp-type 8 -j DROP
-A icmp_packets -p icmp -m icmp --icmp-type 3 -j ACCEPT
-A icmp_packets -p icmp -m icmp --icmp-type 11 -j ACCEPT
COMMIT

save the file and exit the editor

(8) import the rules into the firewall
    type the following:
[COLOR="Magenta"]iptables-restore < /root/primary_firewall[/COLOR]

If you don't get errors, the rulesets are active..

(9) type the following
[COLOR="Magenta"]iptables -L[/COLOR]

you should get the following output (or something very close to it)

Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp-data
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:whois
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:pop3
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:imap2
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:spamd
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:imaps
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:mysql
ACCEPT     all  --  localhost.localdomain  anywhere
icmp_packets  icmp --  anywhere             anywhere
LOG_DROP   all  --  anywhere             anywhere

Chain FORWARD (policy DROP)
target     prot opt source               destination

Chain LOG_ACCEPT (0 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere            LOG level warning tcp-options ip-options prefix `[IPTABLES ACCEPT]: '
ACCEPT     all  --  anywhere             anywhere

Chain LOG_DROP (2 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere            LOG level warning tcp-options ip-options prefix `[IPTABLES DROP]: '
DROP       all  --  anywhere             anywhere

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp-data
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:whois
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:pop3
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:imap2
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:spamd
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:imaps
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:mysql
ACCEPT     all  --  localhost.localdomain  anywhere
icmp_packets  icmp --  anywhere             anywhere
LOG_DROP   all  --  anywhere             anywhere

Chain icmp_packets (2 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere            icmp echo-reply
ACCEPT     icmp --  mgjventures.mgjventures.com  anywhere            icmp echo-request
DROP       icmp --  anywhere             anywhere            icmp echo-request
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded

(10) Type the following at the commandline
[COLOR="Magenta"]apt-get nmap[/COLOR]

If you got this far, Congratulations! you now have a basic, working firewall on your Ubuntu server
You should be able to test this out with:
ssh valid_user@your_ip_address (should work), 
ping your_ip_address (should fail), 
ftp (should work), 
nmap your_ip_address (should fail).

That's it... Enjoy!

---

