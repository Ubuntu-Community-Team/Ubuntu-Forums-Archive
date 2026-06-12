---
title: "E: Unable to locate package atomiadns-webapp"
date: 2014-05-05
forum: New to Ubuntu
---

### Post by Denkinhalt on 2014-05-05
Hi 

I would like to install atomiadns-webapp. 
But i get this Message:

root@dns:~# apt-get install atomiadns-webapp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package atomiadns-webapp

How can that be fixed?

Regards


System:
Ubuntu 12.04 LTS (GNU/Linux 3.2.0-23-generic-pae i686)

---

### Post by Danger_Monkey on 2014-05-05
You can search for the correct package using something like:

```

apt-cache search atomiadns-

```

You can enter any part of the word, and it will search for all of the text you enter.  "atomiadns-webapp" doesn't appear to be in the repositories, but if you google it, you will find installation instructions.

---

### Post by Denkinhalt on 2014-05-05
thanks. That was quick. :)


root@dns:~# apt-cache search atomiadns-
atomiadns-api - SOAP-server for Atomia DNS
atomiadns-client - Atomia DNS Command line client
atomiadns-database - Standalone database-package for Atomia DNS
atomiadns-dyndns - Atomia DNS DDNS server
atomiadns-masterserver - Complete master SOAP server for Atomia DNS
atomiadns-nameserver - Atomia DNS Sync application
atomiadns-powerdns-database - Standalone database-package for Atomia DNS PowerDNS nameserver agent
atomiadns-powerdnssync - Atomia DNS PowerDNS Sync application
atomiadns-zoneimport - Atomia DNS zone file importer.


atomiadns-webapp is missing. 


The installation instruction i found on the website of atomiadns:
[http://atomiadns.com/get-started/install-atomia-dns/](http://atomiadns.com/get-started/install-atomia-dns/)


Any other advise?

---

### Post by ian-weisser on 2014-05-05
Are you also asking on the atomiadns forum for this support?
It's their package, hosted on their site.
It's not in the Ubuntu repositories, and is not Ubuntu-community-supported software.
You should report his failure to atomiadns so they can fix their repository.
We will certainly try to help, but that help is limited since you you don't seem to have an Ubuntu problem, and it's not an Ubuntu package or hosted in an Ubuntu repository.

Specific help we can offer:
You can also browse the atomiadns repos. I quickly discovered the webapp package in an expected location: [http://public.apt.atomia.com/ubuntu-precise/pool/main/a/atomiadns-webapp/](http://public.apt.atomia.com/ubuntu-precise/pool/main/a/atomiadns-webapp/)
You can easily download to /var/cache/apt/archives, then it should install easily and normally using either dpkg or apt-get.

---

