---
title: "Firewall to use?"
date: 2009-03-17
forum: Recurring Discussions
---

### Post by sv1cdn on 2009-03-17
Hello!
Which firewall do you recommend to use with Ubuntu 8.10?
Take care!

---

### Post by cdenley on 2009-03-17
That depends on what you are trying to accomplish. Generally, people who need to use the firewall in ubuntu configure it with UFW or GUFW. Also, generally, using a firewall in ubuntu provides little or no benefit, but it depends what servers you're running and what you want the firewall to do.

---

### Post by OrangeCrate on 2009-03-17
> **sv1cdn said:**
> Hello!
Which firewall do you recommend to use with Ubuntu 8.10?
Take care!

> By default, Ubuntu ships with no open ports on public interfaces. In other words, a "port scan" would show all closed ports, nothing open. As a result, putting up a firewall would provide no more security than not putting one up. Remember that open ports provide services that hackers can connect to, and only if they can connect to these services can they be potentially abused and exploited.

[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

Test it here:

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by hyper_ch on 2009-03-17
usually there's no need for altering your already installed firewall.

---

### Post by bodhi.zazen on 2009-03-17
> **sv1cdn said:**
> Hello!
Which firewall do you recommend to use with Ubuntu 8.10?
Take care!

These discussions tend to go in circles and if you are asking a general question like this, IMO, it is an indication you need to do some reading.

Start here :

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

and here :

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

Otherwise I am moving this to recurring discussions.

If you have a specific question, please tell us what you are wanting to use a firewall for exactly.

---

### Post by sv1cdn on 2009-03-18
Great help from all! Many thanks!
I am an IT engineer and been trained and using firewalls like NetScreen, Juniper, Fortinet. Been using Windows OS but since two years now I am an addict in Ubuntu and linux OS.
For the sake of security I am now trying to determine what should be done in Ubuntu in order to get most of security.

---

