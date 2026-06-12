---
title: "trouble connecting internet"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by bemi.eliahu on 2008-09-03
hi, it seems that my new ubuntu is not able to connect the adsl modem. the support at the provider said that my computer activated inet6 instead of inet so the modem cannot communicate. any suggestions?

thanks

---

### Post by paulstaf on 2008-09-03
First off, do a:  

sudo ifconfig 

and see what interfaces you have and make sure that the one you have connected to your DSL is listed.  Say ETH0.

Then see if it has an IP address.  It may not have an IP address.

Here is what it SHOULD look like:
eth0      Link encap:Ethernet  HWaddr 00:21:86:58:d2:b4  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:86ff:fe58:d2b4/64 Scope:Link

If yours doesn't have an inet addr: address that looks normal, then try:

sudo dhclient

or try forcing a dhcp address to that particular interface using:

sudo dhclient eth0

You shouldn't have to mess with anything else.  You might want to reset your Adsl modem a couple of times or any other router you may have in between.

Good luck!

---

### Post by bemi.eliahu on 2008-09-03
> **paulstaf said:**
> First off, do a:  

sudo ifconfig 

and see what interfaces you have and make sure that the one you have connected to your DSL is listed.  Say ETH0.

Then see if it has an IP address.  It may not have an IP address.

Here is what it SHOULD look like:
eth0      Link encap:Ethernet  HWaddr 00:21:86:58:d2:b4  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:86ff:fe58:d2b4/64 Scope:Link

If yours doesn't have an inet addr: address that looks normal, then try:

sudo dhclient

or try forcing a dhcp address to that particular interface using:

sudo dhclient eth0

You shouldn't have to mess with anything else.  You might want to reset your Adsl modem a couple of times or any other router you may have in between.

Good luck!

Hi, Thanks. when doing the sudo ifconfig it doesnt give inet addr with ip adress - instead it will give inet6 addr with other non ip info. 
thanks again.

---

