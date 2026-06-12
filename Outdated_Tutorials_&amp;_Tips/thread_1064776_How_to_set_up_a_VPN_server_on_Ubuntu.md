---
title: "How to set up a VPN server on Ubuntu"
date: 2009-02-09
forum: Outdated Tutorials &amp; Tips
---

### Post by cviorel on 2009-02-09
Hi there!
For those of you who need to set up a VPN server, I wrote a long-small step-by-step guide.


Install PoPToP Point to Point Tunneling Server:
```
sudo apt-get install pptpd
```

Edit */etc/pptpd.conf* file:
```
sudo joe /etc/pptpd.conf
```

Uncomment the following lines (replace IP range if you like)
```

localip 192.168.0.1
remoteip 192.168.1.1-255

```
Save and exit.

Edit */etc/ppp/pptpd-options* file
```
sudo joe /etc/ppp/pptpd-options
```
Make sure you have this:
```

refuse-pap
refuse-chap
refuse-mschap
require-mschap-v2
require-mppe-128
proxyarp
nodefaultroute
lock
nobsdcomp
noipx              ## you don't need IPX
mtu 1490           ## may help your linux client from disconnecting
mru 1490           ## may help your linux client from disconnecting

```
Save and exit.

Next step is to add users who can use this connection.
```
sudo joe /etc/ppp/chap-secrets
```
The file should look like this:
```

# Secrets for authentication using CHAP
# client           server      secret                    IP addresses
cviorel            pptpd       my_secret_password        *
another_user       pptpd       his_secret_password       *

```
Now we need to configure IP Masquerading on the VPN server.
The purpose of IP Masquerading is to allow machines with private, non-routable IP addresses on your network to access the Internet through the machine doing the masquerading.

**ufw Masquerading**
IP Masquerading can be achieved using custom ufw rules. This is possible because the current back-end for ufw is **iptables-restore** with the rules files located in */etc/ufw/*.rules*. These files are a great place to add legacy iptables rules used without ufw, and rules that are more network gateway or bridge related.
The rules are split into two different files, rules that should be executed before ufw command line rules, and rules that are executed after ufw command line rules.

a) First, packet forwarding needs to be enabled in ufw. Two configuration files will need to be adjusted, in */etc/default/ufw* change the *DEFAULT_FORWARD_POLICY* to *&#8220;ACCEPT&#8221;*: 
```
DEFAULT_FORWARD_POLICY="ACCEPT"
```
 Then edit */etc/ufw/sysctl.conf* and uncomment:
```
net.ipv4.ip_forward=1
```
 Similarly, for IPv6 forwarding uncomment:
```
net.ipv6.conf.default.forwarding=1
```

b) Now we will add rules to the */etc/ufw/before.rules* file. The default rules only configure the *filter*  table, and to enable masquerading the nat table will need to be configured. Add the following to the top of the file just after the header comments:
```

# nat Table rules
*nat
:POSTROUTING ACCEPT [0:0]

# Forward traffic from eth1 through eth0.
-A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE

# don't delete the 'COMMIT' line or these nat table rules won't be processed
COMMIT

```

The comments are not strictly necessary, but it is considered good practice to document your configuration. Also, when modifying any of the *rules* files in */etc/ufw*, make sure these lines are the last line for each table modified:
```

# don't delete the 'COMMIT' line or these rules won't be processed
COMMIT

```

c) Finally, disable and re-enable ufw to apply the changes:
```
sudo ufw disable && sudo ufw enable
```

IP Masquerading should now be enabled. You can also add any additional FORWARD rules to the */etc/ufw/before.rules*. It is recommended that these additional rules be 
added to the *ufw-before-forward* chain. 

**iptables Masquerading**
iptables can also be used to enable masquerading.
a) Similar to ufw, the first step is to enable IPv4 packet forwarding by editing */etc/sysctl.conf* and uncomment the following line:
```
net.ipv4.ip_forward=1
```
 If you wish to enable IPv6 forwarding also uncomment:
```
net.ipv6.conf.default.forwarding=1
```
-  Next, execute the sysctl command to enable the new settings in the configuration file:
```
sudo sysctl -p
```
- IP Masquerading can now be accomplished with a single iptables rule, which may differ slightly based on your network configuration:
```
sudo iptables -t nat -A POSTROUTING -s 192.168.0.0/16 -o ppp0 -j MASQUERADE
```
The above command assumes that your private address space is 192.168.0.0/16 and that your Internet-facing device is ppp0. The syntax is broken down as follows:
[LIST]
  [*]-t nat -- the rule is to go into the nat table
  [*]-A POSTROUTING -- the rule is to be appended (-A) to the POSTROUTING chain
  [*]-s 192.168.0.0/16 -- the rule applies to traffic originating from the specified address space
  [*]-o ppp0 -- the rule applies to traffic scheduled to be routed through the specified network device
  [*]-j MASQUERADE -- traffic matching this rule is to "jump" (-j) to the MASQUERADE target to be manipulated as described above
[/LIST]
b) Also, each chain in the filter table (the default table, and where most or all packet filtering occurs) has a default policy of ACCEPT, but if you are creating a firewall in addition to a gateway device, you may have set the policies to DROP or REJECT, in which case your masqueraded traffic needs to be allowed through the FORWARD chain for the above rule to work:
```

sudo iptables -A FORWARD -s 192.168.0.0/16 -o ppp0 -j ACCEPT
sudo iptables -A FORWARD -d 192.168.0.0/16 -m state --state ESTABLISHED,RELATED -i ppp0 -j ACCEPT

```
The above commands will allow all connections from your local network to the Internet and all traffic related to those connections to return to the machine that initiated them.

