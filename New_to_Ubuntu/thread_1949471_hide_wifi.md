---
title: "hide wifi"
date: 2012-03-30
forum: New to Ubuntu
---

### Post by bariamtak on 2012-03-30
I set up my system with ubuntu 11.10 32 bit and am using it for the last 5 months. I have a LAN and now i m sharing the internet connection with two of my friends. I use the WEP -40/128bit key security in ad hoc mode. It works fine.

But the thing is that i don't want to let others see my wifi. I dont see any option to hide my wifi in network settings. Can i hide my network without disconnecting my friends ?
Do i have to buy separate router or access point to hide the wireless networks. I am not concern with the security for now. i only want to hide the visibility of the wifi.
Thanks in advance.

---

### Post by ashhab2010 on 2012-03-30
Hiding your wifi is not a solution for security... Finding a hidden wifi is a trivial task. there are many free sofware available that can detect your network
I recommend you to use WEP2 Personal instead of WEP-40/128bit and use a long non-dictionary pass to make your network more secure.

---

### Post by bariamtak on 2012-03-30
Thank you for the suggestion.As i have mentioned before I only want to hide it.

---

### Post by ccrs8 on 2012-03-30
ashhab2010 is absolutely correct (except I'd recommend WPA2).  That being said, to answer your question, somewhere in your router settings should be an option to broadcast your SSID.  Disable that option, and your network name (SSID) will not broadcast out and be visible.  People who have connected to that network in the past should still be able to connect without having to manually enter the network info, so your friends will be fine.  If you need to get someone else connected to it, they just have to manually enter your network name in their wifi setup.

---

### Post by uRock on 2012-03-30
There is nothing wrong with using WEP. Depending on what you have connecting to the router, WEP may be the only choice. There should be a setting listed when you log into your router to stop broadcasting the SSID. That is the function you need to find to hide your network.

---

### Post by Bill Z on 2012-03-30
Try doing both.  Go to your router and make it hidden.  Use WPA2.  Rename your network something like Test_No-Internet. If they find it, they may not be interested.  Maybe call it Linux_Virus_Test. Unless you use only wire (all in the same room), a network can never be too secure.

---

### Post by kurt18947 on 2012-03-30
I had my SSID hidden.  After reading several articles I changed pass phrases and turned it on.


Here's one source:

[http://www.howtogeek.com/howto/28653/debunking-myths-is-hiding-your-wireless-ssid-really-more-secure/](http://www.howtogeek.com/howto/28653/debunking-myths-is-hiding-your-wireless-ssid-really-more-secure/)

Another:

[http://sites.google.com/site/easylinuxtipsproject/securitywireless#TOC-Myth-1:-not-broadcasting-the-SSID-h](http://sites.google.com/site/easylinuxtipsproject/securitywireless#TOC-Myth-1:-not-broadcasting-the-SSID-h)

I used GRC's password generator but less than 63 characters.
[https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm)

I imagine if someone were determined enough it'd be impossible to make consumer-grade hardware/software invulnerable.  The trick is to not be the "low hanging fruit".  It seems like WEP is on the "low hanging fruit" list.  Kind of like the joke where if you and your friend are being chased by a bear, you don't have to outrun the bear.  You just have to outrun your friend.

---

### Post by bariamtak on 2012-03-30
Thank you all but I think I forgot to tel you that right now I am not using any other hardware( router or access point ). I am sharing from my laptop directly. And in the network setting in wireless, I don't see the option to hide SSID. Am i missing something ? The SSID is same with my network name and if I Delete it, I cannot save the settings .How do I do ?
Or is there no options for me ?

---

