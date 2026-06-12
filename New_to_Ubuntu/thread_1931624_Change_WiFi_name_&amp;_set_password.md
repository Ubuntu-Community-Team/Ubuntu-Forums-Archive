---
title: "Change WiFi name &amp; set password"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by doppel.ganger on 2012-02-25
How do you change the name of a WiFi network? Also, how do you set a password? I will also accept Windows 7 instructions. Thanks!

---

### Post by fcomstoc on 2012-02-25
As far as I know you change those settings on the router by typing in 192.168.1.1 or 192.168.0.1 or whatever the router ip address is into your web browser. That pulls up the router config. If you have never set up the password to change the settings it should be the manfcr default (something like admin) you can find that on the internet. Then the network name is the SSID setting, and the password is usually in the wireless settings.

It doesn't matter what OS you are using as long as there is a working web browser. 

Another note you have to be connected through wireless or Ethernet to change these settings. There is no way to do this if you are not on the network.

---

### Post by doppel.ganger on 2012-02-25
How do I find the router ip?

---

### Post by doppel.ganger on 2012-02-25
Okay, got in and set a new SSID and WPA/WPA2 PSK code. Now when I connect to the network on my Nook, type in the code, It connects but says Connected, But No Internet. :( Works fine on netbook.

---

### Post by audiomick on 2012-02-25
Two things: if you can get into the router, then you can look at its' status and see if it has an internet connection. Can't tell you specifics; it's different for each device, but it will be there. If the router has an internet connection, then your machine is not talking to it properly.

Secondly, just a bit of advice: don't mess around with this sort of stuff on a wireless connection. It is too easy to lock yourself out of the router. Get a cable and plug yourself in.

---

### Post by doppel.ganger on 2012-02-25
No, it works like a charm on my computers. I just can't get my Nook Tablet to connect to it now. Like I said, it connects but says it can't get on the 'net.

---

### Post by audiomick on 2012-02-25
The only time I see that kind of a message is when I have one of my machines on a fixed IP that the router doesn't like. Is your tablet thingy set to get an address via DCHP?

---

### Post by doppel.ganger on 2012-02-25
Hmm... Tablet doesn't offer options like that. :/ Should I change it to static ip in the wifi router setup?

---

### Post by doppel.ganger on 2012-02-25
Sorry, gotta catch some Zs. I'll get back in the morning.
BTW, eastern time here. :)

---

### Post by audiomick on 2012-02-25
> **doppel.ganger said:**
> 
BTW, eastern time here. :)

Central European time here. It's nearly 4 in the morning. :-\"


If there is nothing to change in the Tablet, then I think you can assume that it is on DCHP.

---

### Post by d4m1r on 2012-02-25
> **doppel.ganger said:**
> Hmm... Tablet doesn't offer options like that. :/ Should I change it to static ip in the wifi router setup?

No, not if everything but the Nook is working. Try clearing/deleting your old network from the Nooks settings and try connecting to your (new SSID) network and specify the username and password.

---

### Post by fcomstoc on 2012-02-26
> **doppel.ganger said:**
> No, it works like a charm on my computers. I just can't get my Nook Tablet to connect to it now. Like I said, it connects but says it can't get on the 'net.

Does the nook support the kind of security that you have turned on (WPA, WPA2, WEP)? I know that some devices only support WEP.

---

### Post by doppel.ganger on 2012-02-26
The two other networks in our house use the same WPA/WPA2 PSK connections. I'll try to connect manually.

---

### Post by doppel.ganger on 2012-02-26
Still didn't work. It connects, but says no internet. I'll take off the security and try it.

---

### Post by doppel.ganger on 2012-02-26
Ah. The WPA algorithms were set on AES. When I changed it to TKIP, it worked. SOLVED!

---

