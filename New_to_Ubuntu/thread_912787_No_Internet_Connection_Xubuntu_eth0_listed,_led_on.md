---
title: "No Internet Connection Xubuntu eth0 listed, led on router shows - no ip WT??"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by burlingtongs on 2008-09-07
I run a charity computer company. I have a boat load of thinkpads we are trying to install xubuntu on , 650mhz - 128mb - 20gb drive. Everything during the install seems ok EXCEPT these units did not come with internal ethernet and thus during the setup process we are given a warning that eth0 was not found (something to that extent) and so we choose setup network connection later.

XUBUNTU loads up and we start rocking out. The interface etc loads fine, no worries there. We insert our very generic  Xircom REM56G ethernet and modem card into the pc card bus (pcmcia). XUBUNTU detects and installs it fine. The device shows in the network settings. Settings>Network. Roaming mode is selected. Should be good there. I check to confirm network connectivity by seeing the LED on the router indicate activity to the corresponding lan port. Things again look good. However when right click on the network icon and choose connection information it is all 0.0.0.0 It has no ip. I toggle back to automatic dhcp mode but to my surprise no changes. I go off and do an ifconfig and it has a 169.x.x.x ip (private ip address) 

my only thoughts have been bad NIC so I changed it, three times. (we have a crap load of these cards)no change. Now my latest thought was maybe there was something to that setup error message we had received regarding the OS not finding an eth0. No idea. Spent four hours tonight and my wife wants to kill me so im asking for your help. Thanks guys - Rock out

Bobby

---

### Post by rockerphil on 2008-09-07
the only thing that comes to mind for me is to reinstall the OS with the network card installed on the machine, cus every version of Ubuntu will try to auto-configure your the network via DHCP as long as there's a network device present, also, you may try using the alternate install CD, just a thought though. hope it helps,

Phil

---

### Post by tangibleorange on 2008-09-07
> **rockerphil said:**
> the only thing that comes to mind for me is to reinstall the OS with the network card installed on the machine, cus every version of Ubuntu will try to auto-configure your the network via DHCP as long as there's a network device present, also, you may try using the alternate install CD, just a thought though. hope it helps,

Phil

yeah I would also recommend this. however, it may not be practical. you could try:

```
sudo dhclient -r eth0
sudo dhclient eth0
```

and then try opening up the internet...

---

### Post by superprash2003 on 2008-09-07
have you tried static ip..that may help

---

### Post by burlingtongs on 2008-09-08
So I tried the sudo dhclient and that ended with no dhcp offers. I then attempted the static ip and could not reach the gateway ip, (router). Destination Host Unreachable. I have three other cards I am going to try tonight. Crappy thing is that it came on for about 3minutes today after doing the re-install.

Thoughts?

---

### Post by burlingtongs on 2008-09-08
Gets a little more SUCKY :) The Linksys router shows the MAC ADDRESS as active and it has been assign an IP Address from the router view. However from ubuntu stand point NO IP FOR YOU!!

thoughts dear friends?

---

### Post by NetpigsBang on 2008-09-08
**[[color=magenta]Buy Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Test drive our brand new real-time traffic estimator and create your campaign. Choose text, banner, or interstitial ads. Target by site, keyword, demographic. Create or upload multiple ads. **[[color=seagreen]Sell Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Find out how we can help you generate more revenue from your ad space. Customize ads to match your site Approve and reject ads for your site Works alongside other ad programs [**[color=red]Make money online,now![/color]**[color=#0000cc][/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)

---

### Post by tangibleorange on 2008-09-09
> **burlingtongs said:**
> Gets a little more SUCKY :) The Linksys router shows the MAC ADDRESS as active and it has been assign an IP Address from the router view. However from ubuntu stand point NO IP FOR YOU!!

thoughts dear friends?

i'm afraid i don't really know much about troubleshooting wired connections - mine have always worked out the box... try posting the output of:

```
cat /etc/network/interfaces
ifconfig
```

---

