---
title: "Virtual Machine Security"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by imjscn on 2008-07-04
My guest XP share host ubuntu's internet through the setting of Nat which is suppose to share host's address and communicates with host via a private network--they said it's hidden behind host.

Since I don't need to share anything between host and guest except internet connection, I didn't make any setting for share in the host.

In my case, guest XP is protected by host ubuntue's nature strong security system, right? or, do I still need to install firewall for guest XP?

I don't know what else vmplayer has done on host ubuntu to make it shareable, do I need to shut down anything to protect itself from sharing anything with guest?

By the way, saving data and document in online storage is the most convenient way to share things, I'd recommend this to VM folks.

---

### Post by Canis familiaris on 2008-07-04
Ubuntu has a built in firewall called iptables which will protect Ubuntu and to a certain extent your Windows VM. However it will not protect you from Spyware and viruses. 
You should install a Spyware remover and probably an antivirus for the Windows VM.
But wait for comment for a more experienced VM user to be sure.

P.S.:Why do you want to access the internet through Windows Vm anyway? You could access the internet from the host Ubuntu as well.

---

### Post by imjscn on 2008-07-04
I prefer not use firewall in ubuntu because its default security system is safe enough for me and additional protection might consume PC resources. 

I use an statistic analysis software in VM, which need connect to data source, that's why I need VM connect to internet. I don't have other internet activities in VM.

---

### Post by Canis familiaris on 2008-07-04
> **imjscn said:**
> I prefer not use firewall in ubuntu because its default security system is safe enough for me and additional protection might consume PC resources. 

I use an statistic analysis software in VM, which need connect to data source, that's why I need VM connect to internet. I don't have other internet activities in VM.

Ubuntu already has a firewall preinstalled called iptables. It is command line software. You don't generally have to do anything with it.

If you ONLY use the statistic analysis software, you are pretty safe.
Of course you could set up a firewall in Windows such as Comodo to disallow all incoming and outgoing connections from all software except the Statistic analysis software.

---

### Post by imjscn on 2008-07-04
I see, if so, I think I can try to work without firewall. Thanks!

---

