---
title: "Why can't I see my websites from within my LAN?"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by andrewjamesw on 2012-07-25
I have Ubuntu 12.04 with LAMP running. I have bought a domain name that is the same as my surname e.g. [www.examplesurname.net.nz]("http://www.examplesurname.net.nz"). I have configured DNS with multiple subdomains e.g. [www.examplefirstname.examplesurname.net.nz]("http://www.examplefirstname.examplesurname.net.nz") to point to my IP. These are for family members to use with their own websites. I set up family members as Ubuntu users and configured Apache with each family members name as a virtual host. I have opened port 80 on my router and **everything works just fine from outside my LAN**, e.g. typing in the domain (or subdomain) to a browser :-) They are mainly Wordpress sites and work great. I have a mobile internet device (ipad with 3G) which I can test them on, all OK
Here's my problem. I don't know how to access these sites from my LAN.
How do I access my (and family members) websites from within my LAN? I know i can use the local IP of the server e.g.192.168.xx.xx but that just displays the default Apache server, not the virtual servers I have created. I want to be able to sit in my nice cosy lounge in front of the fire with my laptop and build/edit sites on my server downstairs. 
I have spent ages changing router settings, but with no success. 
Has it got something to do with the fact that I am not allowed to go out from the LAN and then come back in? I've spend a lot of time trying to sort this out, this is my first post on a forum ever. Fingers crossed someone can tell me what to do.

---

### Post by cryptotheslow on 2012-07-25
I ~think~ you could put entries for the dns names pointing to the LAN IP address in your /etc/hosts file.

I believe the hosts file is queried before DNS so effectively overriding the external IP address returned via DNS.

Bear in mind that if this is on a mobile device e.g. a laptop that if you later want to access the sites externally then you will need to revert the hosts file changes - so keep a copy of the original handy.

Let us know how it goes.

---

### Post by Cheesemill on 2012-07-25
You have 2 options here.

1 - Set up an internal DNS server. Can be tricky to set up but only needs to be done once no matter how many machines you have on your LAN. This used to always be done with Bind but a newer, easier option would be Dnsmasq.
[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)
[http://wiki.debian.org/HowTo/dnsmasq](http://wiki.debian.org/HowTo/dnsmasq)

2 - Edit the /etc/hosts file on your machine(s) and add entries for the domain/subdomains. Very easy to do but needs to be done on each machine on your internal network.

---

### Post by andrewjamesw on 2012-07-25
> **Cheesemill said:**
> You have 2 options here.

1 - Set up an internal DNS server. Can be tricky to set up but only needs to be done once no matter how many machines you have on your LAN. This used to always be done with Bind but a newer, easier option would be Dnsmasq.
[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)
[http://wiki.debian.org/HowTo/dnsmasq](http://wiki.debian.org/HowTo/dnsmasq)

2 - Edit the /etc/hosts file on your machine(s) and add entries for the domain/subdomains. Very easy to do but needs to be done on each machine on your internal network.
Thanks! 
Do you mean edit the hosts file on the server or all the local machines?
My server etc/hosts file looks like this:
127.0.0.1 localhost
127.0.1.1 UbuntuD530
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

---

### Post by cryptotheslow on 2012-07-25
You need to edit that file on all the other machines apart from the server.

---

### Post by andrewjamesw on 2012-07-25
oh no. That sounds like a pain. Most of the other machines are running win7, I've got no idea how to do that on them, and there are quite a few, all doing different things, lots of DLNA, printer sharing and other stuff going on here. I'm a little reluctant to mess with them.
 
I was thinking about (again) whether the router was the issue. My old router a Belkin something or other, used to let me go out of the LAN and come back in with a domain name. The D-Link I am using now might be the issue? I stopped doing sites for a while and only recently decided to have another play around, after i had replaced the router. I'd rather just buy a new router if that would fix it. The manual for the D-Link is less than informative, and it has been a bit ordinary in almost every way. 
Any ideas about routers? Has anyone got one that does that?

---

### Post by cryptotheslow on 2012-07-25
Windows has a hosts file too. Locations:

NT, 2000, XP (x86 & x64), 2003, Vista, 7 and 8:
%SystemRoot%\system32\drivers\etc\hosts

95, 98/98SE, Me:
%WinDir%\hosts

The hosts file has a really simple format, it would be hard to get it wrong.

Yes some routers refuse to route back into the LAN when the external IP is accessed from the LAN. I've had some that do and some that don't - can't remember off the top of my head which was which. There may be a configuration change you can make on your D-Link to make it work, but it will probably be a command line config done via telnet. See if you can find a CLI Reference manual for your router.

---

### Post by alphacrucis2 on 2012-07-25
Windows has hosts file under c:\windows\system32\drivers\etc

It works pretty much the same as hosts file on linux.


Whoops I see someone beat me to it ;-)

---

### Post by andrewjamesw on 2012-07-25
There is a bit about static routing in the router set up.
I played about with it and tried to point the WAN to the local IP of the server. Didn't do anything. I'm not even sure these settings have anything to do with what I am trying to achieve.
 
So what do I add to the hosts file? 
Server is on local IP 192.168.0.103

---

### Post by cryptotheslow on 2012-07-25
One additional line for each name you need, simply with the IP of the server followed by a few spaces then the name.

e.g.
```

192.168.0.103       [www.examplefirstname.examplesurname.net.nz]("http://www.examplefirstname.examplesurname.net.nz")

```

Try adding one line first, save the file then try to ping the name you just added and see that it is resolving to the LAN IP now.

---

### Post by Cheesemill on 2012-07-25
You add a line for each subdomain:
```
192.168.0.103     sub1.example.com     sub1
192.168.0.103     sub2.example.com     sub2
```

---

### Post by andrewjamesw on 2012-07-25
I tried that in my windows 7 machine. Still doesn't work. 
I rebooted it just to see if that made any difference, it didn't.
Not sure what to do now. 
I'm gonna sleep on it. It's nearly midnight here in NZ.

---

### Post by andrewjamesw on 2012-07-25
Yeah ! just tried that and it worked! Success at last.
 
It was the removal of the www and the adding of the sub domain at the end that did it.
 
it went like this: 
192.168.0.103     examplefirstname.examplesurname.net.nz     examplefirstname
 
Thank you very much people for all your help :-)

---

