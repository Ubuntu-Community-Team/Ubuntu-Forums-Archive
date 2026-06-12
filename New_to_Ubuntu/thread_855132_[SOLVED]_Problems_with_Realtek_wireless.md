---
title: "[SOLVED] Problems with Realtek wireless"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by Berean on 2008-07-10
Hi,

I've just loaded Hardy onto my wife's laptop.  I've got everything going apart from wireless. I've done something stupid where I wasn't able to get any internet - from deleting apps - but now I have manual configuration (in the task bar) but don't know how to get wireless.  I've followed the 8.04 manual pages but don't have a clue as to how to rectify this!  Is anyone able to help, please?

---

### Post by tjwoosta on 2008-07-10
> I've done something stupid where I wasn't able to get any internet - from deleting apps - but now I have manual configuration (in the task bar) but don't know how to get wireless.

im confused..

did you have wireless working before you mean?

or it never worked since you installed?

what kind of apps did you delete?

what is the make and model of your wireless card?

also please post the output of theese two commands (to help us determine what drivers you would need)

```
lspci
```
```
lsusb
```

---

### Post by Berean on 2008-07-10
tjwoosta,

Thanks for your response.  I agree: It wasn't that clear.  I've solved the problems with the apps.  However, I've spent 3-4 hours trying to configure the Realtek RTL-8139 driver using Ndiswrapper and failed.  Nevertheless, I've now got wireless internet using my external USB dongle (Netgear WG111v2) straight out of the box.  Any ideas about the Realtek disaster?

---

### Post by oldsoundguy on 2008-07-10
in a word ... Realtek!  (it is a disaster for Linux)
Realtek has a failure to communicate with the Linux development crew.
You see it over and over and over again in the posts here.
It can be made to work.  But patience and time are involved.  MANY threads on your issue on the forums. Do a forum search. 
(that will also help you to learn more about this forum .. one of the BEST on the web, and certainly the best Linux forum HANDS DOWN!  No one gets treated like an idiot on this forum!) (unlike some others I have used in the past!)

---

### Post by Berean on 2008-07-10
> **oldsoundguy said:**
> in a word ... Realtek!  (it is a disaster for Linux)
Realtek has a failure to communicate with the Linux development crew
I'll stick with my dongle then!  Can't be bothered with all that faffing.

> Do a forum search. 
(that will also help you to learn more about this forum .. one of the BEST on the web, and certainly the best Linux forum HANDS DOWN!  No one gets treated like an idiot on this forum!)
I thought I had done a forum search, but now we've got the new forum I'm not so sure that it's as good as the old "automatic" one (but I may be wrong).  I couldn't find anything on the Realtek 8139, but (I concede) many on Realtek.  Thanks for your post: This forum is the best on the web - I agree - so thanks for contributing to my problem (that should read; solution).  Not to be a complete newb, how do I search (just to clarify that I'm doing it correctly).  Regards,

---

### Post by Rudedawg on 2008-07-10
I too had difficulty with the realtek wireless. I was able to get it to work using ndiswrapper, but I still cannot connect to encrypted networks. It actually works great with unencrypted networks. If your wifi is encrypted, try turning it off for a moment to test it or test it on someones unencrypted wifi. If for some reason you are unsure how to encrypt and unencrypt your wifi, try to find someone who has an unencrypted wifi setup so you can test. Wifi encryption can be a pain when you don't know what you are doing.

---

### Post by oldsoundguy on 2008-07-10
I do my searches in steps.  first the name (a lot of hardware problems are not posted in the hardware area, where they should be posted!) .. then a process of elimination.  and IF I need to follow the thread once posted (such as you are attempting to do), I then do the search each day using my NIC, as everything I have posted to, will then come up and all the new replies will be shown in bold.  (except Pink Ponies .. a fun thread!)

I have a secure WEP network, but am using Atheros based D-Link cards (full D-Link system including access point and router.) these are desktops, not laptops.  NEVER had an issue as they installed out of the box.

---

### Post by Berean on 2008-07-10
> **Rudedawg said:**
> I too had difficulty with the realtek wireless. I was able to get it to work using ndiswrapper, but I still cannot connect to encrypted networks. It actually works great with unencrypted networks. If your wifi is encrypted, try turning it off for a moment to test it or test it on someones unencrypted wifi. If for some reason you are unsure how to encrypt and unencrypt your wifi, try to find someone who has an unencrypted wifi setup so you can test. Wifi encryption can be a pain when you don't know what you are doing.
Rudedawg,

I've tried everything!  I couldn't get it working either with, or without encryption.  I'll stick with my Netgear USB, I think.  I have absolutely no problems with that manufacturer!  Thanks for your advice.

---

### Post by Berean on 2008-07-10
> **oldsoundguy said:**
> I do my searches in steps.  first the name (a lot of hardware problems are not posted in the hardware area, where they should be posted!) .. then a process of elimination.  and IF I need to follow the thread once posted (such as you are attempting to do), I then do the search each day using my NIC, as everything I have posted to, will then come up and all the new replies will be shown in bold.  (except Pink Ponies .. a fun thread!)

I have a secure WEP network, but am using Atheros based D-Link cards (full D-Link system including access point and router.) these are desktops, not laptops.  NEVER had an issue as they installed out of the box.
Thanks for the advice oldsoundguy, much appreciated.  I use WEP encryption and I think that might be part of the problem, but I really don't want to consider using unencrypted.  I'll stick with Netgear, and limited posts!  Once again, thank you to you all, and - although not solved - thread solved!

---

