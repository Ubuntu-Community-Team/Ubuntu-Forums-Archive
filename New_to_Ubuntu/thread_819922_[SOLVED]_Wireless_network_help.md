---
title: "[SOLVED] Wireless network help"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by Dutch70 on 2008-06-05
I just got ubuntu installed from the live cd to my 
(vista partitioned) hdd. 

I cant seem to connect to the internet, going through the troubleshooter to step 3.2.5 "check IP assignment" it gives this info...

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No Such Device
"My Network"-ERROR while getting interface flags - No Such Device
"MY Network"-ERROR while getting interface flags - No Such Device
wmaster0: unknown hardware address type 801
Bind Socket to interface: no such device.

I had an online connection and surfed the web from the live cd, before I transferred it to the hdd. then I done something wrong trying to get it connected after I put it on the hdd.
 
The nework manager icon only gives me the option to "manually configure" now. previously it showed my connection. 

 As many of you know, I just got a wonderful new toy and cant play with it...:lolflag: I would really appreciate any help offered. TIA

btw: my PC experience = about 4 mnths, short of web browsing.
Ubuntu experience...bout an hour! and growing! hehe

---

### Post by FuturePilot on 2008-06-05
What kind of wireless card is it? Please post the output of
```
lspci
```
You can find the terminal under Applications&#8594;Accessories&#8594;Terminal

---

### Post by Dutch70 on 2008-06-05
Thanks for responding so fast, I am doing this the long way...rebooting and paper & pencil...

lspci shows that it is realtek...

RTL8101E PCI Express Fast Ethernet Controller (rev 01)

Is that the info you needed? 
 
Linksys wireless adapter, it all worked when I used it with the live cd. so surely I did this trying to get it set up.
 
With the fresh install, first time I accessed it,and clicked on the network manager icon it showed my network and signal strenth even my neighbors actually. I had to install a couple of packages via the troubleshooter guide, then enable it or something. After I did all that, iwconfig showed "my network" 
 
Somehow, when I go to  the network manager icons now, it just gives 2 options "wired connect" which is grayed out, and "manual configuration" which is showing my wireless network with a tic in the box....:lolflag:

---

### Post by vfrankli on 2008-06-05
I had a similar experience when I made some changes.  I lost my access to the internet and the twin monitors showed up on the task bar, instead of the connection meter.  I found that going back into the router setup and making sure the network data, password, type of security, etc. were exactly the same on the Ubuntu laptop.  Once that happened, it worked.

---

### Post by Dutch70 on 2008-06-05
Yes, that did it...I got back on ubuntu and messed with the network settings, and I am now talking to you for the first time while using ubuntu, :guitar:

Thanks you very much!!!

---

