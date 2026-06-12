---
title: "help with transmission / deluge"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by nomeparece on 2008-08-16
i'm having problems with the BT clients transmission and deluge, neither of them seems to be able to download at a decent speed (max 10 kb/s). i'm  connecting to a wireless network, with a router (d-link di-524), and using the not-manual configuration in nm-applet. 
this is what i've done: at first, i was using transmission but it couldn't find any peers, and in the preferences showed "port closed", for any port. then, installed deluge, and it showed all ports closed. finally, uninstalled deluge, and transmission started showing all ports open, but downloading really slow.
Before installing ubuntu i was using xubuntu, and transmission worked fine.. so.. i dont' know where the problem comes from

could anyone help me configure these things.. i'm really lost
thanks..

---

### Post by SZ07 on 2008-08-16
Make sure port forwarding is setup correctly in your router and your bittorrent client.

I don't use transmission but this is what I did when I noticed deluge was slow upon installation:

Go to preferences-->network tab

Make sure the following are checked:
Enable Mainline DHT
UPnP
NAT-PMP
Peer Exchange
Local Peer Discovery

The following should be UNchecked:
Random Ports
Prefer to encrypt the entire stream

Set inbound and outbound encryption to "enabled" and level to "either." If you are still not getting good speed, disable encryption for both and see if anything happens.

I was able to hit max speeds with these settings but I find that utorrent is still better. If you can't get full speed then maybe try utorrent.

---

### Post by nomeparece on 2008-08-16
tried those settings, deluge works and donwloads at aobout 25-30 kb/s.:) so now i'm going to try port forwarding my router.

---

