---
title: "Sudo problems"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by huwaw69 on 2008-11-20
I use terminal sometimes it works perfectly fine until now...
I don't know what i have done wrong or something
it displays this:
sudo: unable to resolve host ubuntu

The ouput of
cat: /etc/hosts
huwaw69@ubuntu:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 ubuntu.ubuntu-domain ubuntu.smartbro.net

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

what should i do?

---

### Post by huwaw69 on 2008-11-20
I'm using ubuntu 8.10 Ibex

---

### Post by taurus on 2008-11-20
What does /etc/hostname look like?

```
cat /etc/hostname
```
The name in /etc/hostname should be matching up with the one in /etc/hosts.

---

### Post by huwaw69 on 2008-11-20
root@ubuntu:/home/huwaw69# cat /etc/hostname
ubuntu

---

### Post by Kevbert on 2008-11-20
You need to edit the hosts file using
```
gksudo gedit /etc/hosts
```
You need to change
```
127.0.1.1 ubuntu.ubuntu-domain ubuntu.smartbro.net
```
to
```
127.0.1.1 ubuntu
```

---

### Post by taurus on 2008-11-20
Your /etc/hostname should be **ubuntu.smartbro.net** since that is the one you have in /etc/hosts.

---

### Post by huwaw69 on 2008-11-20
It's now solved! Thanks...
:guitar:

---

