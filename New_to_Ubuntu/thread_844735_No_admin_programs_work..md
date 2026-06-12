---
title: "No admin programs work."
date: 2008-06-29
forum: New to Ubuntu
---

### Post by ethanklein on 2008-06-29
Trying to install anything in terminal I get this.

sudo: unable to resolve host ux9a
what does that mean?

I have no access to add/remove programs.

Ubuntu 8.04

---

### Post by ethanklein on 2008-06-29
I just tried sudo apt-get update

sudo: unable to resolve host ux9a
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release

Anyone know what his thing is? sudo: unable to resolve host ux9a

---

### Post by iaculallad on 2008-06-29
Post the output of the terminal command below:

```
cat /etc/hosts
```

---

### Post by kuja on 2008-06-29
Unable to resolve host is generally a DNS issue ... often temporary. It means that you couldn't resolve the URL to an IP Address.

---

### Post by neurostu on 2008-06-29
Did you edit:
```

/etc/apt/sources.list

```

---

### Post by ethanklein on 2008-06-29
An internet issue shouldnt have anything to do with why software sources, add/remove progams, wont even load.

heres what cat /ect/hosts did

 127.0.0.1 localhost
127.0.1.1 ux9a.theplace

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by ethanklein on 2008-06-29
No I havent even touched the sources list. I was thinking about it though.

---

### Post by iaculallad on 2008-06-29
> **ethanklein said:**
> An internet issue shouldnt have anything to do with why software sources, add/remove progams, wont even load.

heres what cat /ect/hosts did

 127.0.0.1 localhost
127.0.1.1 ux9a.theplace

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Edit your /etc/hosts file:

```
gksu gedit /etc/hosts
```

and replace the string **127.0.1.1 ux9a.theplace** with **127.0.1.1 ux9a**

Save and Close. 

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by ethanklein on 2008-06-29
> **iaculallad said:**
> Edit your /etc/hosts file:

```
gksu gedit /etc/hosts
```

and replace the string **127.0.1.1 ux9a.theplace** with **127.0.1.1 ux9a**

Save and Close. 

```
sudo apt-get update && sudo apt-get upgrade
```

Thank you so much! This did the trick.

---

