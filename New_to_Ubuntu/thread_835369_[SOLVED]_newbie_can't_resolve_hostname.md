---
title: "[SOLVED] newbie can't resolve hostname"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by BigBadBaz on 2008-06-20
Hi. I'm a complete newbie (first time setting up a server or dealing with Linux). I just installed Ubuntu 8.04 server. I can ping the ip address, but when I try to ping the hostname, it doesn't work.

---

### Post by drs305 on 2008-06-20
Run this to check the hosts file. It should have a line like: 
127.0.0.1 yourcomputername

```
cat /etc/hosts
```

If you aren't sure, you can post the results here and we can look at it and give you further advice.

---

### Post by the_doc on 2008-06-20
You resolve host names either by a DNS service or by your own hosts file.  If you're setting up your own server I'm guessing you've not set up a DNS sevice?

---

### Post by BigBadBaz on 2008-06-20
> **drs305 said:**
> Run this to check the hosts file. It should have a line like: 
127.0.0.1 yourcomputername

```
cat /etc/hosts
```

If you aren't sure, you can post the results here and we can look at it and give you further advice.

It reads:
127.0.0.1 localhost

---

### Post by BigBadBaz on 2008-06-20
> **the_doc said:**
> You resolve host names either by a DNS service or by your own hosts file.  If you're setting up your own server I'm guessing you've not set up a DNS sevice?

I set my server up within another network that has a DNS service.

---

### Post by the_doc on 2008-06-20
Put the IP address of the PC you want to connect to plus its name into that file in the same format as the **localhost** entry.

---

### Post by BigBadBaz on 2008-06-20
> **the_doc said:**
> Put the IP address of the PC you want to connect to plus its name into that file in the same format as the **localhost** entry.

I did that with one computer, and it worked. However, I also want to be able to access my server with webmin from any machine I want.

---

### Post by the_doc on 2008-06-20
After re-reading this thread I guess what you want is for every network node to be able to access the new server by its name.  If you already have a DNS server in that network then I'm guessing you'll have to register the new server with the DNS server.

The host file method isn't really convenient if this is the case, as every node would have to have an entry for the new server in its host file.

---

### Post by BigBadBaz on 2008-06-20
How do I do that? Does it have to be done from the DNS side?

---

### Post by JordanH on 2008-06-20
Let me see if I got this straight...
PC1 - new linux machine.  eg hostname PC1.acme.com / IP address 192.168.1.1
PC2 - Other whatever machine.  eg hostname PC2.acme.com / IP address 192.168.1.2

You try to ping PC1 from PC2 as follows:  ping 192.168.1.1
and you receive the correct reply.

You try to ping PC1 from PC2 as follows:  ping pc1.acme.com
and you receive timeouts.

Ok... so the problem is that pc1.acme.com is not being resolved on PC2.  So a) pc1.acme.com is not registered in your DNS or b) PC2 does not have an entry in its host file for pc1.acme.com.

Lets assume b) and we'll go from there.

Make sure each system has a host file with the correct address of the other.
Linux:  /etc/hosts
Windows:  c:\windows\system32\drivers\ets\hosts

Now add the appropriate line in each host file
on PC1:  echo "192.168.1.2  pc2  pc2.acme.com" >> /etc/hosts
on PC2:  echo "192.168.1.1  pc1  pc1.acme.com" >> /etc/hosts
(if it is Windows, use notepad to edit the appropriate file then save and close)

You may now ping the hosts using IP address, hostname or fully qualified name.

[edit]  D'oh!  It appears you have decided to use Option a) the DNS instead of using option b) local hosts files.  Are you sure you have a local DNS server?  If this is a company, speak to your sysadmin and they will add the appropriate records for you.  (You can ask them to add an "a" record for your new host and they'll understand.  If you do not have a sysadmin or DNS server, then you are back to Option B).

If you want to install a DNS server, this is more work.  Do some searching on "bind".

---

### Post by BigBadBaz on 2008-06-20
That won't work for me. I want to be able to use webmin from any machine in the network.

---

### Post by the_doc on 2008-06-20
As I've already said, the hostfile method is not convenient.

**How do I do that? Does it have to be done from the DNS side?**

