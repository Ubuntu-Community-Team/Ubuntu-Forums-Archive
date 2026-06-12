---
title: "Wireless Networking"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by edwardLS on 2008-06-05
Can wireless be set to use no encryption?  That is, can it be used on an Open Network?  I have search, but apparently my search capabilities are not up to speed yet.

I am assuming that the answer is YES, since there are so many Open Networks offering free internet access.  If this is the case, what do I set in the configuration for encryption which does not offer "None"  - only WEP and WPA.

---

### Post by st33med on 2008-06-05
Yes, however, it is VERY insecure. Your private stuff could be monitored by hackers or you would have someone hijack you're router, and on, and on...
You never would want to do that unless you are holding a party or making a free hotspot for a restaurant.

Usually, you need to fix some options in the router's menu. When you are connected to the router in question, type in Firefox **192.168.1.1**. That is the usual IP address for the router unless otherwise specified. I would recommend getting help with your router manufacture to check out on which menu the option is in or explore it yourself.

Again, this setup is VERY insecure. Be careful, because this sacrifices security for a little convenience.

---

### Post by st33med on 2008-06-05
> **edwardLS said:**
> If this is the case, what do I set in the configuration for encryption which does not offer "None"  - only WEP and WPA.

That encryption is just that: a password\key to gain access and secure your network by encrypting data to the receiver. That situation is impossible; to have data encrypted without an encryption.

---

### Post by deltaprime on 2008-06-05
agree with st33med it is too insecure, even wep can be cracked within under 20 mins at times (yes i did it on my own network) wpa encryption is better try to get wpa2 working in ubuntu and use that to be secure. go with wpa and choose a encryption over 124 bytes if you can, make your password long with upper lower case letters, numbers and symbols.
good luck.

---

### Post by st33med on 2008-06-05
> **deltaprime said:**
> agree with st33med it is too insecure, even wep can be cracked within under 20 mins at times (yes i did it on my own network) wpa encryption is better try to get wpa2 working in ubuntu and use that to be secure. go with wpa and choose a encryption over 124 bytes if you can, make your password long with upper lower case letters, numbers and symbols.
good luck.

you mean 128 byte encryption ;).

---

### Post by edwardLS on 2008-06-06
Thank you for your response and advice.  

Maybe I am approaching my situation in a way that has no good/secure solution.  I 'only' use Wireless on my Laptop, and I only use the laptop when I travel/camp  Many of the Motel and Campgrounds offer free wireless internet access.  It was my plan to use that free wireless to gain access to my email and respond to email while on the road.  My experience so far has been that the offered free wireless internet access is an open wireless network with no encryption.

I see, and agree, with your advice that is is not secure.  Any suggestion as to how to gain access to my email in a more secure manner would be sincerely appreciated.  I am relatively new at this "on the road" stuff, so I don't have a great deal of knowledge of the best practices to draw on.

---

