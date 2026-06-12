---
title: "ssh connection refused"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by RichardBruce on 2013-04-27
Hi,

I'm trying to set up my new machine so I can ssh to it. I am able to ssh over my LAN (ssh localhost and ssh 192.169.1.100 from a different machine both work), but when I try to ssh using my public ip address I get "connection refused". I have already turned off the router firewall, moved my machine to the  DMZ and turned on port forwarding. I havent set up any firewall or  anything like that on my machine (Ubuntu 13.04) so just have whatever is  there by default. I think I have a problem with port forwarding because nmap -sT 192.168.1.100 returns:
PORT   STATE SERVICE
22/tcp open  ssh
25/tcp open  smtp
80/tcp open  http

while 'nmap -sT xxx.xxx.xxx.xxx' returns
PORT   STATE SERVICE
23/tcp open  telnet
53/tcp open  domain
80/tcp open  http

Does this look like a port forwarding problem to everyone else? or perhaps you have better ideas?

---

