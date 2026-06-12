---
title: "lan addresses"
date: 2012-05-08
forum: New to Ubuntu
---

### Post by squrl on 2012-05-08
I have a network dns321 drive on my lan and made the mistake of doing a reset on it. Now I cant seem to access it. Is there a way to query the lan from ubuntu to verify the lan addresses on my lan.  Maybe the reset changed the address.

Thanks

---

### Post by Mark Phelps on 2012-05-08
You can't query a "lan" -- that's a network, which is a collection of things; you have to query a device.

If your local addresses are assigned by a router (through DHCP), you have to get access to the router's admin pages, and on one of them, you will have the ability to display the list of LAN "clients" -- each one with its own IP address.

---

### Post by nrabett on 2012-05-08
Try this

for ip in $(seq 1 254); do ping -c 1 192.168.1.$ip>/dev/null; [ $? -eq 0 ] && echo "192.168.1.$ip UP" || : ; done

... replacing 192.168.1 with the three first numbers in the address you find after "inet addr" in the sections eth? or wlan? after entering the command "ifconfig" in a terminal. Getting the result could take five minutes.

---

