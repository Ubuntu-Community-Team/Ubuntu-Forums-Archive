---
title: "Help Registering an Ubuntu Server with a Microsoft DynDNS server"
date: 2014-01-29
forum: New to Ubuntu
---

### Post by william9 on 2014-01-29
Hi
I have built a Ubuntu 12.04.3 LTS server in Azure. In Azure we also have built a MS 2012 domain controller running AD & DNS. I need to get my Ubuntu server so it can register itself with the MS DDNS service so other hosts can resolve my Ubuntu server.
I have managed to get resolv.conf so that it contains the domain (by adding a tail file under /etc/resolvconf/resolv.conf.d/).
I have followed some guidance from this link ---> [https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)
and installed installed and tried to configure ddclient.
I am not sure I am on the right path eg. I'm not sure of the protocol to configure in the ddclient
I have configured the ddclient to run as a daemon and configured an user account in the AD server for authentication.
Has anyone achieved this configuration and can point me to what will be required?
Thanks
....
I have come some way to resolving this however still struggling.
I have found I can update an unsecured Windows 2012 DDNS using nsupdate.
Now I am trying to make this work to a secured DNS server. 
I can get it to successfully update the DNS server using kinit to generate a ticket and then running nsupdate -g option. The issues with this are that the ticket kinit creates has a defined lifetime and I don't know how to schedule kinit to run automatically and without having to save a clear text password etc.
Now I need to somehow figure out how to generate a ticket on server boot so I can schedule the nsupdate to run.
PS I also tried to create keys using ktutil - however I haven't been successful in using anything in this space.
Any assistance would be greatly appreciated!
Cheers

---

