---
title: "Having problems with my new laptop and current network"
date: 2013-07-17
forum: New to Ubuntu
---

### Post by Thefuzzyone69 on 2013-07-17
I just got a new laptop yesterday and was excited to finally give Ubuntu a try. The computer came with Windows 8 installed and thought I'd give it a fair chance...but that lasted less then 30 minutes before throwing in a live cd and wiping that mess from my computer. I'll admit I was stupidly overzealous in doing so and failed to create a recovery disc before hand but I really, really didn't want to be stuck with 8. But to get to the point, my laptop seems to suck all the bandwidth of my network. Speedtests without the laptop connected has my desktop running mid 30's Mbps while if I connect the laptop the desktop is lucky to get 1Mbps if it's even able to complete the test at all. The laptop of course hits mid 30's every time no problem. After scratching my head and consulting my linux enthusiast friend he commented on problems with Broadcom drivers and lo-and behold guess what network card is in this laptop. He's since abandoned me for Burger King so I thought I'd seek assistance here. 

lspci -vnn | grep 14e4: yields BCM4314 [14e4:4727] 

I'd found where there is someone working on a driver for this card but it is listed as wip at the moment. So is there any hope for me getting to use Ubuntu?

---

