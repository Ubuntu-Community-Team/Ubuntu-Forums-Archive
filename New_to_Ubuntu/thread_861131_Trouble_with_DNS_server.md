---
title: "Trouble with DNS server"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by SmoothRunnings on 2008-07-16
I am having trouble setting up the DNS server in Ubuntu Server. I come from a Windows Server network and fully understand how to setup it with respect to Microsoft's practices however when I attempt to apply the same knowledge to Ubuntu I fail. 

We have a wireless network that we are putting on a separate network seqment that requires use to have have a DNS/DHCP server so we can translate the server names cross to network seqment. 

From what know with Microsoft DNS server you have to point the DNS server to it's self making the primary DNS IP address the IP address of the DNS server. Inside the DNS server you can add forwarders which I normally do. However MS DNS server doesn't require or asked for for an dns1.xxxxx.com record and that's were I think I am getting lost but Ubuntu DNS server does.

I have install the ubuntu-desktop to try and make my life easier but it's ended up runines becuase I found after installing the GD(something)Admin interface which installs Bind9 that there is no option for forwarders, and if I manaually change the configuration files in the /etc/bind/ folder the changes are not reflected in the application even after I reboot the machine... (FRUSTRATION SETS IN)

I also need to create a domain.local account and I am not sure if I can do this with the Linux DNS server? Microsoft DNS server supports it and recommends it for security reasons.

So I am open to your input. 

Thanks
Andrew

---

### Post by schwascore on 2008-07-18
I'm not an expert on DNS, but here are some resources that might help you out a bit.

[http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)

[http://www.howtoforge.com/installing-an-ubuntu8.04-dns-server-with-bind](http://www.howtoforge.com/installing-an-ubuntu8.04-dns-server-with-bind)

[http://www.novell.com/coolsolutions/feature/19391.html](http://www.novell.com/coolsolutions/feature/19391.html)
(This one is specifically about migrating from Microsoft DNS. It is written for SUSE, but it might work on Ubuntu as well.)

Good luck and perhaps you could post a solution if you find one.

---

