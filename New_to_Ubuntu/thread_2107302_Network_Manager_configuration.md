---
title: "Network Manager configuration"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by kitnkaboodle on 2013-01-21
:confused:
Hi there.
 
New to UBUNTU, and, after using it without any difficulties for quite some time (my son loaded it on my PC, as Windows was causing too much frustration), I find that in trying to set up a new router, something seems to have changed in the Network Manager configuration.
 
I'm a little savvy, but not too techie, so simplistic language would be appreciated in any response or assistance you're able to provide.
 
I had tested the internet connection with my dlink router prior to setting up the new router, and it worked.
However, when I disconnected the dlink and went through the instructions for the new router, the Network Manager goes out and tries to find a connection with the internet.
The result that comes back is: No network connection.
(I'm on my laptop, which I can use to access the internet through hard-wiring my modem to the PC).
Now, even when I try to go back and set up my dlink router, I can't access the internet at all.
Is there somewhere that I can check the settings to re-establish a connection with the internet? I'm using Firefox as my browser.
 
Not sure what other info you require at the moment; I've gone through the resident UBUNTU help files and haven't been able to resource the 'fix'.
 
Thanks!
Kit

---

### Post by grahammechanical on 2013-01-21
Where do you think that the problem lies? With the router not connecting to the ISP? Or with Network Manager not connecting to the router? And how are you trying to connect to the router? With wireless or cable (ethernet)?

My router has 5 LEDs. Power; Ethernet; Wireless; Broadband; Internet.

I have all five lit up because I am connected to the router by both ethernet cable and wireless. You may have either ethernet or wireless depending on which method you are using. You do not tell us.

If Internet is not lit up them the router is not connecting to the ISP.

You do not say which version of Ubuntu you are using. It could be 12.04 or 12.10. It can make a difference. Do you see a network icon in the top panel towards the right of the screen?

Click on it. Do you see a tick mark against Enable Networking and Enable wireless? Do you see a list of wireless access points that are in range of the wireless adapter in the computer. Is your router in the list?

Another method is to go to System Settings and open Networking and click on either Wired or Wireless. Again it depends on your method of connecting to the router.

There is not much more we can do until we have established wether the issue is with the router of the computer.

Regards.

---

### Post by kitnkaboodle on 2013-01-21
Hi again and thanks for the quick response.
Okay, sorry, I'm still using 10.04 Lucid Lynx - haven't bothered to upgrade to v12 of any sort yet, 'cause I noted support until April, so have scheduled it for mid-March.
(hmm.... first mistake??)
 
I believe I'm trying to connect through Ethernet?? (again, newbie to routers, Ubuntu and connections, so I'm a bit at a loss....) I'm hard-wiring (ethernet cable?) from the modem to the router, and the WAN (grey) cable is connected from my PC to the router.
 
My router seems to have all its lights blinking and trying to connect, so I don't think it's that. (The only reason I was upgrading is because I've been having support issues with dLink and couldn't get their support in an upgrade for that router and found a new router for a good price, so figured I'd configure it with my PC desktop.)
And, as the router is trying to connect to the Network Manager and I keep getting the message that I have no network connection, I'm just trying to work backward from there...
 
In my version of Ubuntu, there doesn't seem to be an option for Enable wireless, only Enable networking, which is checked, as well as Enable Notifications; Connection Information is greyed out, so I can't access it, and I'm not sure how to Edit Connections, so it's not much help to me.
When I checked with my ISP, they advised that the router should automatically find it and that I not assign a static IP address.
 
Hope that's answered most of your questions and you're able to assist.
Thanks again!
Kit.

---

### Post by windscape on 2013-01-21
Hi,

Some more information that might help is if any other your other PCs can access the Internet through your new router or not. Also, what is the make and model of the new router?

---

### Post by kitnkaboodle on 2013-01-21
Hi there.
 
No, I can't get my other PCs to access through the router; the only other PC I have is a laptop, and it only has an ethernet connection. I'm unable to connect both the ethernet and the router/WAN connection at the same time.
 
The make and model of the new router is: TrendNet TEW-652BRP.
Although, I can't get my dlink router to work again, which is a WBR-3210.
 
Any assistance would be great, as I really don't want to re-load Windows onto the PC.
 
Thanks,
Kit.

---

### Post by steeldriver on 2013-01-21
Can you establish a LAN connection from any device (Linux or Windows) to the router e.g. by opening a browser and typing the router's default IP into the address bar?

[The default IP for the Trendnet appears to be 192.168.10.1 according to the almighty google]

If you have a cable modem, it is possible that your ISP has tied the internet service to the MAC address of your original router - sometimes it's possible to get the modem to bond to a new device, other times you need to clone the MAC or ask your ISP to update the MAC record.

---

### Post by kitnkaboodle on 2013-01-21
Thanks for the ideas so far.
I'm going to go out and check on them this evening and log back in tomorrow to let you know what happened.
 
Have a great evening/morning (depending on where you are....) and talk to you tomorrow...
 
Best,
Kit.

---

