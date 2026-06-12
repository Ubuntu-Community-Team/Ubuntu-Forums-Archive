---
title: "what's this lease {andare.swiftmedia.com} thing in my dhchlient.conf?"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by hanzj on 2008-05-16
Hi, below is my dhclient.conf file. 
Why do I have a part on "lease"? What is that lease part all about? Is it safe to delete the whole lease { foo foo foo } part?



```
# Configuration file for /sbin/dhclient, which is included in Debian's
#    dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#    man page for more information about the syntax of this file
#    and a more comprehensive list of the parameters understood by
#    dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#    not leave anything out (like the domain name, for example), then
#    few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, host-name,
    netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
[COLOR=Red]#  option host-name "andare.swiftmedia.com";[/COLOR]
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
```

---

### Post by Golem XIV on 2008-05-16
You are "leasing" an IP address from a DHCP server.  This is standard procedure with most ISPs.

andare.swiftmedia.com would be the name of the DHCP server.

---

### Post by hanzj on 2008-05-17
but if you go to andare.swiftmedia.com, you'll see it's just a parked page. what's that all about?


Also, doesn't the" #" symbol at the start of a line in the conf file mean that it's actually just "parenthetical" comment?

---

### Post by infamousjeff on 2013-02-23
> **hanzj said:**
> but if you go to andare.swiftmedia.com, you'll see it's just a parked page. what's that all about?


Also, doesn't the" #" symbol at the start of a line in the conf file mean that it's actually just "parenthetical" comment?

Anyone figure this out?! I got same thing on windows or Linux.

---

### Post by QIII on 2013-02-23
Thank you for sharing.  Everyone’s questions and answers are valuable.

If a thread has had no activity for about a year or more, it is best to start a new thread of your own. Not only will you be more likely to get a response, but things change so quickly in the software world that an old thread may cause you more trouble than it will help due to outdated information.

Please feel free to add a link to this thread in the new one you start.

Best wishes!

*Thread** closed.***

---

