---
title: "I show to be wired and connected but no internet"
date: 2011-12-12
forum: New to Ubuntu
---

### Post by sdelinde on 2011-12-12
Toshiba satellite a215, lucid Lynx 64-bit os. I ran cd to install Oneiric Ocelet[ATTACH]208970[/ATTACH]

[ATTACH]208971[/ATTACH]

[ATTACH]208972[/ATTACH]

[ATTACH]208973[/ATTACH]

[ATTACH]208974[/ATTACH], and have manually set up my wired network. I can see other  computers on network but can not
get the internet on fireFox to find server. My ip address and dns are correct, they worked
well with Ubuntu 7.10. What am I missing in order to get connected.

Thanks for any of your help! I have played with Ubuntu for a while but an still a green horn
newby.

---

### Post by gandaran on 2011-12-12
wired internet should work automatically without doing any setup, try deleting the network manager wired setup then reboot the computer and see if that works, it should! (if DCHP server is enabled on the router)

---

### Post by sdelinde on 2011-12-12
Thanks, My wired connection is from my work, from which, i ubtained the ip address, gateway, dns, etc.
I have to put this in manually. These settings worked fine in Ubuntu 7.10. But with Ocelet I can see the
other computers in my network, also printers etc. But I can not get on the internet , Firefox browser says server not found.

any help you can provide??

---

### Post by gandaran on 2011-12-12
>  Firefox browser says server not found.
have you tried any other web browser?
looks more like a DNS problem
or are you using a proxy server?

---

### Post by sdelinde on 2011-12-12
My question is why would the same settings work in Ubuntu 7.10, and not on Oneiric Ocelet???

---

### Post by ephmanjmm on 2011-12-12
Perhaps, you did not put the info in correctly.  It shows a default gateway of 255.255.255.0  if I am understanding your pictures correctly.
The gateway for destination 0.0.0.0 is 255.255.255.0

---

### Post by dave0109 on 2011-12-12
The screenshot of your interfaces show the wifi but not the ethernet port.  On the wifi, you only have IPv6 setup, there's no IPv4 address.

Your routing table only shows IPv4 addresses.

But mostly, your default gateway is wrong.  It should be one of the addresses on your 200.10.10 network.  This is a classic networking error where you can see local machines, but nothing out side of the LAN.  Don't worry, we've all made it. :)

---

### Post by sdelinde on 2011-12-12
[ATTACH]208991[/ATTACH]

Check out these screen shots and see if you can find out what I am doing wronge!!!

---

### Post by gandaran on 2011-12-12
> **sdelinde said:**
> [ATTACH]208991[/ATTACH]

Check out these screen shots and see if you can find out what I am doing wronge!!!
the default route is what I believe is wrong.

---

### Post by sdelinde on 2011-12-12
How would I obtain this default route? Next to my laptop here, I have my desktop running windows xp
the manual settings are : address 200.10.10.xxx, gateway 255.255.255.0, mask: 255.255.255.0, 
dns 204.174.16.4, with alturnitive 204.174.18.2.  

I just assumed that everything with the exception of ip address would be the same, did work in Ubuntu 7.10.

---

### Post by sdelinde on 2011-12-12
Dave, How would I obtain this default route? Next to my laptop here, I have my desktop running windows xp
the manual settings are : address 200.10.10.xxx, gateway 255.255.255.0, mask: 255.255.255.0, 
dns 204.174.16.4, with alturnitive 204.174.18.2.  

I just assumed that everything with the exception of ip address would be the same, did work in Ubuntu 7.10.

---

### Post by gandaran on 2011-12-12
the default route is the gateway
>  gateway 255.255.255.0
this is wrong as gateway should be the router IP address (the same IP you use to login to the router configuration page)

---

### Post by sdelinde on 2011-12-12
Thank you very much, You were right, I got it going!!!!!!

---

