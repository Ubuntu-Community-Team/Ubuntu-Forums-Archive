---
title: "Problem with MAC(Physical) address"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by karthikophobia on 2008-11-18
My friend just switch to Ubuntu from XP. He is registered with a different ethernet card from the one he is using. So he needs to change his MAC address to that of his old card to access internet/LAN. 

He tried to change it with System > preferences > network  Configuration. He edited the 'Auto eth0' connection and changed the MAC address. But, it didn't work.

Plz tell, what is to be done to change the MAC address.

thanq

---

### Post by halitech on 2008-11-18
the MAC address is hardcoded into the NIC, there is no easy way to change it without using spoofing of some kind. Did he physically change the NIC when he installed Ubuntu?

---

### Post by redseventyseven on 2008-11-18
Does this help?
[http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/)

If not, try googling "changing mac address ubuntu" and see if there's any other guides.

---

### Post by karthikophobia on 2008-11-18
No, He just changed in th '**Network Configuration**' after he installed ubuntu.

Can't the MAC address be changed using the *ifconfig* command?

---

### Post by karthikophobia on 2008-11-18
No, He just changed in th '**Network Configuration**' after he installed ubuntu.

Can't the MAC address be changed using the *ifconfig* command?

---

### Post by halitech on 2008-11-18
not using the ifconfig command but according to the link red provided it should be able to be done by editing the network interfaces config file

---

### Post by karthikophobia on 2008-11-18
> **redseventyseven said:**
> Does this help?
[http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/)

If not, try googling "changing mac address ubuntu" and see if there's any other guides.

We tried the link you suggested, but still, Net isn't connecting

---

### Post by ibuclaw on 2008-11-18
Do you know what the MAC address of the card was previously?

That would be a start in getting it right.

Also, if you don't mind, can you post the contents of **/etc/network/interfaces** just for clarification?

[EDIT]
Also, try rebooting your computer after you save the file... the network daemon requires restarting.

Regards
Iain

---

### Post by handydan918 on 2008-11-18
> **karthikophobia said:**
> My friend just switch to Ubuntu from XP. He is registered with a different ethernet card from the one he is using. So he needs to change his MAC address to that of his old card to access internet/LAN. 

He tried to change it with System > preferences > network  Configuration. He edited the 'Auto eth0' connection and changed the MAC address. But, it didn't work.

Plz tell, what is to be done to change the MAC address.

thanq

So what's wrong with just getting the net admin to authorize the current MAC?

---

