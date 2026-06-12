---
title: "install netconfig via apt-get"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by know-it-some on 2008-08-13
Hi folks,

Was wondering what package I need to install via apt-get in order to get the netconfg command line utility.  (I prefer using netconfig instead of ifconfig.) However, when I try 

apt-get install netconfig

I get:  

E: Couldn't find package netconfig

Anyone know? Thanks!

---

### Post by insineratehymn on 2008-08-13
Howdy, couldn't find a link to a .deb for netconfig (is this a Red Hat program?), so you may have to install it using **alien**.

That is available in the repos via apt-get.
You will then have to use alien to install netconfig.

You can find the rpm here: [http://rpmseek.com/rpm-pl/netconfig.html?hl=com&cx=0::](http://rpmseek.com/rpm-pl/netconfig.html?hl=com&cx=0::)

Find the appropriate one and have fun. :)

---

### Post by know-it-some on 2008-08-13
Okay thanks for the tip.  I guess netconfig is a redhat centric thing.  I always assumed it was more or less universal since it is such a convenient ifconfig replacement that doesn't require that X be installed.  I'll just use ifconfig.  Thanks again.

---

### Post by insineratehymn on 2008-08-14
It is completely possible to install netconfig, you just need a utility like alien to install a .rpm on Debian architecture. Should be pretty straight forward if you wanna try it.

---

### Post by InfinityCircuit on 2008-08-15
If it was possible to find a source package for this I would make a .deb but I can't find the source...

EDIT: I have the source I will build a deb within the hour.

---

### Post by y@w on 2008-08-15
> **InfinityCircuit said:**
> If it was possible to find a source package for this I would make a .deb but I can't find the source...

[http://www.google.com/search?q=netconfig+.rpm&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=netconfig+.rpm&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

You can use alien to convert an .rpm to .deb package. I've done it several times and never had a problem. I have to ask... Why would you want to run netconfig on Ubuntu?? Just edit /etc/network/interfaces or you can use the GUI tools if you have GNOME installed. No need to use ifconfig.

---

### Post by InfinityCircuit on 2008-08-15
The OP seemed intent on using netconfig, so I figured that I may as well build a deb for it.  I agree that it is way outdated.

It's in my ppa (see signature).

Direct Link: [http://ppa.launchpad.net/dmoerner/ubuntu/pool/main/n/netconfig/netconfig_0.8.24-1ubuntu2_i386.deb](http://ppa.launchpad.net/dmoerner/ubuntu/pool/main/n/netconfig/netconfig_0.8.24-1ubuntu2_i386.deb)

---

### Post by Duckyspetrie on 2008-08-15
Nerds!

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

Delete. My. Account.

---

### Post by cariboo on 2008-08-15
I don't understand what you wre trying to say. :)

Jim

---

### Post by y@w on 2008-08-15
> **InfinityCircuit said:**
> The OP seemed intent on using netconfig, so I figured that I may as well build a deb for it.  I agree that it is way outdated.

It's in my ppa (see signature).

Direct Link: [http://ppa.launchpad.net/dmoerner/ubuntu/pool/main/n/netconfig/netconfig_0.8.24-1ubuntu2_i386.deb](http://ppa.launchpad.net/dmoerner/ubuntu/pool/main/n/netconfig/netconfig_0.8.24-1ubuntu2_i386.deb)

I'm just questioning the OP's intent on using it.. Seems like a hack to do something that's already built-in to the OS. :)

---

### Post by know-it-some on 2008-08-15
Excellent responses on this topic so thanks to everyone.  As it happens I have been using fedora core ever since it was redhat 8 without a gui (or even x) installed at all.  I had always used netconfig simply because it was so easy.  Now that I am on ubuntu I am certainly open to trying new methods, although once again I am building servers without X so commandline shortcuts are like gold to me.  Right now my biggest problem is getting the server to accept a port 22 connection!

(see other thread).

Thanks for the netconfig deb file!

---

