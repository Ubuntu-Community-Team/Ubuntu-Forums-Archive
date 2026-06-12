---
title: "Safest way to run a web server?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Twizzle on 2008-05-28
I am setting up a home server which I will use for backups, streaming video to my media PC and hopefully as an email server once I figure it all out. I would also like to run a web server on it so family and possibly a few friends can view my photos and I can check my emails.

As this will be a web facing part of the box, I was wondering how the best and most secure way would be to set it up as the box contains backups etc.

I have been considering running a virtual machine for the web part as I figure that if someone hacked in they would not be able to see my backup data etc.

Am I right in thinking this or is it overkill for such a small part of my sever?

---

### Post by lisati on 2008-05-28
I'm not sure of all the details (it depends in part on the setup you have), but sometimes a router can be configured to help provide firewall activities and give permissions to specific requests. You'll probably want to look into protection against DOS. 

[http://www.spamcop.net/fom-serve/cache/329.html]("http://www.spamcop.net/fom-serve/cache/329.html") has some food for thought about configuring mailserves - you want to consider what kind of policy you'll have for dealing with SPAM.

---

### Post by superprash2003 on 2008-05-28
the virtual webserver idea is quite good.. you could go ahead with that..but you need a powerful system for that..

---

### Post by tigerplug on 2008-05-28
> **Twizzle said:**
> I am setting up a home server which I will use for backups, streaming video to my media PC and hopefully as an email server once I figure it all out. I would also like to run a web server on it so family and possibly a few friends can view my photos and I can check my emails.

As this will be a web facing part of the box, I was wondering how the best and most secure way would be to set it up as the box contains backups etc.

I have been considering running a virtual machine for the web part as I figure that if someone hacked in they would not be able to see my backup data etc.

Am I right in thinking this or is it overkill for such a small part of my sever?


You could use apache with a Virtual directory - security is always going to be an issue with a webserver on your home connection. You just need to be smart about it.

Check these out:
**Setup of Apache web server (SSL-capable), Postfix mail server with SMTP-AUTH and TLS, BIND DNS server, Proftpd FTP server, MySQL server, Courier POP3/IMAP, Quota, Firewall, etc.**
[http://howtoforge.com/perfect-server-ubuntu8.04-lts](http://howtoforge.com/perfect-server-ubuntu8.04-lts)

**Virtual Hosts in Apache - Using specified directories:**

[http://articles.slicehost.com/2008/4/25/ubuntu-hardy-installing-apache-and-php5](http://articles.slicehost.com/2008/4/25/ubuntu-hardy-installing-apache-and-php5)
[http://articles.slicehost.com/2008/4/28/ubuntu-hardy-apache-config-layout](http://articles.slicehost.com/2008/4/28/ubuntu-hardy-apache-config-layout)
[http://articles.slicehost.com/2008/4/28/ubuntu-hardy-apache-configuration-1](http://articles.slicehost.com/2008/4/28/ubuntu-hardy-apache-configuration-1)
[http://articles.slicehost.com/2008/4/28/ubuntu-hardy-apache-configuration-2](http://articles.slicehost.com/2008/4/28/ubuntu-hardy-apache-configuration-2)
[http://articles.slicehost.com/2008/4/29/ubuntu-hardy-apache-virtual-hosts-1http://articles.slicehost.com/2008/4/29/ubuntu-hardy-apache-virtual-hosts-2](http://articles.slicehost.com/2008/4/29/ubuntu-hardy-apache-virtual-hosts-1http://articles.slicehost.com/2008/4/29/ubuntu-hardy-apache-virtual-hosts-2)

**DynDNS - If you have a dynamic IP address.**
[http://www.dyndns.com/](http://www.dyndns.com/)

**You'll also need this is you want to map that to a domain name:**
[http://www.easydns.com/](http://www.easydns.com/)


Its pretty easy to do. :)


> **superprash2003 said:**
> the virtual webserver idea is quite good.. you could go ahead with that..but you need a powerful system for that..


Virtual as in VMware or as in Hosts?

---

### Post by Twizzle on 2008-05-28
Cool thanks for all that :) Guess Ill be doing some reading and research.

I currently have a cable connection into a Linksys router and then onto one server, a media PC and an office PC. The server is running 8.04 (desktop version cos i still like my GUI :) when I shh or vnc into it ). I aways worry that my router is not enough to keep people out though especially if I open it up as a web server.

When you say powerfull for a virtual server, it is an Athlon XP2400 (underclocked to 1800 to stay cooler) with 1Gb RAM - is that enough for a virtual server of this type?

Also in realtion to Apache and virtual folders, I assume thay would mean any hacker would only see the contents of that folder and **could not** get round it?

I worry that someone could hack in and just delete all my backup files etc and I assume the web site part would be the weak link.

Off to read some of those links now.. thanks again

---

### Post by tigerplug on 2008-05-28
No problem. Read and you will learn ;)

Just be sure to take your time and don't overlook the security side of things.
Learn more about portforwarding, NAT, UPNP, Triggering etc...  it helps in the long run.

Try to learn about the Apache config files, what they do and why.


Good luck!


:)

---

