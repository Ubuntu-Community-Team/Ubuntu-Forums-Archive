---
title: "How to surf wirelesssly with my ubuntu?"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by ronferds on 2008-09-04
ola,

I am a proud user of my ubuntu 8.04, i love the feel and usability of it. I have an unlimited broadband connection, which i am presently using, with windows xp professional, I also have a Dlink wireless router connected to my Modem and hence, the connection to the internet, is established between my acer aspire 5920 and the internet.I have a user name as well as a password, so as to protect my connection from usage, by others.

When i boot in from ubuntu, I cannot connect to the internet wirelessly. The following image is seen, and it asks for the following, Note that i have a user name and password, but when i input the former  it does not work. What do I do?

When i go to the network manager, the wireless roaming is enabled and all, but when i unlock it, My details within the wirelss roaming tab is blank.  

Could you'll kindly suggest a possible remedy for this? 

:(

---

### Post by swoll1980 on 2008-09-04
Did you check your card for compatibility? Also some brands of cards I've used through ndiswrapper would not support 128 bit wep I had to use 64 bit

---

### Post by ronferds on 2008-09-04
> **swoll1980 said:**
> Did you check your card for compatibility? Also some brands of cards I've used through ndiswrapper would not support 128 bit wep I had to use 64 bit

Hi there and thanks a million for replying. So what would you advise me to do?

---

### Post by crispy_420 on 2008-09-04
Still using WEP?

What wireless chipset are you using?

Is WPA an option for you?

Just asking because WEP provides the security strength of wet toilet paper. It may hold, but for how long? You only stop the lazy wireless theives.

---

### Post by swoll1980 on 2008-09-05
> **ronferds said:**
> Hi there and thanks a million for replying. So what would you advise me to do?

Did you check it for compatibility? Are you using ndiswrapper? What kind of card do you have?

---

### Post by lintoon on 2008-09-05
You do not need a username to access the wireless network. You just need the wep or wpa key which has been set on your router (If one has been set).  I'm guessing you are confusing your login username and password details when prompted for a password.  If not I apologise for the assumption.

---

### Post by lintoon on 2008-09-05
Also, the details are blank because your wireless will be set to DHCP.  This means you will be given all the details necessary in order to use the network from the DHCP server (Your router).  Without this, eg if it is set to manual, you would have to know all of the addresses.  Eg IP address, subnet mask, default gateway and dns.  If this means nothing to you don't worry because DHCP sorts it out for you anyway.

---

### Post by Slug71 on 2008-09-05
I dont think WEP or WPA was very well supported with Hardy(could be wrong though as i didnt use it very long). I used an unsecure connection with mac filtering and disabled broadcasting of the SSID.

Are you sure your wireless card is recognised? I had to enable a Restricted Driver from Admin-Hardware Drivers on my Acer.

---

### Post by Crafty Kisses on 2008-09-05
I'd like to see the results of this command: ```
lshw -C network
```

---

### Post by lazyart on 2008-09-05
There is no username for the wireless network.  The connection it found is encrypted.  You need to:
1. Find out what type of encryption is in use.  64 or 128 WEP?  Maybe it's WPA?  I use WEP at home so I know it's supported.
2. Find out the encryption key.  It might be a word, a phrase or a string of letters and numbers.
Armed with that information you should be able to enter it and connect.

---

### Post by ronferds on 2008-09-05
Hi Lazyart,

How do i find out whether it is 64 or 128 WEP?

Also, How do i find out the encryption key?

Is it the same user name as well as password?

---

### Post by ronferds on 2008-09-05
so what do i do then? i will send u the screenshots of my connection :(

---

### Post by ronferds on 2008-09-05
> **swoll1980 said:**
> Did you check your card for compatibility? Also some brands of cards I've used through ndiswrapper would not support 128 bit wep I had to use 64 bit


Hi There I have added screenshots of my connection to highlight the issue.... 


Hope this helps in aiding your analysis.

Regards,

Rohan

---

### Post by ronferds on 2008-09-05
> **crispy_420 said:**
> Still using WEP?

What wireless chipset are you using?

Is WPA an option for you?

Just asking because WEP provides the security strength of wet toilet paper. It may hold, but for how long? You only stop the lazy wireless theives.


Hi,

I am attching some screenshots to thos thread...hope it helps.

Thanks a million,

Rohan

---

### Post by ronferds on 2008-09-05
> **lintoon said:**
> You do not need a username to access the wireless network. You just need the wep or wpa key which has been set on your router (If one has been set).  I'm guessing you are confusing your login username and password details when prompted for a password.  If not I apologise for the assumption.


Hi Lintoon, 
 

I will attch some screenshots to highlight my plight. I hope the screenshots helps in aiding your analysis...

Ciao,

:):KS

---

### Post by Slug71 on 2008-09-05
In the last screen shot of your last post.
Wireless Security - WEP 64/128-bit ASCII
Key               - (you need to enter the key you set on your router here)

If you log into your router you should be able to find it under wireless security, should say something like WPA or WEP Shared Key, if you dont remember it.

You wont be able to connect without it unless you disable your wireless security

---

### Post by Slug71 on 2008-09-05
ronferds, log into your router and check what security you have enabled. With WEP and WPA you do not need a User Name, just a key(password). If you check my earlier post youll see where to find it once you log into your router.

---

### Post by knix on 2008-09-05
> **Slug71 said:**
> ronferds, log into your router and check what security you have enabled. With WEP and WPA you do not need a User Name, just a key(password). If you check my earlier post youll see where to find it once you log into your router.

If you have physical access to your router, I would use an ethernet cable when changing settings.

---

### Post by ronferds on 2008-09-06
> **Slug71 said:**
> ronferds, log into your router and check what security you have enabled. With WEP and WPA you do not need a User Name, just a key(password). If you check my earlier post youll see where to find it once you log into your router.
Thanks buddy...how dumb of me...gotit connected...sniff :') am connected again....

---

### Post by ronferds on 2008-09-06
Thanks swoll1980,

i have managed to resolve the issue

---

### Post by crispy_420 on 2008-09-06
The router is the issue at hand. Your wireless chipset looks to be an Intel based solution, and a newer model at that.

What is the Make/model of your router? Lets start there and move outward from there?

Question to the rest of the folks: been a little while since install, does Intel chipset require non-free option?

---

### Post by ronferds on 2008-09-06
Thanks all of you guys... have managed to connect to my laptop...i owe all of you...big time :)


:guitar:

---

### Post by knix on 2008-09-06
> have managed to connect to my laptop
congratulations

---

### Post by Slug71 on 2008-09-06
> **ronferds said:**
> Thanks all of you guys... have managed to connect to my laptop...i owe all of you...big time :)


:guitar:

Nice one ronferds!! 
Enjoy!
:guitar:

---

