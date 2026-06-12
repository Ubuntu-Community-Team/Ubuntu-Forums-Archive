---
title: "not able to get connected to the Internet on my ubuntu11.10"
date: 2011-11-07
forum: New to Ubuntu
---

### Post by adengappa on 2011-11-07
My pc runs on windows7.On top of it I have intalled ubuntu11.10. But I could not get the wifi connection in my ubuntu. I couldn't see my network connection name in that list. Even if connect the network cable it is not showing. But in windows7 I could get wifi.
Do I need to do anything else for getting my network connection?Any help please..


Thanks

---

### Post by MG&amp;TL on 2011-11-07
What sort of internet do you have? Is it a card, an adapter, etc.?

First step: Go to the wifi icon in the top right and ensure your network is not there. If network(s) are listed, but yours is not there, ignore the below.

Second step: You may need a driver for your internet. This is manifested with no interfaces available in the wifi icon. This can be problematic. Go to "additional drivers" and see if there is one available for your card/adapter.

If yours is not on the network, but others are, I have absolutely no clue. Sorry.

---

### Post by amjjawad on 2011-11-07
> **adengappa said:**
> My pc runs on windows7.On top of it I have intalled ubuntu11.10. But I could not get the wifi connection in my ubuntu. I couldn't see my network connection name in that list. Even if connect the network cable it is not showing. But in windows7 I could get wifi.
Do I need to do anything else for getting my network connection?Any help please..


Thanks

Hello and Welcome to Ubuntu Forum :)

Is that Normal Installation or Wubi Installation?

---

### Post by adengappa on 2011-11-07
I have a fast internet using modem. Could you please tell me what additonal drivers should I need to download?

If I click the wifi icon, it is not listing anyone's network.> **MG&TL said:**
> What sort of internet do you have? Is it a card, an adapter, etc.?

First step: Go to the wifi icon in the top right and ensure your network is not there. If network(s) are listed, but yours is not there, ignore the below.

Second step: You may need a driver for your internet. This is manifested with no interfaces available in the wifi icon. This can be problematic. Go to "additional drivers" and see if there is one available for your card/adapter.

If yours is not on the network, but others are, I have absolutely no clue. Sorry.

---

### Post by adengappa on 2011-11-07
I just checked for additional drivers. my broadcamSTA wireless was not activated. When I clicked the Activate, it tried to download drivers, but finally left a error message

"sorry could not install drivers, check 
/var/log/jocky.log.

How do I go ahead further? Any help?

---

### Post by Paqman on 2011-11-07
You need to be connected to download the drivers. Plug straight into your router with a cable and try again.

---

### Post by gandaran on 2011-11-07
> **adengappa said:**
> I just checked for additional drivers. my broadcamSTA wireless was not activated. When I clicked the Activate, it tried to download drivers, but finally left a error message

"sorry could not install drivers, check 
/var/log/jocky.log.

How do I go ahead further? Any help?
first find out the broadcom wireless chipset model with this commad in terminal
```
lspci
```
then with that information either paste the output here or use the forum search box for broadcom threads, there are plenty of them with instructions on how to install the driver
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by wildmanne39 on 2011-11-07
Hi, just post the result of this command please it will give more specific information on your wireless card, and there is a little more work to be done installing sta driver in 11.10 then in previous version.
```
lspci -nnk | grep -iA2 net
```
Thank you

---

### Post by adengappa on 2011-11-07
Thank you. I typed lci. It printed a lot of message.since I don't have net connection.couldn't paste here.but in the last line it printed some info about the network controller.
Broad com corporation bcm4312 802.lib 
Any help.

E=gandaran;11435429]first find out the broadcom wireless chipset model with this commad in terminal
```
lspci
```
then with that information either paste the output here or use the forum search box for broadcom threads, there are plenty of them with instructions on how to install the driver
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)[/QUOTE]

---

### Post by wildmanne39 on 2011-11-07
Hi, just run it this way:
```
lspci -nn | grep 0280
```
does it say 4312 [14e4 4315]or what is the number and does it say lphy?
Thank you

---

