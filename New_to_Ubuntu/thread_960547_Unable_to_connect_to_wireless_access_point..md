---
title: "Unable to connect to wireless access point."
date: 2008-10-27
forum: New to Ubuntu
---

### Post by afbuntu on 2008-10-27
Hi... i'm new to linux especially ubuntu. i'm using a wireless access point to connect to the internet. the thing is now that i'm using ubuntu i can detect the access point but unable to connect. my wireless is open (no security). still i can't access it. i have load of work to do. please help me.

---

### Post by decoherence on 2008-10-27
First of all, can you connect, using the same settings, with another computer? Or with the same computer under Windows? That will rule out the access point as the problem.

With that ruled out, we need more information about your wireless hardware. Under the Applications menu, under Accessories, run the Terminal program. In the window that comes up, type

```
sudo lshw -C network
```

It will ask you for a password... type it and press enter, keeping in mind it won't show anything (no little dots to represent what you type) Select the outputted text, right click and select copy (or press Ctrl Shift C... note Ctrl C WON'T do it... this is particular to terminals) then paste the stuff here.

While you're at it, please post the output of the command

```
uname -a
```

cheers,
sean

---

### Post by unknownmosquito on 2008-10-27
If you can't get it to connect with NetworkManager, try installing wicd:
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)
I was having problems on campus (same situation, no authentication sort of deal) and wicd cleared up my issues.

---

### Post by phidia on 2008-10-27
What wireless card do you have? It could be that it is not fully enabled. Did you enable the card from System > Admin > Hardware drivers?

To find your card type open a terminal and enter > lshw -C network

---

### Post by bodhi.zazen on 2008-10-27
What wireless card ?

---

### Post by afbuntu on 2008-10-30
D-Link AirPlus G+ [DWL-G520+]

---