I'm not a complete DNS expert, but yes I would suggest that would have to be done on the DNS server.  Essentially you would be putting the new servers name and IP address into the DNS database, then the network nodes should be able to resolve the new server name if your DNS server is set up correctly.

---

### Post by BigBadBaz on 2008-06-20
I probably won't be able to get access to the DNS server until Monday. I'll try it then, and let you know.

---

### Post by the_doc on 2008-06-20
Good luck!

---

### Post by BigBadBaz on 2008-06-20
I didn't get to the dns server yet, but I was told that our main ubuntu server didn't need to be added to it.

---

### Post by Dedoimedo on 2008-06-20
Hello,
Setting up the DNS server (BIND) is a lot of work. But if you want, I can help ... say the word.
Dedoimedo

---

### Post by BigBadBaz on 2008-06-20
I don't need to set up the DNS server, it's already set up. I'm just trying to get my derver to be reachable through its hostname. the_doc recommended that I try to add my hostname to the DNS server, but my boss told me that our main LAMP server didn't need to be. Any other ideas?

---

### Post by Dedoimedo on 2008-06-20
Hello,

The DNS server is defined in this file:

/etc/resolv.conf

Add the line: nameserver xxx.xxx.xxx.xxx where xxx.xxx.xxx.xxx is the IP address. Save and exit and you should have your DNS server all set up.

Of course, you must be able to reach it - this means the right route and firewall rules.

Dedoimedo

---

### Post by the_doc on 2008-06-21
> **BigBadBaz said:**
> I don't need to set up the DNS server, it's already set up. I'm just trying to get my derver to be reachable through its hostname. the_doc recommended that I try to add my hostname to the DNS server, but my boss told me that our main LAMP server didn't need to be. Any other ideas?

If your network uses DNS to resolve hostnames I can't see how your new server name will be resolved unless it's added to the database if you don't want to use the host file method.  But I'll be happy to be educated!

---

### Post by hyper_ch on 2008-06-21
Listen to Dedoimedo two posts above.

---

### Post by the_doc on 2008-06-21
Who me?

---

### Post by hyper_ch on 2008-06-21
no, not you doc... I meant the TO

---

### Post by the_doc on 2008-06-21
Phew, thought I'd missed something!

---

### Post by BigBadBaz on 2008-06-23
> **Dedoimedo said:**
> Hello,

The DNS server is defined in this file:

/etc/resolv.conf

Add the line: nameserver xxx.xxx.xxx.xxx where xxx.xxx.xxx.xxx is the IP address. Save and exit and you should have your DNS server all set up.

Of course, you must be able to reach it - this means the right route and firewall rules.

Dedoimedo

I already had the line nameserver xxx.xxx.xx.xxx
I don't have any firewall on my server. How do I make sure that I have the right route?

---

### Post by Dedoimedo on 2008-06-23
Hi,

Type route and if you want post here. Just in general:

default is the default gateway --> this IP leads to all IPs not defined in any other route; preferably, it will point to your DNS server.

A flag that indicates gateways is G.

Ping and traceroute can also help make sure you have no network connectivity problems.

Dedoimedo

---

### Post by BigBadBaz on 2008-06-23
> **Dedoimedo said:**
> Hi,

Type route and if you want post here. Just in general:

default is the default gateway --> this IP leads to all IPs not defined in any other route; preferably, it will point to your DNS server.

A flag that indicates gateways is G.

Ping and traceroute can also help make sure you have no network connectivity problems.

Dedoimedo

I can ping google.com ad well as all of my internal servers.
Route gives me the following:

Destination   192.168.42.0            default 
Gateway       *                       192.168.42.1
Genmask       255.255.255.0           0.0.0.0
Flags         U                       UG
Metric        0                       100
Ref           0                       0
Use           0                       0
face          eth0                    eth0

The gateway does look right.

I'm sorry, the post didn't come out like I thought it would. There's a space in between each of the addresses.

---

### Post by JordanH on 2008-06-23
> **BigBadBaz said:**
> I didn't get to the dns server yet, but I was told that our main ubuntu server didn't need to be added to it.

