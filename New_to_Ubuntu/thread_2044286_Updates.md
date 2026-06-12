---
title: "Updates"
date: 2012-08-19
forum: New to Ubuntu
---

### Post by wiradog on 2012-08-19
Hi Guys,
I am in the process of installing and configuring Ubuntu 12.04 on a PC to use as a NAS. I have configured the network config for DHCP, which from behind my router gives the new NAS access to the internet-only it does not download any updates.
When I run 'sudo apt-get updates' it fails to contact the server, this also applies to any other command for updates or down loads.
Any ideas on what could be wrong? Do I have to set up domain names or something to make this work?

:confused:

---

### Post by The Cog on 2012-08-19
It is update singular, not pleural:
```
sudo apt-get update
```

But I don't think that's your problem. To start with, it would help if we could see if DNS is working, and if general internet access is working. Please can you try these commands and post the results. 

First, we'll try general IP connectivity. Try to ping this address:
```
ping 91.189.94.12
```

If that didn't work, it would help to see your routing table:
```
route -n
```

but if the ping did work, let's try DNS name resolution:
```
ping ubuntuforums.com
```

---

### Post by newb85 on 2012-08-19
> **wiradog said:**
> I have configured the network config for DHCP, which from behind my router gives the new NAS access to the internet-only it does not download any updates.
When I run 'sudo apt-get updates' it fails to contact the server, this also applies to any other command for updates or down loads.

If apt-get updates fails, it would be helpful to those trying to help you to post the error messages you're receiving (or if the list is unwieldy, at least a representative sample).

The issue could be the DNS server.  I've experienced issues where the internet worked great for everything except downloading updates, and the error messages told me that the hostnames weren't being resolved.  Setting network-manager to use an alternative DNS server took care of the problem.

If you're using a version of Ubuntu with a GUI, click the wireless applet, go to "Edit Connections" and edit the connection being used to connect to the internet.  Under IPv4 settings, switch the method from "Automatic (DHCP)" to "Automatic (DHCP) addresses only" and in the DNS Servers box, enter an alternative DNS (for example, Google's 8.8.8.8 ).

---

### Post by wiradog on 2012-08-20
Thanks Guys,

There seems to have been a problem with internet connection in general which has now cleared as mysteriously as it appeared. All is fine for now, thanks for your help.

---

