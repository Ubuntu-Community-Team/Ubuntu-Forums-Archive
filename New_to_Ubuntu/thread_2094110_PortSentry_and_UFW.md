---
title: "PortSentry and UFW"
date: 2012-12-12
forum: New to Ubuntu
---

### Post by ACagliano on 2012-12-12
As you probably know, the firewall in Ubuntu is ufw. Now, I wanted to edit my PortSentry configuration file, so that if it is triggered, it passes a deny rule to ufw. The following is the text of the KILL_ROUTE command that PortSentry runs if it is triggered.

KILL_ROUTE="ufw deny from $TARGET"

Is that ok? Portsentry runs as root.

---

### Post by chadk5utc on 2012-12-13
Hello
Actually UFW is the firewall interface for iptables which comes with Ubuntu 
heres a link for port sentry > [http://manpages.ubuntu.com/manpages/lucid/man8/portsentry.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/portsentry.8.html)
This gives more examples of how to use it properly. What is it that your trying to do?

---

### Post by ACagliano on 2012-12-14
> **chadk5utc said:**
> Hello
Actually UFW is the firewall interface for iptables which comes with Ubuntu 
heres a link for port sentry 
This gives more examples of how to use it properly. What is it that your trying to do?

PortSentry is port-scan detection daemon that, when it detects a port scan, blocks the scan, reverse DNS's the IP address of the scanning host, and then should pass a rule to the firewall. This command follows the exact same structure to pass a rule to your firewall on the command line, as here:

KILL_ROUTE= " insert rule to pass to firewall "

So the text in those quotes is the command as you would pass it on the command line. I have PortSentry up and running perfectly fine. I'm just curious what to put in those quotes.

---

### Post by haqking on 2012-12-14
> **ACagliano said:**
> PortSentry is port-scan detection daemon that, when it detects a port scan, blocks the scan, reverse DNS's the IP address of the scanning host, and then should pass a rule to the firewall. This command follows the exact same structure to pass a rule to your firewall on the command line, as here:

KILL_ROUTE= " insert rule to pass to firewall "

So the text in those quotes is the command as you would pass it on the command line. I have PortSentry up and running perfectly fine. I'm just curious what to put in those quotes.

Does your Ubuntu machine have a WAN IP Address ? because if not then it wont get port scanned anyways, your router will which most deny portscans anyway.

Or are you worried about people on your LAN scanning your ports ?

And as stated UFW is not a firewall it is merely a interface to the Linux kernel firewall which is Netfilter/IPTables

---

### Post by ACagliano on 2012-12-14
No. It has a local IP address, and is behind a modem and router, both of which are firewalled as well. PortSentry is merely an additional precaution because I do use Ubuntu as a hacking distro.

---

### Post by haqking on 2012-12-14
> **ACagliano said:**
> No. It has a local IP address, and is behind a modem and router, both of which are firewalled as well. PortSentry is merely an additional precaution because I do use Ubuntu as a hacking distro.

If you are behind a router using a local IP address then it is likely you are using NAT, how do you expect someone to port scan your local IP ?

You use Ubuntu as a hacking distro ? LOL what does that mean ? Feel free to explain, it wont go over my head ;-)

---

### Post by ACagliano on 2012-12-14
I legitimate hacker can get to you if he wants to, no matter what configuration you are hiding behind.

I am in the internet security field and I fall under the category "ethical hacker" which means I know how to hack, but I choose not to use it for bad things.

I dual boot Mac OS X and Ubuntu. I use Ubuntu for hacking because I can get its firewalls up tighter and there are alot more tools for Linux OS's than for OS X (I mean you can theoretically get them set up on OS X, but its more of a hassle).

---

### Post by haqking on 2012-12-14
> **ACagliano said:**
> I legitimate hacker can get to you if he wants to, no matter what configuration you are hiding behind.

I am in the internet security field and I fall under the category "ethical hacker" which means I know how to hack, but I choose not to use it for bad things.

I dual boot Mac OS X and Ubuntu. I use Ubuntu for hacking because I can get its firewalls up tighter and there are alot more tools for Linux OS's than for OS X (I mean you can theoretically get them set up on OS X, but its more of a hassle).

ahhh i see, i'm enlightened ;-)

yet you thought that UFW is a firewall and "the" firewall for Ubuntu, and you would use it to get things "tight" instead of IPTables directly ?

Could you explain to me how you would get to port scan my local machine through my WAN address ? I am familiar with Firewalking, router exploitation etc so feel free to get in depth for my clarity

---

### Post by ACagliano on 2012-12-14
Haha. Easy there. I'm still learning. I'm not an expert yet. 

I know ufw is a front end for iptables, but I just called it a firewall for simplicity's sake.

The most I've done is bluejacking and minor scripting of DOS attacks. I haven't yet had any practice with breaking into routers. Most of my experience falls on the other end...preventing attacks and what not. Next year, I'll be learning the good stuff ;)

---

### Post by haqking on 2012-12-14
> **ACagliano said:**
> Haha. Easy there. I'm still learning. I'm not an expert yet. 

I know ufw is a front end for iptables, but I just called it a firewall for simplicity's sake.

The most I've done is bluejacking and minor scripting of DOS attacks. I haven't yet had any practice with breaking into routers. Most of my experience falls on the other end...preventing attacks and what not. Next year, I'll be learning the good stuff ;)

ahh ok, no worries.

;-)

Peace

---

