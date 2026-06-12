---
title: "[SOLVED] python list all ip addresses"
date: 2008-03-14
forum: Programming Talk
---

### Post by themusicwave on 2008-03-14
Good Morning everyone,

I was wondering if there is an easy way to list all the IP addresses a machine has in Python.  

I am writing and installer for a system in Python, the server has 2 NICs, one to run Apache and talk to the Enterprise/business network and one to talk a few hundred machines.

What I am trying to do is figure out the IP for the user so they don't have to enter it.  This way I can configure apache to listen on the correct NIC.  

I can get the "Primary" IP address with:

socket.gethostbyname(socket.gethostname())

The problem is that the server runs on Windows(not my choice) and depending on how the user setup the NICs, this could be the wrong address.  I know the starting octet of the correct address so if I could get both I could pick the right one.

Thanks in advance for the help!

---

### Post by themusicwave on 2008-03-14
I just figured it out.  This will return a list will all the system IP Addresses.

[PHP]
def getIpAddresses(self):
        addrList = socket.getaddrinfo(socket.gethostname(), None)

        ipList=[]
        for item in addrList:
            print "Item:", item
            ipList.append(item[4][0])

        return ipList
[/PHP]

---

