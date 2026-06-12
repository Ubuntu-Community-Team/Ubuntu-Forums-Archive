---
title: "minor problem in terminal"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by knoc on 2008-09-03
recently, using sudo command in terminal I've been getting this result

knoc@knoc-laptop:~$ sudo aptitude update
**sudo: unable to resolve host knoc-laptop**
[sudo] password for knoc: 
Get:1 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B] 

...and so on and so forth

I just suddenly started getting the "sudo: unable to resolve host knoc-laptop"

why is this? and what can I do to get rid of it? I'm sure it was some stupid mistake I made. Any help is appreciated. Thanks in advance :)

---

### Post by Ryadt on 2008-09-03
Can you post the output of:```
cat /etc/hosts
```

---

### Post by knoc on 2008-09-03
knoc@knoc-laptop:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 knoc-laptop.MAIN

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by knoc on 2008-09-03
I went into my network settings host list and deleted 

127.0.1.1 knoc-laptop.MAIN 

and the problem was solved. Thanks for pointing me in the right direction. I think I was trying to join a windows workgroup earlier where I made the mistake. I'm installing samba at the moment to get that straightened out.

---

### Post by iaculallad on 2008-09-03
> **knoc said:**
> knoc@knoc-laptop:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 knoc-laptop.MAIN

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

On your terminal:

```
gksudo gedit /etc/hosts
```

and remove the .MAIN from this line:

```
127.0.1.1 knoc-laptop.MAIN
```

so that it would just be:

```
127.0.1.1 knoc-laptop
```

Save and Close file. Then:

```
sudo apt-get update && sudo apt-get upgrade
```

EDIT: Disregard, Problem had been resolved by the OP

---

### Post by Ryadt on 2008-09-03
> **knoc said:**
> knoc@knoc-laptop:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 knoc-laptop.MAIN

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Try ```
gksudo gedit /etc/hosts
```
then change it to look like this```
127.0.0.1 localhost
127.0.1.1 **knoc-laptop**

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by Malac on 2008-09-03
> **knoc said:**
> knoc@knoc-laptop:~$ cat /etc/hosts
127.0.0.1 localhost
**127.0.1.1 knoc-laptop knoc-laptop.MAIN**
 
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
change it to this and it will work for the work group or normal access.
This is a known bug in network admin app

---

