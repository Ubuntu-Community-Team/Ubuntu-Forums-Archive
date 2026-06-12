---
title: "[SOLVED] Network disappeared"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by theolddrummer on 2008-11-30
I installed Ubuntu 8.10 a few weeks ago. When installed there was a browsable windows networkk just there - I could transfer files and the hole bit with no issues.
A couple of days ago there was an update of the kernel and the networking vanished,
Anyone know why?
Is the only way to get a network now, by installing LDAP and Samba? (actually that looks like it would be fun)

Very curious as to why the network disappeared.

Thanks for any info!

:guitar:

---

### Post by cmnorton on 2008-11-30
Is Network Manager running? It should be a little icon on the bottom right-hand side of the display.

What happens when you enter ifconfig from an X-term?

How did you connect to the internet before the network connectivity went away?

---

### Post by theolddrummer on 2008-11-30
> **cmnorton said:**
> Is Network Manager running? It should be a little icon on the bottom right-hand side of the display.

What happens when you enter ifconfig from an X-term?

How did you connect to the internet before the network connectivity went away?

I have internet connectivity as usual and the Network Manager is running ("Wired network connection")
What has vanished is the other Workgroup PC's in the house, IE Places/Network/Windows Network/now all 4 other PCs do not show up. I caqn ping the machines fine though.

This is what I get from ifconfig;
eth0      Link encap:Ethernet  HWaddr 00:05:5d:df:5f:e1  
          inet addr:192.168.1.115  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::205:5dff:fedf:5fe1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13545 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4238 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4918432 (4.9 MB)  TX bytes:666053 (666.0 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:576 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:37808 (37.8 KB)  TX bytes:37808 (37.8 KB)

---

### Post by cmnorton on 2008-11-30
What are the IP addresses of the other systems? 

Check your /etc/hosts file, what's changed? If you've upgraded recently, the upgrade should have backed up your /etc/hosts file to a similar name with an extension to prevent its being interpreted as /etc/hosts.

---

### Post by fester225 on 2008-12-02
I think I was just having the same problem.
The icon I should have been looking for is Samba Shares. I finally found it by starting Konqueror, and then clicking on Network Folders. Finding what you're looking for should be fairly straight-forward from there.

---

### Post by Kellemora on 2008-12-03
Hi TOD

Our network drops out every time there is an update!
And it takes half a day to get it back up and running again.

NO configuration files change, in fact nothing at all changes, except for the shares appearing in Places/Network.

We can ping, we can run smbtree and they all show up there just fine, and we can type in the IP address to bring them up MANUALLY, which is a ROYAL PAIN!!!!!
But they won't appear under Places/Network where they belong.

This problem has been going on now (verified by the thousands of archives I've read over the past three months) for OVER 2 YEARS NOW, with NO RESOLUTION forthcoming!

Everybody has their own way around the bugs in Ubuntu, for me rebooting the computers 3 times in quick succession often fixes it.  If I'm on the kernel before the newest one.  The newest one we have no LAN that works for more than an hour IF we can get it up at all.

When trying the new kernel again today, we get "Fatal Kernel Error" warning and then that computer crashes.
And I'm on the STABLE Ubuntu LTS not the new experimental Decrepid one.

TTUL
Gary

---

### Post by theolddrummer on 2008-12-05
> **Kellemora said:**
> Hi TOD

Our network drops out every time there is an update!
And it takes half a day to get it back up and running again.

NO configuration files change, in fact nothing at all changes, except for the shares appearing in Places/Network.

We can ping, we can run smbtree and they all show up there just fine, and we can type in the IP address to bring them up MANUALLY, which is a ROYAL PAIN!!!!!
But they won't appear under Places/Network where they belong.

This problem has been going on now (verified by the thousands of archives I've read over the past three months) for OVER 2 YEARS NOW, with NO RESOLUTION forthcoming!

Everybody has their own way around the bugs in Ubuntu, for me rebooting the computers 3 times in quick succession often fixes it.  If I'm on the kernel before the newest one.  The newest one we have no LAN that works for more than an hour IF we can get it up at all.

When trying the new kernel again today, we get "Fatal Kernel Error" warning and then that computer crashes.
And I'm on the STABLE Ubuntu LTS not the new experimental Decrepid one.

TTUL
Gary

Thanks for the information everyone.
Out of town a couple of days and then I started messing with things on my own (without your advice)
Yes I know - I really broke it and had to reinstall.
everything is working and even after the kernel update I did not loose the network.
Thank again all.

---

