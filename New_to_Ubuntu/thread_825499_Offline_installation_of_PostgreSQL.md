---
title: "Offline installation of PostgreSQL"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by rdebnath on 2008-06-11
Hi,

I have got the debian packages required to install PostgreSQL (in a USB drive) and trying installing them in my home PC.

I use the "sudo dpkg -i *" command to install. It ends up with errors...
Then I see two broken packages in my Synaptic Package Manager "ssl-cer" and "openssl-blacklist". I don't find any PostgreSQL server in the program list (as in the case of mysql).

Anybody, please tell how can I get postgres running on my ubuntu machine.

Thanks,
Rajesh

---

### Post by bdk6m2007 on 2008-06-17
> **rdebnath said:**
> 
Then I see two broken packages in my Synaptic Package Manager "ssl-cer" and "openssl-blacklist".

 
Sounds like you have dependency problems. Try doing:
 
```

apt-get update
apt-get -f install

```
 
and this should install the missing packages.
 
Of course, another (better) approach is to do:
 
```

apt-get update
apt-get install postgresql-8.3

```
 
so that you install from the ubuntu repositories (you can replace 8.3 with 8.2, 8.1, 8.0, or 7.3 if you don't want version 8.3).

---