c) If you want masquerading to be enabled on reboot, which you probably do, edit */etc/rc.local* and add any commands used above. For example add the first command with no filtering:
```
iptables -t nat -A POSTROUTING -s 192.168.0.0/16 -o ppp0 -j MASQUERADE
```

**Logs**
Firewall logs are essential for recognizing attacks, troubleshooting your firewall rules, and noticing unusual activity on your network. You must include logging rules in your firewall for them to be generated, though, and logging rules must come before any applicable terminating rule (a rule with a target that decides the fate of the packet, such as ACCEPT, DROP, or REJECT).

If you are using ufw, you can turn on logging by entering the following in a terminal:
```
sudo ufw logging on
```
To turn logging off in ufw, simply replace on with off in the above command.
If using iptables instead of ufw, enter:
```
sudo iptables -A INPUT -m state --state NEW -p tcp --dport 80 -j LOG --log-prefix "NEW_HTTP_CONN: "
```

A request on port 80 from the local machine, then, would generate a log in dmesg that looks like this:
```

[4304885.870000] NEW_HTTP_CONN: IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=58288 DF PROTO=TCP SPT=53981 DPT=80 WINDOW=32767 RES=0x00 SYN URGP=0

```

The above log will also appear in */var/log/messages*, */var/log/syslog*, and */var/log/kern.log*. This behavior can be modified by editing */etc/syslog.conf*  appropriately or by installing and configuring **ulogd** and using the ULOG target instead of LOG. The ulogd  daemon is a userspace server that listens for logging instructions from the kernel specifically for firewalls, and can log to any file you like, or even to a PostgreSQL or MySQL  database. Making sense of your firewall logs can be simplified by using a log analyzing tool such as **fwanalog**, **fwlogwatch** or **lire**.

NOTE: Documentation for this article is taken from [https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html).

---

### Post by dmizer on 2009-02-09
Would you please add this howto (not a link to your site, but the actual text of the howto) to the Tutorials and tips section?

For the time being, I am moving this post to the servers section of the forums. Great work.

---

### Post by cviorel on 2009-02-10
> **dmizer said:**
> Would you please add this howto (not a link to your site, but the actual text of the howto) to the Tutorials and tips section?

For the time being, I am moving this post to the servers section of the forums. Great work.

Sorry about that!
Removed the link, posted the actual guide. You may move it to the proper section.
Take care!

---

### Post by dmizer on 2009-02-10
> **cviorel said:**
> Sorry about that!
Removed the link, posted the actual guide. You may move it to the proper section.
Take care!

Done!

Just thought the guide was too good for the servers section. Thanks for this. :)

---

### Post by HyperHacker on 2009-03-27
I followed this guide on my desktop and now my laptop can no longer connect to it through SSH, even when it's on the same network. The connection times out. I can ping it, but not connect.

Also the Configure VPN window has a Gateway field. What do I put in there?

---

### Post by xurwxj on 2009-06-05
is there any tips or guide for pptpd intergrate with openldap?
thx

---

### Post by cheddercaveman on 2009-06-17
> **HyperHacker said:**
> I followed this guide on my desktop and now my laptop can no longer connect to it through SSH, even when it's on the same network. The connection times out. I can ping it, but not connect.

Also the Configure VPN window has a Gateway field. What do I put in there?

I am now too experiencing this problem, anyone going to come along and give some insight into this.  Just for additional help I went the ufw masquarade route with mine and it stayed connected to ssh while I made the update, but once I disconnected and now tried to reconnect I've got nothing.  Please provide some insight into this.  Thanks.

---

### Post by houseonfire on 2009-06-17
Great guide. I'm using this for college.

Are ports going to be a problem? Or can 80 be used?

---

### Post by Meph1st0 on 2009-07-11
All kinds of questions:

Do I need to do any port forwarding on my router?  What port does this use?

Do I need to choose between ufw masquerading or iptables masquerading?  Do I need to do both?  Which is better?

If used,
```
localip 192.168.0.1
remoteip 192.168.1.20-30

```
in the /etc/pptpd.conf file do I also need to adjust the 
```
# Forward traffic from eth1 through eth0.
-A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE
```
line in the /etc/ufw/before.rules file?

How do I add the rules to the ufw-before-forward chain?  I don't see a file with that name.

---

### Post by cviorel on 2009-10-17
Of course, you have to do masquerading.

---

### Post by devliljohn on 2009-11-19
I still cant get Masquerading to work with ufw. i noticed something interesting:
for ufw you say to add this to the nat table:
-A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE

but for iptables you say to add this rule to the nat table:
-A POSTROUTING -s 192.168.0.0/16 -o ppp0 -j MASQUERADE

why are these different? i tried both configurations in my /etc/ufw/before.rules file and neither of them work. what am i missing? i am desperately trying to get this working asap for a project for work.

---

### Post by devliljohn on 2009-11-19
> **devliljohn said:**
> I still cant get Masquerading to work with ufw. i noticed something interesting:
for ufw you say to add this to the nat table:
-A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE

but for iptables you say to add this rule to the nat table:
-A POSTROUTING -s 192.168.0.0/16 -o ppp0 -j MASQUERADE

why are these different? i tried both configurations in my /etc/ufw/before.rules file and neither of them work. what am i missing? i am desperately trying to get this working asap for a project for work.

ok after fooling around with this on and off for 2 days i figured out the issue with ufw ip masq is that he has specified the wrong subnetmask:
192.168.0.0/24    will not work because it will not route the 192.168.1.1-255 client addesses so you have to use :
192.168.0.0/16

---

### Post by spezticle on 2010-06-28
why pptpd and not openvpn? just curious...

---

### Post by saeed144 on 2011-08-01
I have set up PPTP VPN server on ubuntu.
But accounts are open for concurrent simultaneous connections. means there can be many users using one account at the time.
i need to limit that to one user at the time.
anybody knows how it can be done?

---