As per my previous note and the_doc's comments, your above statement is incorrect.  You really do need to have it in the DNS.
Your 2 options are
A)  Update the DNS to point to your new machine.
B)  Use Host files.
You have said that host files are out of the question (correct answer, seeing as this is not your home system)

Your sysadmin really needs to add a record to your DNS to point to your server in order for clients to resolve the IP address.

---

### Post by BigBadBaz on 2008-06-23
I confirmed with my sysadmin that we have never had to manually add a server to the DNS, nor have we used host files.

---

### Post by the_doc on 2008-06-23
Do you use DHCP on that network?

---

### Post by BigBadBaz on 2008-06-23
Yes.
I just had my sysadmin add my server to the DNS, and it still doesn't work.

---

### Post by the_doc on 2008-06-23
Ask him if you're using dynamic DNS.

---

### Post by BigBadBaz on 2008-06-23
We are using dynamic DNS.

---

### Post by the_doc on 2008-06-23
Right!  That's why you don't manually add DNS host records, because the IP address associated with each hostname would be updated to frequently with DHCP, and would be inconvenient.  So dynamic DNS does it in conjunction with DHCP, everytime DHCP dishes out a new IP to a host it updates DNS with the new details.

Same principle as doing it yourself, but less hassle!

Your /etc/resolv.conf file lets your computer find and query the DNS server.

You say it's still not working?

---

### Post by BigBadBaz on 2008-06-23
That's correct.

---

### Post by the_doc on 2008-06-23
Ok, sorry if I'm regurgitating old info, are you sure you are getting a DHCP address?

---

### Post by BigBadBaz on 2008-06-23
I believe that I'm getting a DHCP address. In the file /etc/network/interfaces it says iface eth0 inet dhcp. Also, I got an IP address without setting it manually. Unless something's not working right, I should be getting a DHCP address.

---

### Post by BigBadBaz on 2008-06-24
Any other ideas?

---

### Post by the_doc on 2008-06-24
I have been thinking about this one and haven't simply jumped ship!  

Can you check to see if there are any host records on the DNS server that pertain to your new server (in addition to the one your sysadmin added manually)?

And it may be worth trying to refresh the new servers IP address lease and see if that updates the DNS server.

---

### Post by BigBadBaz on 2008-06-24
There are no other records on the DNS sever. When I refreshed the IP address I did get a new address. However, although the DNS server says that my IP address is leased, it doesn't associate any name with it.

By the way, I just asked the sysadmin if we're using dynamic DNS and he said that we are using it to connect to the outside, but within our network we're not using it. (The first time I asked the boss.)

---

### Post by JordanH on 2008-06-26
Some Dynamic DNS servers require that you explicitly login and update your IP address when it changes.  Do the other servers in the environment really do this?  It's rare that I see servers use dynamic addresses within a company network.

I'm really confused how you can have no records in the DNS and no host files and yet be able to lookup other server addresses.

So, internally, do you use a DNS server?  Or are you strictly relying on an external DNS?

---

### Post by BigBadBaz on 2008-06-27
We have an internal DNS server, but it's not dynamic (post #39). We usually do not have to add a server to the DNS (it's done automatically), but we tried doing that anyway, and it didn't help.

From my server I can ping another IP address or hostname, and all of the other servers can be pinged by there hostnames or IP addresses.

---

### Post by BigBadBaz on 2008-07-02
Hi all. I solved it! I had to set up a Samba file server, so I reinstalled Ubuntu, but this time with Samba. After the installation of Webmin, I tried logging on using the hostname, and it worked! I tried doing it on another machine, and that one worked as well!

My thanks to all of you for your time and help.

---

### Post by the_doc on 2008-07-04
> **BigBadBaz said:**
> Hi all. I solved it! I had to set up a Samba file server, so I reinstalled Ubuntu, but this time with Samba. After the installation of Webmin, I tried logging on using the hostname, and it worked! I tried doing it on another machine, and that one worked as well!

My thanks to all of you for your time and help.

Not sure how that solved the problem, but I'm happy for you!

---

### Post by BigBadBaz on 2008-07-06
I don't know either, but it worked on another server I was trying to set up as well. I'm not about to start complaining.

---

### Post by lavinog on 2008-10-15
I think it worked because samba setup wins

---

