---
title: "My IP address has been hijacked"
date: 2014-08-04
forum: New to Ubuntu
---

### Post by lsheran on 2014-08-04
I have been running Ubuntu 14.04 since its release and all have been working well. I am also running Plex Media Server. Last week I noticed that I was unable to see the contents of the Plex Media Server.  The only thing available was the queue. My network is on 192.168.1.0. My IP addresses are all reserved. The Media server has a reserved address of 192.168.1.100. On checking the address that the machine is running on, I found it to be 192.168.102.100. I can't determine where it is getting this address from. All my other machines are fine. I can't seem to make this machine get the 192.168.1.100 address. I change the address from the command line, but when I reboot, it goes back to 192.168.102.100. By the way, I can access the internet, although my gateway is 192.168.1.1. I decided to make the IP static. When I do this, ifconfig shows the correct address of 192.168.1.100, but I can't access anything.  I have been searching, but with no results. I am thinking that I'll have to reinstall, which I don't want to do. I'm thinking that there is bug on my machine.  It is not making sense. Have anyone seen anything like this before or have an idea as to what may be causing this?
Thanks in advance to everyone for any light you may be able to shed on this.

Lester

---

### Post by steeldriver on 2014-08-04
Hello and welcome to the forums

I think the most likely explanation is that there is another device on your network that is acting as a DHCP server and router, and your plex server is getting its 192.168.102.xxx IP from that - can you describe your network some more?

---

### Post by ajgreeny on 2014-08-04
Your problem sounds rather like that discussed at [http://ubuntuforums.org/showthread.php?t=2237478&p=13089570#post13089570](http://ubuntuforums.org/showthread.php?t=2237478&p=13089570#post13089570) which is also someone with a plex media server.

---

