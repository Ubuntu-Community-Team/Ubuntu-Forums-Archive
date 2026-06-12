---
title: "How do you use OpenVPN in Ubuntu 12.10?"
date: 2013-03-08
forum: New to Ubuntu
---

### Post by TheManno1 on 2013-03-08
There are tutorials for 12.04 but not 12.10?

---

### Post by fantab on 2013-03-09
The tutorial for 12.04 will apply to 12.10 as well. In case there are any issues get back here and we'll help you figure 'em out.

---

### Post by TheManno1 on 2013-03-12
Error: Bridge-utils does not seem to be installed.
gadmin-openvpn-server version 0.1.5-3.1

---

### Post by fantab on 2013-03-12
Are you using this on Server or Desktop?

---

### Post by TheManno1 on 2013-03-12
> **fantab said:**
> Are you using this on Server or Desktop?

john@john:~$ lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 12.10
Release:    12.10
Codename:    quantal

---

### Post by TheManno1 on 2013-03-13
[https://www.youtube.com/watch?v=HuzLjR-1pgE](https://www.youtube.com/watch?v=HuzLjR-1pgE)
Ok, for those of you who are new to linux. DO NOT, I repeat, DO NOT  "chmod 777" any folder, especially a system folder. he really should  have suggested "sudo cp -r ~/Downloads/BHMS1VPN/ /etc/openvpn/". It'll  actually do what he wanted without running into rights-management  probplems because sudo&#65279; temporarally gives the user root administrative  rights for the fallowing command. I'm sure he's new. I don't mean to put  him down, but please never chmod 777. It gives everyone access to the  folder.

Is it safe to chmod 777
I have gadmin-openvpn-client is a fast and easy to use GTK+ administration tool for
the OpenVPN client.
And gadmin-openvpn-server is a fast and easy to use GTK+ administration tool for
the OpenVPN server.
Whats the difference between the 2

---

### Post by TheManno1 on 2013-03-14
Bump 


[LIST]
[*]john@john:~$ lsb_release -a
[*]
[*]**LSB Version:     core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch**
[*]
[*]Distributor ID: **   Ubuntu**
[*]
[*]Description: **   Ubuntu 12.10**
[*]
[*]Release:**    12.10**
[*]
[*]Codename:**    quantal**
[/LIST]
 [B]
Is it safe to chmod 777[/B]?
I have **gadmin-openvpn-client** is a fast and easy to use GTK+ administration tool for
the** OpenVPN** client.
And **gadmin-openvpn-server **is a fast and easy to use GTK+ administration tool for
the** OpenVPN** server.
Whats the difference between the 2?Which one am I suppose to use or do I need both?

---

### Post by fantab on 2013-03-14
Change Mode or chmod 777 makes a file read, write and execute, AFAIK. It is generally safe, unless you don't know what the file is and you don't want to make such file an executable.

openvpn-client is for Desktop and openvpn-server is for server. 

For openvpn to work you need two files in your /etc/openvpn:
1. client.conf
2. cacrt (certificate)

---

