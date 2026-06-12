---
title: "Wire Less"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by new@this on 2008-06-03
Ubuntu seems so cool and I can't wait to explore it further.  I downloaded a copy yesterday (6/2/08) and installed it without problem on my Dell Latitude d630 notebook.  The only snafu I've run into is that my notebook will not connect to my wireless network at home.  My network name shows up in the list of available wireless network and I can try to connect but after about 30 seconds the computer stops trying to look and resumes it's not connected status.  I can connect to my home network with other computers and devices perfectly.  Any ideas for resolving this?

---

### Post by hyper_ch on 2008-06-03
deactivate any encryption on the wifi and try to connect unencrypted

---

### Post by valmorel on 2008-06-03
I had a very similar problem with my desktop set-up, and the conclusion I came to was that the wireless card was not directly supported by Ubuntu. Searching the forums confirmed this, and explained how to fix it, but at this point in my Linux development, the instructions were beyond me. Here is how I solved it: I connected the machine to my router with a cable connection from the installed cable network card. Cabled networking is better supported just now. I am sure your laptop will have one of these. I did this with the machine turned off. For some reason, it would not 'hot' connect. After re-booting, I left the machine for about three mins, during which time Ubuntu connected to the net via the cabled card, recognised there was an unsupported wifi network card, and offered to download and install a fix. All I had to do was follow the on-screen prompts. Look for a small green icon to appear on the right hand side of the top bar after you re-boot, and click it to follow the route I took. Hope it works for you as it did for me.

---

### Post by uterrorista on 2008-06-03
> **hyper_ch said:**
> deactivate any encryption on the wifi and try to connect unencrypted
that might be it...

without any encryptation you can test at terminal:
```
sudo iwconfig wlan0 essid <name_of_your_network>
```
make ```
iwconfig --help
``` for further information

and see if you can connect...

---

### Post by new@this on 2008-06-07
I appreciate all these suggestions and I've given each one a shot.  My network has no encryption, and my Dell can connect perfectly when I plug it in to my router, but still no wireless connectivity.

---

### Post by new@this on 2008-06-15
This may seem very strange, but last night I was traveling and the hotel I stayed in had wireless internet access.  I started my Dell with Ubuntu and I was able to connect!  I haven't done anything to the network configuration on my notebook.  So now I suppose the problem is with my Netgear router at home.  I have no security set on the router and the router can see the MAC address of my notebook but still won't connect.  Very wierd.  Any ideas?

---

