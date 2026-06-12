---
title: "Wireless Network With File Server - Security Question"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by Dthorton15 on 2008-09-21
Hello all!
Im pretty new to Linux but in the near future I'm going to be getting a server from a friend of mine with Ubuntu Linux on it.  Once I get it I intend on installing Samba on it so I can use it as a network drive for my 2 other PC's(Windows).

That said:
They are both wireless and are used wireless constantly(move around alot) and I was wondering how secure it would be to have a wireless file server.
Right now via my router I have a few security settings:
-Anti-Spoof(Defends against spoofed IP and MAC addresses)
-Mac Filtering
-WPA Encryption
-Broadcast off

With the Ethernet cord running directly into the server and setting it in my router that only the local ip's of my 2 computers can access the server should that be enough security to protect my files on the server from being viewed by an intruder? 

Thanks in advanced.

edit: Also if someone could explain what the eth0 eth1 etc system is that would be cool. If not I'll figure it out.

---

### Post by virtuallinux on 2008-09-21
That sounds pretty secure to me. You can also set up restrictions on who can access the server through Samba.

As far as explaining the "eth0 eth1 etc. system", that's kinda a broad question.  Basically, each network interface on the system gets labeled ethx, where x is replaced with the number of the network interface, starting at 0.  For example, if you had three network interfaces, you would have eth0, eth1, and eth2.  If that doesn't make sense, isn't clear, or doesn't answer your question, feel free to PM me.

---

### Post by Dthorton15 on 2008-09-21
> **virtuallinux said:**
> That sounds pretty secure to me. You can also set up restrictions on who can access the server through Samba.Cool TY.
> **virtuallinux said:**
> For example, if you had three network interfaces, you would have eth0, eth1, and eth2.Thanks a lot I understand now. 

I made a little diagram of what I want to do--is it possible?
[[IMG]http://img87.imageshack.us/img87/6664/networklayoutcopyqy5.th.jpg[/IMG]](http://img87.imageshack.us/my.php?image=networklayoutcopyqy5.jpg)[[IMG]http://img87.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by mc4100 on 2008-09-21
If you think you're network is going to be actively attacked then you need to make sure you have a solid WPA password. It's the only way to make sure your data is safe, also, by the way, Mac Address filtering, and Hiding the SSID provide **no extra security**.

---

### Post by virtuallinux on 2008-09-21
That diagram looks fine; that's pretty much what my network looks like.

---

### Post by Dthorton15 on 2008-09-21
> **mc4100 said:**
> If you think you're network is going to be actively attacked then you need to make sure you have a solid WPA password. It's the only way to make sure your data is safe, also, by the way, Mac Address filtering, and Hiding the SSID provide **no extra security**.Thanks for telling me that. I knew that SSID's could be easily found even with broad cast off, just not all wireless devices can find it. I also know that Mac Addresses can easily be spoofed.  There is some thing on my router thats called Anti-Spoof protection. I read that it's mainly for spoofed IP filtering, and I don't know how reliable it is.

So that leaves me with the WPA encryption. Should I use WPA or WPA2. From what I have read WPA is more secure but WPA2 is more compatible. Right now I have it set to mixed but all my devices are using the WPA anyway so should I just change it to WPA?

And thanks again Virtual

---

### Post by virtuallinux on 2008-09-21
I think you may have it backwards on WPA/WPA2 WPA2 is newer, and isn't supported on as many devices. From the small amount of research I just did via google, I'm getting the impression the WPA2 is more secure, but WPA is still very secure as long as you use a strong passphrase.

---

### Post by Dthorton15 on 2008-10-05
Okay so I got my server and got everything running the way I want to... for the most part.

I installed Webmin and started to configure Samba.  I configured it to how I thought it should be configured I guess I messed up somewhere.

I keep getting this error when I try to create a new folder on the server in Windows: "You need permission to perform that action" Did I mess something up?

---

