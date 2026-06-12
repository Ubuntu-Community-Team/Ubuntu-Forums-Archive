---
title: "Best way to extract vlan Tci from skb"
date: 2012-02-06
forum: Programming Talk
---

### Post by joyboyhardik@yahoo.com on 2012-02-06
Hi 

I want to forward packets which are vlan tagged through vlan_hwaccel_rx

Now the device has vlangroup (neccesary field to pass) but i am not sure how to extract the vlan id from skb->data. are there any methods which shall do that .

Example:

skb->protocol = eth_type_trans(skb, tun->dev); // shall return the protocol.


Regards and Thanks

---

