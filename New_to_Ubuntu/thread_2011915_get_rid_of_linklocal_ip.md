---
title: "get rid of linklocal ip"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by alimomen on 2012-06-28
my dear helper
 
im new to ubuntu,I have installed ubuntu on vmware.I used to connect my alfa usb adapter card and It got ip from dhcp(some thing like 192.168.1.5) i installed dhcp3-server ,dhcp3-common and i upgrade and updated(sudo apt-get install update and upgrade),but from that time on as soon as i connect alfa it gets locallink ip(169.254), i got confused and in dire need of help
what should i do(in details and simple words of cource)
thanks

---

### Post by Drenriza on 2012-06-28
> **alimomen said:**
> my dear helper
 
im new to ubuntu,I have installed ubuntu on vmware.I used to connect my alfa usb adapter card and It got ip from dhcp(some thing like 192.168.1.5) i installed dhcp3-server ,dhcp3-common and i upgrade and updated(sudo apt-get install update and upgrade),but from that time on as soon as i connect alfa it gets locallink ip(169.254), i got confused and in dire need of help
what should i do(in details and simple words of cource)
thanks

A linklocal address also called localscope in IPv6 (i believe) is a local LAN significant ip address only.
You get such a address if you cannot reach a DHCP service, and havnt a static ip address.

The linklocal address is then assigned to you, so you can communicate with a future DHCP service on the LAN, when one presents itself.

[http://en.wikipedia.org/wiki/Link-local_address](http://en.wikipedia.org/wiki/Link-local_address)

---

### Post by spikoley on 2012-06-28
It sounds like the DHCP3 install or the upgrade killed your network card.  My guess is that was DHCP3 that did it.  I think the DHCP3 server turned off your DHCP client.   

The command *dhclient* will attempt to obtain an IP address.  Try running that first.

```
sudo dhclient
```

If that doesn't work then try uninstalling DHCP3 server.

---

### Post by alimomen on 2012-06-28
> **spikoley said:**
> It sounds like the DHCP3 install or the upgrade killed your network card. My guess is that was DHCP3 that did it. I think the DHCP3 server turned off your DHCP client. 
 
The command *dhclient* will attempt to obtain an IP address. Try running that first.
 
```
sudo dhclient
```
 
If that doesn't work then try uninstalling DHCP3 server.
 it didnt worked(command not found0
uninstalling dhcp3 seems to be just omitting the problem,I am after the solution not ignoring the problem
anyone knows what the solution is?

---

### Post by spikoley on 2012-06-28
> **alimomen said:**
> 
uninstalling dhcp3 seems to be just omitting the problem,I am after the solution not ignoring the problem
anyone knows what the solution is?

It isn't ignoring the problem.  It is trouble shooting.  In order to find the issue you need to eliminate the variables until you find the one that is causing the issue.  Since you listed installing DHCP3 Server as one of the variables it is the logical place to start.

Why did you install DHCP Server?  The only reason I can think of to install it is to allow other computers to connect threw it to reach the internet.  Do you need other computers to obtain an IP address through this computer?  If not, then there is no reason to have DHCP3 Server installed.

It looks like the latest version of Ubuntu may have changed the DHCP client and that is why *dhclient* didn't work ([Proof it use to work]("http://ubuntuforums.org/showthread.php?t=1062894&highlight=dhcp")).  Maybe there was a typo?  Try using the command again, but with specifying the network interface.  I will use eth0 as an example.  Your interface might be different.

```
sudo dhclient eth0
```

My other educated guess is when you installed DHCP3 Server it altered the DHCP client configuration file to prevent it from obtaining an IP address from a DHCP server.  Post the results of /etc/network/interfaces.

```
less /etc/network/interfaces
```

Try uninstalling DHCP Server if *dhclient* didn't work.  You can alway install it again.

[DHCP3 Server Ubuntu Help Page]("https://help.ubuntu.com/community/dhcp3-server")

---

