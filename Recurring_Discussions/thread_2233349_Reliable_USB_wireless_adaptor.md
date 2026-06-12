---
title: "Reliable USB wireless adaptor"
date: 2014-07-08
forum: Recurring Discussions
---

### Post by samuel16 on 2014-07-08
Hi, 
      I am newbie to Ubuntu & Linux. I want to setup my Windows 7 PC for Ubuntu.  This machine will run both Windows 7 and  Ubuntu 14.04 (booted from a USB drive), when i finally set it up. During my preparation, i noticed that there are lot of questions on the net about  USB wireless adapters not working with Ubuntu.  I want to buy a wireless USB adapter  that will   


[LIST=1]
[*]be  compatible  and has been tested on Ubuntu 14.04.
[*]not only compatible,  but  more importantly,  will  work reliably  without  dropping connection  everyday.
[*]will  run  in N300 or N150 (second choice) protocol.
[*]currently my other machines are on  WPA2-PSK (AES encryption).  So i would like the same in this new USB stick.
[*]also work  reliably  when the machine boots  in  Windows 7  mode.
[/LIST]

I tend to run this machine continuously;  so i need a wireless USB stick  that will run  for atleast a few days ,  without disconnections.  If  you have come across a USB for 14.04, that meets the above 5 criteria,  please let me know.  I have to buy this USB  (hopefully from local  Frys store)  as soon as possible.  I am using a NetGear  (N 300 speed)  router,  and so it would be nice if  i can find a Netgear  USB  wireless adapter.  From past experience i know that it would be a safer bet, when  the  router and  desktop receiver are paired from the same company.  So, i am leaning towards  NetGear,  but  am  not  tied to the brand,  if  i can find a reliable  USB dongle  that works on both Windows and  Ubuntu 14.04.  

Looking forward to preparing my  Ubuntu  bootable  USB  drive tomorrow. 
Thanks for any leads.

---

### Post by samuel16 on 2014-07-09
No replies so far.  ](*,)     Meanwhile, my reading indicates that compatability  depends mostly on the chipset used by the wireless adapter.  

[LIST=1]
[*]Also, i found that there exists  a list of  chipsets  on which  Ubuntu  has tested on, and hence the official  chipsets.   Does anyone know where i can find such a list of 14.04 ?
[*]I found thinkpenguin.com which claims that their products have been tested on Ubuntu ([COLOR=#000000][FONT=verdana]11.04, 11.10, 12.04, 12.10, 13.04, 13.10, 14.04).   Does anyone have good or bad experiences with their products ?  Specifically, i am looking at their  USB wireless  model [/FONT][/COLOR][COLOR=#4477AA][FONT=verdana](TPE-N150USB) [/FONT][/COLOR][COLOR=#000000][FONT=verdana]and wonder if anyone has tried this. [/FONT][/COLOR]
[/LIST]
[COLOR=#000000][FONT=verdana]&#8203;
Thanks for any input.

[/FONT][/COLOR]

---

### Post by Bucky Ball on 2014-07-09
*Thread moved to **Recurring Discussions**.*

Welcome. There are a ton of threads and info here and elsewhere regarding this. ;)

You could start here:

[https://duckduckgo.com/?q=best+wireless+adapter+ubuntu](https://duckduckgo.com/?q=best+wireless+adapter+ubuntu)

Broadcom, Ralink, Realtek, Atheros. If it is very new chipset it may not work (like brought out last week), but quite probably will eventually.

---

### Post by Mike_Walsh on 2014-09-01
Hi, Samuel.

I use Ethernet on my Compaq desktop. However, I also have an ancient Dell laptop, on which I run Lubuntu, because of its low hardware requirements. This Dell refuses to run a wireless adapter, but is quite happy with Ethernet.

On the occasions I'm running both machines at the same time, I use a TP-Link TL-WN725N (v.2) wireless adapter on the desktop. When I first switched to Ubuntu, back in May, the original Ubuntu kernel that was pre-installed in the .iso image ( the 3.13-0.32 kernel) wouldn't run the adapter. However, over the next two kernel upgrades, sometime between the 3.13-0.33 and the 3.13-0.34 kernels, it now runs very well indeed.

Obviously support has been brought in for the Realtek RTL8188EUS chipset that it uses. It worked fine under XP, and, according to the box, ought to work fine for Windows 7.

If you visit the website:-

[http://uk.tp-link.com/products/details/?categoryid=243&model=TL-WN725N](http://uk.tp-link.com/products/details/?categoryid=243&model=TL-WN725N)

it will tell you all you need to know.

You may also find this of interest:-

[https://wikidevi.com/wiki/TP-LINK_TL-WN725N_v1](https://wikidevi.com/wiki/TP-LINK_TL-WN725N_v1)

One caveat; this IS only an N150 adapter. However, unless you're playing very graphics-intensive online games, there's no reason why it shouldn't do what you require of it. It also works superbly at streaming video and online radio stations.

Hope that helps.

Regards,

Mike.

---

### Post by kurt18947 on 2014-09-02
In the early days of WiFi it's true that having the router/wireless access point and adapters from the same company was helpful.  I'm not sure that's true today. You are correct that in linux world chip sets matter, rather than manufacturer. Netgear has an Atheros based adapter - WNA 1100 - that has a pretty good rep.  I have a couple RealTek RTL8192SU based adapters - TEW-649UB - that seem faster and has been very reliable.  The caveat with the RTL8192SU based adapters is that they may have a problem with suspend/resume.  There's an easy fix if you choose to go that route.

---

### Post by Mike_Walsh on 2014-09-02
> **kurt18947 said:**
> In the early days of WiFi it's true that having the router/wireless access point and adapters from the same company was helpful.  I'm not sure that's true today. You are correct that in linux world chip sets matter, rather than manufacturer. Netgear has an Atheros based adapter - WNA 1100 - that has a pretty good rep.  I have a couple RealTek RTL8192SU based adapters - TEW-649UB - that seem faster and has been very reliable.  The caveat with the RTL8192SU based adapters is that they may have a problem with suspend/resume.  There's an easy fix if you choose to go that route.

I don't wish to hijack the OP's question, but it's interesting that you mention the suspend/resume problem. My TP-Link, using that RTL 8188 chipset, does exactly the same. If I remove the wireless adapter, so the system is Ethernet only, it'll happily wake up from suspend, every time. 

If the adapter is plugged in, and I suspend the system, it'll wake up if I do so within about a minute; otherwise, I get the black screen and a warning about the 'rtl 8188 chipset failed to initialize'.....followed by a string of numbers, and a Launchpad bug report reference.

Regards,

Mike.

---

### Post by Bucky Ball on 2014-09-02
Well old thread, and it is in recurring discussions for a reason. Difficulties with specific wireless adapters should perhaps be addressed in new threads, but thanks for sharing.
[I]
Thread closed.[/I]

---

