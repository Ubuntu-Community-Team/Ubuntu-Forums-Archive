---
title: "apt-get troubles"
date: 2006-06-19
forum: Repositories &amp; Backports
---

### Post by Madnashua on 2006-06-19
I've just changed my install from dapper desktop to dapper server (lamp). When I was using desktop edition I used a sources.list from the ubuntu wiki:

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

but after editing my sources.list I get an odd error when trying to update - 'Errhttp://archive.ubuntu.com dapper Release.gpg Temporary failure resolving áarchive.ubuntu.comá' (odd part being the á characters)

I've checked my sources.list (with vi) repeatedly but can't find the á characters anywhere.

I use putty and ssh to access my linux box if this makes any difference??

I'm somewhat of a linux n00b so any help would be much appreciated!

---

### Post by mjm115 on 2006-06-19
Can you paste your sources.list please?

---

### Post by Madnashua on 2006-06-19
How do I do this from the command line?

---

### Post by aysiu on 2006-06-19
```
cat /etc/apt/sources.list
```

---

### Post by Madnashua on 2006-06-19
## Add comments (##) in front of any line to remove it from being checked.

##deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
##deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
##deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
##deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
##deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
##deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
##deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
##deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
##deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
##deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free

---

### Post by mjm115 on 2006-06-20
This is very interesting.  I pasted your source.list into a temporary one and it worked fine.  Have you tried recreating your sources.list?  You said that you got the error after editing your file?  What did you change?

---

### Post by Madnashua on 2006-06-20
I've managed to fix the original problem - I edited my /etc/resolv.conf to contain the correct dns servers. But then I was still receiving timeout errors. I managed to overcome this by switching to a dhcp assigned ip (use static normally) although this is a less than elegant solution for me. I can still access the internet (through firefox) normally on either static or dhcp.

my interfaces:
auto eth0
iface eth0 inet dhcp
address 192.168.0.25
netmask 255.255.255.0
gateway 192.168.0.1

any ideas anyone?

---

