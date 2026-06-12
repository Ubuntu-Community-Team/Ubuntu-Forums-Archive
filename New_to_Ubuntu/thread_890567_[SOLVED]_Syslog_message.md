---
title: "[SOLVED] Syslog message"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by dunbrokin on 2008-08-15
Aug 15 19:54:20 PJ dhclient: DHCPREQUEST of <null address> on eth1 to 10.1.1.1 port 67
Aug 15 19:54:20 PJ dhclient: DHCPACK of 10.1.1.5 from 10.1.1.1
Aug 15 19:54:20 PJ NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth1 
Aug 15 19:54:20 PJ dhclient: bound to 10.1.1.5 -- renewal in 1554 seconds.

This appears about ever half an hour...what is all about?

---

### Post by freak42 on 2008-08-15
it is the renewal of your ip adress.

Your dhcp server (likely your home router) gives out ip addresses for each computer on your network, if your computer asks for one (e.g. at startup).. however these addresses are only lent (or given) for a certain period of time (usually a day). If after this period the computer is still on and wants to keep the ip address it needs to renew it.

As you can see from your output the renewal perio is about 1500 seconds which is about half an hour.. so every half hour your computer asks the router again for an ip address.

There is nothing wrong with this behaviour (no error whatsoever). However the lease/rent period for the ip address is quite short, if you administrate your own router and you don't have a lot of computers you can increase the renewal period. If your network gets administered by somebody, this person might have had resons to set it to this low value.

So in short: Nothing is wrong, this is normal behaviour for any dhcp managed network.

---

### Post by dunbrokin on 2008-08-15
> **freak42 said:**
> it is the renewal of your ip adress.

Your dhcp server (likely your home router) gives out ip addresses for each computer on your network, if your computer asks for one (e.g. at startup).. however these addresses are only lent (or given) for a certain period of time (usually a day). If after this period the computer is still on and wants to keep the ip address it needs to renew it.

As you can see from your output the renewal perio is about 1500 seconds which is about half an hour.. so every half hour your computer asks the router again for an ip address.

There is nothing wrong with this behaviour (no error whatsoever). However the lease/rent period for the ip address is quite short, if you administrate your own router and you don't have a lot of computers you can increase the renewal period. If your network gets administered by somebody, this person might have had resons to set it to this low value.

So in short: Nothing is wrong, this is normal behaviour for any dhcp managed network.

Thanks for that...very informative and much appreciated.

---

### Post by freak42 on 2008-08-15
Thanks for the thanks ;-)

you might want to mark this thread as "solved" you can do that on the red "thread tools" popup-menu on this page's top right area.

---

